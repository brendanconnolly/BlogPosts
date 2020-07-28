## Level 2: Multi Layer framework

 Beyond UI, api or other components included for arranging or manipulating, only consumer is tests.

### Why Go Further
as level 0 and level 1 come together you can find your self in a place where you have more tests than you have time to run. 

You can start to be a victim of your own success. You have these tests, they are being run on and reported upon and each successive sprint the automated test suite grows. 

Sometimes what started out as a requirement, and badge of honor to do everything as a user would starts to run into some real world constraints. 

 now if things are goi attention is being paid to when tests are running and the results. 
#### Time 

#### Reliability

### Seeking Efficiencies

### Architecturally focused
The hardest thing about UI tests is the UI. 

We start looking at how we can leverage layers of our applications architecture to carve out the excess UI from tests. The first ripe target is typically using your api. 

Beyond the api, or if your app doesn't expose one you you're probably going to target the database, reading and writing to it to stage interactions in the UI. We are looking for seams in the application that we can leverage for testing. 

As we turn our attention to our applications architecture, we also have to start investigating thte architecture of our automation framework. 

Its easy and tempting to start making api calls and writing sql statements the same way we started automating at level 0. But the problem is more complicated this time because its not just 1 layer of the application we are dealing with. 

So while the UI portion of our automation is maturing in some ways we are starting over in other areas. Foundational decisions about your automation strategy need to be addressed in order to successfully handle this transition.  The obvious point here that your overall frameworks complexity goes up, the more subtle point is that the nuance of your actual tests and the motivations behind them goes up as well. 

### Understanding your reasoning

We are indexing more and more at this level around efficiencies and to make room for it we are drifting further and further from the idea of having the motivation of these tests follow the mantra of doing things as a user does them.  What we implicitly admitting is that for a set of reasons we are willing to accept an approximation of user activity for elements of tests. 

This means we have to decide what we are actually testing in each test, and should be actively considering what in the UI or what in the end to end, full stack of this series of actions that we are actually testing. 

If we accept approximations, we are accepting some level of risk. Depending on your app it may be big or it might be small, but you need to stsart questioning and understanding what is different when  things are done via the UI and when things are done at other layers. 

The maturity of your understanding of the internals of the application you are testing needs to grow so you can reasonable

