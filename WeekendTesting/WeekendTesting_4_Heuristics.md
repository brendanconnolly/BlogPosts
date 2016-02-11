![Weekend Testing: Heuristic Method](http://www.brendanconnolly.net/wp-content/uploads/2016/02/heuristicMethod.jpg)

Testers use heuristics all the time to evaluate software whether intentionally or intuitively. For this [Weekend Testing Session](http://weekendtesting.com/?p=4246) we dug into testing heuristics. 

This is my 4th session Weekend Testing, and each one has been well worth the time spent, but I'll be honest I had my mind blown twice in this session.

[Albert Gareev](http://automation-beyond.com/) was facilitating this session, and out of the gate after introductions... Boom, the first bomb dropped
 
### Can you Automate Heuristic Methods?

I didn't expect this line of thinking at all. I expected a rousing discussion about different heuristics and how and when to use them. Instead, I get a more esoteric question that literally gave me pause. 

Is it like [Schrödinger's cat](https://en.wikipedia.org/wiki/Schr%C3%B6dinger's_cat), where [the act of observation actually changes reality.](http://www.sciencedaily.com/releases/1998/02/980227055013.htm)
Does the act of quantifying heuristic application into something that could be automated change it? I think it kind of does. 

Automating something by nature dehumanizes it. It strips away the intangible and replaces it with exact and defined measurements. Once automated no more learning occurs while the heuristic is applied. Lessons can only be learned again by rehumanizing the process and introducing a human to review the automated results. 

As you might expect, a group of testers for a variety of reasons generally concur.  

### AI, Machine Learning & Data

The conversation drifted towards the need of a technological leap to actually automate the heuristic method. 

![Data](http://www.brendanconnolly.net/wp-content/uploads/2016/02/StarTrekData.jpg) 

It wouldn't be much of a discussion about artificial intelligence without Data from Star Trek wandering into the conversation and [Jean Ann Harrison](https://twitter.com/JA_Harrison) made the leap for us.

>I can't help but think of Data from Star Trek, the Next Generation trying to understand human interaction.

It's true, Data constantly struggled to understand human behavior.   

However, most automation doesn't try to so closely mimic human response, the return on investment just isn't there. Automation just apes behavior to approximate the intended scenarios being tested. That said, *Machine Learning* through services like [IBM Watson Cloud Services](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/services-catalog.html) or [Azure Machine Learning](https://www.ibm.com/smarterplanet/us/en/ibmwatson/developercloud/) seeks to bridge that gap but instead of artificial intelligence it uses large volumes of data and pattern recognition. Given enough input, trends appear that allow computers to actually recognize the items in images or other data sources. So you can start to see how this could approximate some portion of human insight.  

The reliability and value proposition of automation generally breaks down the closer you get to trying to approximate the reality of human interactions with software. The thought involved in reproducing heuristic method application would require a system that can pass the [Turing Test](https://en.wikipedia.org/wiki/Turing_test). Even then if Data couldn't understand human behavior I'm not confident technology will ever get there.
 
### Automated Heuristics In Action 

Next we looked to a real world app that offered to [help you write in a more polite, friendly tone](https://labs.foxtype.com/politeness), to look at the heuristics it applied and see if through testing we could identify some of them. 

It was pretty fun to have a group of testers all banging on an app at the same time, all the while furiously sharing insights and issues. You learn a lot sharing your process and witnessing others at the same time. Skype get's a little crazy but it's part of Weekend Testings charm. 

### Can A Human learn from Automated Heuristic Application?

So after we had a grip on how the app behaved, we sought to look for its contextual value. No doubt, in some cases the app could suggest more polite alternatives for the input provided.

The more defined the domain is the closer an automated heuristic can approximate it's application. For example consider Microsoft Word's grammar check as opposed to a politeness check. Grammar has a fixed set of rules, they might be nuanced and complex but there are still rules.  However, being polite is often more than applying fixed rules to replace words. It's more subtle than that, it also varies across different segments of society and the world. 

So we concluded a non native English speaker may see some improvement on the politeness of their writing using this app. They could just as easily end up losing meaning in translation by shooting for the highest scores. The automated heuristics don't provide context or insight to the user. You aren't learning if you don't understand the actions that are being taken.

Just when I was starting to feel like I had gotten all I could out of the session the second bomb dropped...   

### Can Test Cases teach you to test?

Wow, so we just concluded that you need context and understanding for real learning to occur. How often have you seen new testers just handed a set of test cases to execute with the hopes they will be immediately functional or at least pick it up as they go.

 If you are using test cases, do yours convey the context and intent of each test? Each step within the test case? Even if they try, what is being lost in translation from tacit to literal?
 
 The group had mixed feelings, but there was definite consensus that learning to test is best done through human interactions and mentoring.

I understand the lure of test cases, I even see how the could have some potential value as reference material. I just don't believe they actually *teach*. In fact I think executing another persons test script increases the likelihood that you will turn off or ignore your testing spidey-sense. You are a soldier in the military following orders, if it's not documented it's not important.  

### A Call to Action 

It took me a long time knowing about [Weekend Testing](http://weekendtesting.com/) before I actually got involved. I regret that, I learn every time I go. I take away insight, I meet fellow testers from all over the world and I get energized about testing. Feel free to check out my other [experience reports](http://www.brendanconnolly.net/category/weekend-testing/) if you need more convincing. 

So pick a session and just show up, practice your craft and you might just enjoy yourself...


