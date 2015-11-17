If you have been testing API endpoints, you may have used tools like [cURL](http://curl.haxx.se/), [Postman](https://www.getpostman.com/), or [DHC](https://dhc.restlet.com/) as a client for testing them. Those tools definitely have their place, but ever since I started automating tests it generally feels faster to just script them up. Even if I'm not going to be checking these tests in, I like doing this for a few reasons. 

* If I do find an issue while testing, then I have a test I can rerun to verify the fix or hand off to a developer as reproduction steps.
* I can quickly modify or expand the test. I might start with the simplest case and as I progress I just modify the test to include more details.
* Computer aided verifications. Assertions in the test script help guarantee I don't misread the output.

I'm not a JavaScript or Node expert but these days they are hard to ignore, so I have been dabbling with them to learn more about them. The first time I made an ajax call to a remote API (Open Library) in JavaScript my mind was blown. The response from host was in [JSON](https://en.wikipedia.org/wiki/JSON) so which meant immediately the variable that I stored response in had all of the properties and values available to me. I could type "response.title" or "response.author" and the value was there, no need to have a class to deserialize the response into. Suddenly I understood exactly why some of the newer teams I had been working with were so frustrated with our xml only API. 

While its easier for developers it's also more easily testable. Enter [Frisby.js](http://www.frisbyjs.com), a light weight framework for testing REST API's using [Node](https://nodejs.org/en/) and JavaScript. 

### Setup
The [Frisby](http://www.frisbyjs.com) site has setup instructions but it is quick and easy If you don't already have them installed, install node and npm.
Once those are installed install two npm packages:
* npm install --save-dev frisby 
* npm install -g jasmine-node
Fire up your favorite editor and create a new .js file, just be sure the file name ends in "_spec" so jasmine will find it.
Now you are ready to rock and roll testing some API's. 

### Verbs
Frisby is very intuitive and readable when it comes to using different http verbs. Command line tools like cUrl are powerful but sometimes its a little hard to remember what all the command line parameters mean. All the CRUD operations are available as easy to read method names like, .post, .get, .delete, .put. I think this makes the tests readable and very easy to write. 

```js
frisby.create('Frisby Post')
  .addHeader('User-Agent','frisbyJS Test')
  .post('https://www.httpbin.org/post',  {hello: 'world'})
  .expectStatus(200)
  .expectBodyContains('world')
  .toss();
```

### Status Codes and Headers
If you need to set specific headers Status codes are easily verified with the expectStatus method.  
```js
frisby.create('Bad Auth expect 401')
  .addHeader('User-Agent','frisbyJS Test')
  .get('https://bad:user@api.github.com/users/vlucas')
  .expectStatus(401)
  .expectJSON({ message: 'Bad credentials', documentation_url: 'https://developer.github.com/v3' })
  .toss();
```

### Multi Step Tests
If you tests require multiple http calls Frisby allows you to chain the calls through the .after and .afterJSON methods. These will guarantee that the first request completes before the next call is made. AfterJSON accepts a function that will have the response JSON from the first response passed to it. This makes it really easy to do an authentication request first to capture a token, then use it in later requests. It's also handy for dynamic resources, so you could make a post call and then using the identifier in the response make a get call to verify the resource was created as you expected.  
```js
frisby.create('Nested Test Repos ContainsJson Frisby')
.addHeader('User-Agent','frisbyJS Test')
  .get('https://api.github.com/users/vlucas')
   .afterJSON(function(jsonResponse) {
     frisby.create("using response from first request")
          .addHeader('User-Agent','frisbyJS Test')
          .get(jsonResponse.repos_url)
          .expectJSON('?',{name: 'frisby'}) //? in path param searches with an array
          .toss();
   })
.toss();
```
### Debugging and Running
By default you won't see any of the responses in the test output. All you have to do is include an inspector call inside the test. Using the example from above in the first request I added inspectBody which will log the unformatted response body to the console. In the second I used inspectJSON which will format the response body and write it to the console. So if you do have multiple steps to the test but only one call is really being tested you can limit the output to just what you want to view. 
```js
frisby.create('Nested Test Repos ContainsJson Frisby')
.addHeader('User-Agent','frisbyJS Test')
  .get('https://api.github.com/users/vlucas')
  .inspectBody() //logs raw response body to the console
   .afterJSON(function(jsonResponse) {
     frisby.create("using response from first request")
          .addHeader('User-Agent','frisbyJS Test')
          .inspectJSON() // this will log the response body (pretty printed) to the console
          .get(jsonResponse.repos_url)
          .expectJSON('?',{name: 'frisby'}) 
          .toss();
   })
.toss();
```
To run your tests, go to the command line and navigate to the folder that contains the file you created and type "jasmine-node .", this will run all tests in all files that end in _spec. If you need more info on executing the tests check out the [Jasmine-Node documentation](https://www.npmjs.com/package/jasmine-node). 

### Wrapping Up
I really like Frisby.js, it was light enough to help me quickly write tests without getting in the way. I can see if you have more than a few steps in a single test that it could get a little unwieldy which might be a problem for some use cases. It is designed to work with JSON, which means if you want to test the XML side of your API you things get more complicated, so this might not be the best tool for quick testing with XML. The example tests are available on GitHUb, if you want to check them out [Frisby Examples](https://github.com/brendanconnolly/FrisbyExamples).