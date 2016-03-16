
A lot of people think testers can only test things with a GUI. If we can't click it or touch it then we are out of our depth. A key area of software applications today is not GUI based, it is the engines that power the applications, it is the [API's](www.webopedia.com/TERM/A/API.html). Some companies only product are services that expose only a API to consumers. 

This Weekend Testing Session targeted [REST](http://www.restapitutorial.com/lessons/whatisrest.html) based APIs and showcased a Chrome plugin [Arc](http://restforchrome.blogspot.com/) that can be used to explore and test them. 

### Getting Started

After the customary greetings and introductions we got a brief introduction and overview what API's are and their purpose. We also got into some of the particulars about what a tester can expect to see when interacting with a REST API. This was valuable because it got everyone on the same and because some testers in the session were fairly new to API testing. 

First, kudos are deserved for the [Michael](http://www.mkltesthead.com), the facilitator of the session and for those testers who were new to this topic and looking to learn. This is what is so great about Weekend Testing sessions, you get exposure to areas of testing that you may not have access to in your current job. Couple that with a very open and supportive environment and its a great opportunity to learn. 

### Digging In

After covering the basics, we turned to using Arc to explore some interfaces. We didn't have a specific API that we were all using so you could imagine this lead to a variety of interface related questions. There is a reasonably high barrier to entry to API testing because you have to get familiar with the related standards and vocabulary before you can really feel comfortable using tools to interact with them. So while everyone was using the same tool, when looking for public API's they all may use HTTP for transport, they aren't all going to be RESTful and each one will have its own topology and conventions. 

That may sound a little painful, but in reality its a very important lesson for testers to learn. API's are not all created equal, and when you start talking about what makes an interface RESTful there's a good chance you'll find some [conflicting definitions and confusion](https://www.mobomo.com/2010/04/rest-isnt-what-you-think-it-is/). 

### Exploring with Pairing

These sessions always get a little hectic, we had about 15 testers all hammering away at once and the messages on Skype can come at you fast and furious. It's just part of the charm of Weekend Testing, everyone's sharing ideas and issues, asking questions or attempting to answer them. This session took a different approach and we were encouraged to pair up into smaller groups. 

This worked really well, some of the more experience API testers could share an API with their group so people weren't trying to find a public API they could use and make sense of while trying to get a handle on testing it. I can't speak for all the groups, but I found mine really helpful (Thanks Amy!) since I got a little distracted looking for an API and its documentation. From what I saw people were allowed some good opportunities to ask questions and learn while getting some hands on experience with a tool they could use in the future. 

I'll be honest though, breaking into groups really changed the dynamics of the session. It may have just been me but I was curious about what the other groups were doing. What might I be missing out on? To combat this, the transcripts from the smaller groups were shared. I guess I just really love the frenzy of the full group, it's kind of energizing :)

### Discovery

A major topic of conversation was how do you know how to navigate an API. RESTful interfaces have the concept of [HATEOS](https://lostechies.com/jimmybogard/2014/09/23/the-value-proposition-of-hypermedia/) (Hypermedia as the Engine of Application State), which basically involves the response to a request including links in it that the client application can use to navigate through the domain. While its regarded as part of the [standard for a restful interface](http://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven), it isn't as prevalent as you might think. Other API types don't have that requirement, so how do you even get started?

Usually you end up needing some documentation to use any API. The documentation and its content and quality varies. From technological solutions like [Swagger](http://swagger.io/getting-started-with-swagger-i-what-is-swagger/) which developers can integrate into their projects to generate automated API documentation to a pdf of the api reference doc. Sometimes you end up having to reverse engineer the process and monitor the web traffic and parse out the api calls made by a web page or app. Not pretty but it still happens. 

For testers though it may come down to a conversation with a developer. Not all API's are meant for public consumption. Their intended use may only be by their companies client applications. We may have only briefly covered this in the session, there was enough there for people to start their own study with some direction. 

### Wrapping It Up

If you are on the fence about checking these sessions out, I really can't recommend them enough and this session was no different. If you think that a session doesn't sound interesting, the folks over at [Weekend Testing Americas](http://weekendtesting.com/?page_id=1630) are opening the process up for suggestions of topics and you could even co-facilitate a sessions if you want to share your expertise in an area. 

You can also check out the [session details](http://weekendtesting.com/?p=4275) including another experience report and [full chat transcript](http://weekendtesting.com/wp-content/uploads/2016/03/WTA-70APIsandARCRESTClient.pdf)

If you need more convincing. feel free to check out my other [experience reports](http://www.brendanconnolly.net/category/weekend-testing/). 

So pick a session and just show up, practice your craft and you might just enjoy yourself... 