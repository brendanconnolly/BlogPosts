![Testing Webhooks with JS](http://www.brendanconnolly.net/wp-content/uploads/2021/07/testing-webhooks-js.png)


Webhooks are a popular way for platforms to notify external clients and integrations when changes are occurring in near real time. Webhooks can be very useful but they can  also present a challenge for both automated and exploratory testing of the webhooks implementation. 

Rather than rely on sites like [webhook.site](https://webhook.site/) and [requestbin](https://requestbin.com/), in this series we will step through automating webhooks testing using NodeJs by creating a webhooks listener that enables us to wait for, recieve and inspect webhooks while testing.

In [part 1](http://www.brendanconnolly.net/testing-webhooks-with-js/) of this series we created a class to act as a wrapper around an [express](https://expressjs.com/) server that listens for webhooks. 

Now we have the infrastructure in place to listen for webhooks, we will take a look at registering, receiving and triggering webhook events using the [Github API](https://docs.github.com/en/rest).

## Configuring Github Webhooks

Github provides webhooks at the repository and organization level. These webhooks are what allow external systems to be updated or trigger workflows when events happen inside a Github repository. So when a build is started because a pull request is merged theres a good chance webhooks are involved. 

To use Github's webhooks a client registers and subcribes to receive notifications for either some or all events. To help troubleshoot and/or monitor the health of the integration, an interface is provided to list the webhook deliveries including the request/response data from each triggered event sent to the registered endpoint.

### Using the Github API
Typically I would turn to [axios](https://github.com/axios/axios) when I need to create an api client. In this case however, Github provides [Octokit.js](https://github.com/octokit/octokit.js), which they describe as `the all-batteries-included GitHub SDK for Browsers, Node.js, and Deno`. To install Octokit from a console inside your project directory enter `npm install @octokit/rest`. 

Octokit provides multiple authentication options, for this guide we will be using the default which is a `personal access token`.  If you neeed an assist on creating a token, the github docs have you covered: [Creating a Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token). 

### Storing the Acccess Token
The access token is a secret that we don't want to share publically, rather put the token directly into our code we'll use the [dotenv](https://github.com/motdotla/dotenv) package to store it as an environment variable. To install, on the console enter `npm install dotenv`.  

In the root of your project directory create a `.env` file, and inside it add `GITHUB_TOKEN=your_token_here`, replacing the placeholder text with the token you generated. 

### Setting up Octokit
To setup the api client, we'll create a new file named `githubClient.js` and enter the following:

```js
const { Octokit } = require("@octokit/rest");
require("dotenv").config();
```

This will import Octokit and load the contents of our `.env` file. Technically the call to `.config()` on the `dotenv` module only needs to happen once. As we progress we can refactor that into a more centralized place, but for now we'll leave it here. 

Create a class named `GithubClient` and add a constructor function. Inside the constructor, we'll create an `instance` property and assign it a new instance of Octokit. The Octokit constructor accepts an options object, to use the personal auth token from from the env variable pass in  `{ auth: process.env.GITHUB_TOKEN }`. 

`.env`
```js
GITHUB_TOKEN=your_token_here
```

`githubClient.js`
```js
require("dotenv").config();
const { Octokit } = require("@octokit/rest");

class GithubClient {
  constructor() {
    this.instance = new Octokit({ auth: process.env.GITHUB_TOKEN });
  }
}

module.exports = new GithubClient();
```

### Configuring Repository Webhooks
Now we are ready to register our listener to receive webhooks from Github. To do this we will be using the `create` and `delete` endpoints from the [Repository Webhooks API](https://docs.github.com/en/rest/reference/repos#webhooks). Octokit provides the `createWebhook` and `deleteWebhook` methods to interact with these endpoints. 

To make this example a bit more real world, rather than use those methods directly inside our tests, we are going to wrap the implementation details of the `Repository` api calls inside a service class. 

The repository endpoints require the repository owner and repository name to be included as parameters. To allow different repository to be used for testing, we are going to store the repository `owner` and `name` as environment variables. Inside the `.env` file add the following, replacing the placeholder values with your test repository values:

`.env`
```js
TEST_REPOSITORY_NAME=repo_name_here
TEST_REPOSITORY_OWNER=repo_owner_here
```
To create the service class, create a new file named `reposService.js` and enter the following:

`reposService.js`
```js
const githubClient = require("./githubClient");
const repositoryName = process.env.TEST_REPOSITORY_NAME;
const repositoryOwner = process.env.TEST_REPOSITORY_OWNER;

class ReposService {

}

module.exports = ReposService;
```

Inside the `ReposService` add an `async` method called `createWebhook`. For this api we need to provide the `url` where we will be listening for webhook events, and an array of the [events 
that will trigger webhooks](https://docs.github.com/en/developers/webhooks-and-events/webhooks/webhook-events-and-payloads). The format of the webhook payload can come in 2 flavors, `json` or `form`. The rest api defaults to `form`, we are going to override this and use `json` instead. 

```js
  async createWebhook(hookUrl, events, contentType = "json") {
    return await githubClient.instance.repos.createWebhook({
      owner: repositoryOwner,
      repo: repositoryName,
      config: {
        url: hookUrl,
        content_type: contentType,
      },
      events: events,
    });
  }
```

To allow our tests to clean up after themselves add another `async` method called `deleteWebhook`. This method accepts the id of the webhook to be deleted. 

```js
  async deleteWebhook(hookId) {
    return await githubClient.instance.repos.deleteWebhook({
      owner: repositoryOwner,
      repo: repositoryName,
      hook_id: hookId,
    });
  }
```

By using a service class we are able to decouple the contract between our tests and the Github Octokit api. This serves to simplify consuming this api in our test code, while also centralizing changes in the event of breaking changes to the Octokit.

## Triggering Events

To trigger webhooks we are going to use the star / unstar repository event. To do this we will be using Github's [Activity API](https://docs.github.com/en/rest/reference/activity) and the `Star a repository for the authenticated user` and `Unstar a repository for the authenticated user` endpoints. Octokit provides the `starRepoForAuthenticatedUser` and `unstarRepoForAuthenticatedUser` methods to interact with these endpoints.

We are going to create another service class to handle the `activity` endpoints. 
```js
const githubClient = require("./githubClient");
const repositoryName = process.env.TEST_REPOSITORY_NAME;
const repositoryOwner = process.env.TEST_REPOSITORY_OWNER;

class ActivityService {

}

module.exports = ActivityService;
```

Inside the `ActivityService` add 2 `async` methods called `starRepository` and `unstarRepository`. Similar to the `reposService` methods, the activity endpoints require the repository owner and repository name to be included as parameters. No other data is needed since these endpoints use identity information from our access token to attribute the star/unstar activity to a user.

```js 
  async starRepository() {
    return await githubClient.instance.activity.starRepoForAuthenticatedUser({
      owner: repositoryOwner,
      repo: repositoryName,
    });
  }

  async unstarRepository() {
    return await githubClient.instance.activity.unstarRepoForAuthenticatedUser({
      owner: repositoryOwner,
      repo: repositoryName,
    });
  }
```

## In Action
We can see what we have so far in action by using the script below on the nodejs console.

```js
require("dotenv").config();
const ReposService = require("./reposService");
const ActivityService = require("./activityService");
const WebhookListener = require("./webhookListener");

const repoSvc = new ReposService();
const activitySvc = new ActivityService();
const captainHook = new WebhookListener();

(async () => {
  const hookConfig = await captainHook.setup();
  console.log(`Listening on ${hookConfig.url}`);

  const addHook = await repoSvc.createWebhook(hookConfig.url, ["star"]);

  await activitySvc.starRepository();
  await activitySvc.unstarRepository();

  captainHook.hooksReceived.forEach((hook) =>
    console.log(JSON.stringify(hook))
  );

  // commented out to allow you to see the webhook registered in github in the repository settings, uncomment to delete the webhook
  //const deleteResponse = await repoSvc.deleteWebhook(addHook.data.id);
  await captainHook.stop();
  console.log(`fin`);
})();
```
In part 3 of this series we'll use mocha and chai to create tests for receiving hooks using what we have built so far. 

The complete code for this series is available on github https://github.com/brendanconnolly/github-test-automation.




