If you have been testing API endpoints, you may have used tools like [cURL](), [Postman](), or [DHC](https://dhc.restlet.com/) as a client for testing them. Those tools definately have their place, but ever since I started automating tests it generally feels faster to just script them up. Even if I'm not going to be checking these tests in, I like doing this for a few reasons. 

* If I do find an issue while testing, then I have a test I can rerun to verify the fix or hand off to a developer as reproduction steps.
* I can quickly modify or expand the test. I might start with the simplest case and as I progress I just modify the test to include more details.
* Computer aided verifications. Assertions in the test script help guarantee I don't misread the output.

I'm not a JavaScript or Node expert but these days they are hard to ignore, so I have been dabbling with them to learn more about them. The first time I made an ajax call to a remote API (Open Library) in javascript my mind was blown. The response from host was in [JSON]() so which meant immediately the variable that I stored response in had all of the properties and values available to me. I could type "response.title" or "response.author" and the value was there, no need to have a class to deserialize the response into. Suddenly I understood exactly why some of the newer teams I had been working with were so frustrated with our xml only API. 

While its easier for developers it's also more easily testable. Enter [Frisby.js](http://www.frisbyjs.com), a light weight framework for testing REST api's using [Node](...) and JavaScript. 

### Setup
The [Frisby](http://www.frisbyjs.com) site has setup instructions but it is quick and easy If you don't already have them installed, install node and npm.
Once those are installed install two npm packages:
* npm install --save-dev frisby 
* npm install -g jasmine-node
Fire up your favorite editor and create a new .js file, just be sure the file name ends in "_spec" so jasmine will find it.
Now you are ready to rock and roll testing some apis. 

### Status Codes
```js
frisby.create('Bad Auth expect 401')
  .addHeader('User-Agent','frisbyJS Test')
  .get('https://bad:user@api.github.com/users/vlucas')
  .inspectJSON()
  .expectStatus(401)
  .expectJSON({ message: 'Bad credentials', documentation_url: 'https://developer.github.com/v3' })
  .toss();
```

### Verbs
Get/Put/Post/Delete

### Multi Step Tests
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
