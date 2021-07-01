# Testing Webhooks with JS

![Testing Webhooks with JS](http://www.brendanconnolly.net/wp-content/uploads/2021/07/testing-webhooks-js.png)

Webhooks are a popular way for platforms to notify external clients and integrations when changes are occurring in near real time. Webhooks can be very useful but they can  also present a challenge for both automated and exploratory testing of the webhooks implementation. 

Typically the integrator registers to recieve webhooks by providing an endpoint that will accept post messages that serve as notifications about events. This usually requires a server available and listening on the public internet. There are sites like [webhook.site](https://webhook.site/) and [requestbin](https://requestbin.com/) that can be used for testing but they aren't a great option for automation, and may not fit your needs depending on the type of testing you need to perform. 

Rather than rely on sites like those, in this series we will use the Github api and webhooks along with NodeJs to create a webhooks listener that allows us to easily automate webhook testing.

## Setup
This post assumes you have [nodejs](https://nodejs.org/en/) installed and a empty node package created. We'll be using [Express](https://expressjs.com/) to create a webserver to listen for hooks. If you are new to nodejs and express the Express documention is helpful and has a [getting started](https://expressjs.com/en/starter/installing.html) guide. 

To install express from a console inside your project directory enter `npm install express`. 

To configure the server, we'll create a new file named `webhookServer.js` and enter the following:

```js
const express = require("express");
const hooksServer = express();
hooksServer.use(express.json());
```
This will import the `express` module, create a express app and adds the json parsing middleware. Next we add variables to store the response code sent when hooks are recieved, the path for the webhooks route, and a placeholder array to store the hook data thats received. the last variable we need is for the port the server will ne listening on. We will default to `3005` but allow that value to be overriden if an arguement is passed to our server on startsup. 

```js 
let responseCode = 200;
let hooksPath = "/hooks";
let hooksRecieved = [];

let hooksServerPort = 3005;
if (process.argv.length > 2) {
  //args passed to process start in 3rd position
  hooksServerPort = process.argv[2];
}
```

Now we are going to add a `post` route to accept the incoming webhooks, and a `get` route to let us see the hooks we've recieved. For the sake of simplicity, both these route will use the same path `/hooks`. 

The `post`route accepts incoming webhook requests and responds with our default status code. The webhook request is destructured so we can capture the headers and body of the request object while adding a timestamp when the hook was recieved. This data is then pushed onto our `hooksRecieved` array. 

The `get` route responds with the serialized  contents of the `hooksRecieved` array. It may not be the prettiest but this will come in handy for quickly checking that hooks are being received.
```js
hooksServer.post(hooksPath, async (req, resp) => {
  const hookData = { recievedAt: Date(), headers: req.headers, body: req.body };
  resp.sendStatus(responseCode);
  hooksRecieved.push(hookData);
});

hooksServer.get(hooksPath, (req, resp) => {
  resp.send(JSON.stringify(hooksRecieved));
});

```
Last we start the server
```js
hooksServer.listen(hooksServerPort, () => {
  console.log(`Listening for hooks at ${hooksPath} on ${hooksServerPort}`);
});

```

## Listening for Hooks

Now that we have a server that listens for webhooks and stores the data recieved, we are going to wrap that server process in a class to make it easy to interact with for testing. 

We'll start by creating a new class called `WebhookListener`, inside this class we are going to start by creating 2 `async` methods: `setup` and `stop`. 

Inside the `setup` method we're going to spin up our webhook server inside a [child process](https://nodejs.org/api/child_process.html) using [fork](https://nodejs.org/api/child_process.html#child_process_child_process_fork_modulepath_args_options). Fork has a built in communication channel that will allow us to communicate with the server process using event based messaging. This messaging provides bi-directional communication, allowing our listener class to access the hooks that have been recieved as well change state or behavior of the server like clearing the hooks recieved or changing http status code returned.

### Starting the Server Process
To use `fork` we're going to import the `child_process` module, and since the first argument to fork is the `modulePath` we'll also import the `path` module to use the `join` method. 

The `setup` method is going to accept an optional  `port` parameter to allow callers to specify a different port to suit their environment.

To start the child process we need to pass 2 arguments, the path to our `webhookServer` file, and an array of args to pass to the server process. For current needs the args array will include our desired port.

Fork returns an instance of `ChildProcess`, we are going to store that in a variable for use later.

```js
const { fork } = require("child_process");
const { join } = require("path");

module.exports = class WebhooksListener {
  async setup(port=3005){
        this.hooksServerProcess = fork(join(__dirname, "webhookServer.js"), [
      port,
    ]);
  }

  async stop(){}
}
```

### Receiving Hooks

Next, we need to make our server publically available on the public internet to receive hooks from Github. To do this we will be using [ngrok](https://ngrok.com/).

> ngrok allows you to expose a web server running on your local machine to the internet. Just tell ngrok what port your web server is listening on. 

Rather than use ngrok directly, we'll be using the [ngrok npm package](https://www.npmjs.com/package/ngrok). The package offers a nice api which makes working with ngrok simple.

To start ngrok and expose our webhook server to the the public internet we use the `connect` method and pass it the port that our server is listening on. The `connect` method will provide us with the dynamic url that was generated by ngrok. 

Now we have our server started and available to receive hooks, we return the full url to use when registering to receive hooks from Github.

```js
const { fork } = require("child_process");
const { join } = require("path");
const ngrok = require("ngrok");

module.exports = class WebhooksListener {

  async setup(port = 3005) {
    this.hooksServerProcess = fork(join(__dirname, "webhookServer.js"), [
      port,
    ]);
    
    const url = await ngrok.connect(port);

    return { url: `${url}/hooks`, };
  }

  async stop() {}

  }
};

```

### Storing Hooks

To notify the `WebhookListener` when hooks are received we will need to update our webhook server code to send a message to the parent process.  
The process for doing this is described in the nodejs [child process docs](https://nodejs.org/api/child_process.html#child_process_subprocess_send_message_sendhandle_options_callback):
>Child Node.js processes will have a process.send() method of their own that allows the child to send messages back to the parent. 

To implement this we need to update the post route hander inside `webhookServer.js` to include `process.send(hookData);`. 

Next we need to update our listener class to listen for messages from the server and store the webhook data. Before we do that though, we need a place to hold the received hooks inside the listener that we can then update as messages arrive. Inside our `setup` method add an array for the received hooks `this.hooksReceived=[]; `

Now that we have a place to store our hooks, we need to add an event handler to listen for the `message` event from the server process. The event handler will accept the message and add it to the `hooksRecieved` array.


`webhookServer.js`
``` js
hooksServer.post(hooksPath, async (req, resp) => {
  const hookData = { recievedAt: Date(), headers: req.headers, body: req.body };
  resp.sendStatus(responseCode);
  hooksRecieved.push(hookData);
  process.send(hookData); // <-- notify the parent process when post received
});
```

`webhookListener.js` 
```js
const { fork } = require("child_process");
const { join } = require("path");
const ngrok = require("ngrok");

module.exports = class WebhooksListener {

  async setup(port = 3005) {
    this.hooksReceived=[]; // <-- hook data storage
    this.hooksServerProcess = fork(join(__dirname, "webhookServer.js"), [
      port,
    ]);

    const url = await ngrok.connect(port);
    // each post will trigger a message event
    this.hooksServerProcess.on("message", (message) => {  
      // take the data recieved and push onto the array 
      this.hooksReceived.push(message); 
    });

    return { url: `${url}/hooks` };
  }

  async stop() {}
  }
};

```

### Clearing Hooks
It would be helpful to clear the received hooks so that we can have a clean slate between tests. Currently the server and the listener class are separately storing the received hooks, to keep the data in the server in sync with the listener we can use the same messaging channnel to send an event to the child process. 

First we will add a new method named `clearReceivedHooks` to the `WebhooksListener` class. This method will, clear the instances `hooksRecieved` array and use the `send` method on the `hooksServerProcess` to send an object to the server process to notify it that hook data should be cleared. 

Inside the `webhookServer` we are going to add an event handler to `process` to listen for the message event. Then in the event handler we will inspect the message contents for the `clearHooks` property and reset the `hooksReceived` array.

`webhookServer.js`
``` js
process.on("message", function (message) {
  if (message.clearHooks) {
    hooksRecieved = [];
  }
});

```

`webhookListener.js` 
```js
  clearReceivedHooks() {
    this.hooksServerProcess.send({ clearHooks: true });
    this.hooksReceived = [];
  }

```

### Stopping the Listener Cleanly
To avoid leaving the server and ngrok processes running and leaving our port in use we are going to add a `stop` method to the `WebhookListener` class.
```js
  async stop() {
    this.hookListenerProcess.kill("SIGKILL");
    await ngrok.kill();
  }
```

Just in case the `stop` method isn't called we will also update the `setup` method inside the `WebhookListener` class to handle for the exit event and attempt a more graceful shutdown.

```js
  async setup(port = 3005) {
    this.hookListenerProcess = fork(join(__dirname, "webhookServer.js"), [
      port,
    ]);

    const url = await ngrok.connect(port);

    this.hookListenerProcess.on("message", (message) => {
      this.hooksReceived.push(message);
    });
    
    //if the process exits call stop to kill the server and ngrok
    process.on("exit", async function () {
      await this.stop();
    });

    return { url: `${url}/hooks`, processHandle: this.hookListenerProcess };
  }

```

## Using the Listener
We can see what we have so far in action using the nodejs console.

```
const WebhookListener = require('./src/webhooks/webhookListener.js');
const captainHook = new WebhookListener();

// an async iife to start the server
( async()=>{ 
  const config= await captainHook.setup()
  console.log(config.url)
 })();
 
 // when finished 
 captainHook.stop();

```
You can then use the url printed to the console to post webhooks to it. Since the console session is still active you can interact with the listener class to clear hooks etc.

In part 2 of this series we'll start using the `WebhookListener` inside end to end tests using the Github api to register our listener and trigger hooks. The complete code for this series is available on github https://github.com/brendanconnolly/github-test-automation.




