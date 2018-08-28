
Part 2 - Testing in Production & Testing In DevOps Environments

![book cover](http://www.brendanconnolly.net/wp-content/uploads/2018/08/devops.png)

When deciding to read [A Practical Guide To Testing in Devops](https://leanpub.com/testingindevops) by [Katrina Clokie](http://katrinatester.blogspot.com/) for [#30DaysOfTesting](https://twitter.com/hashtag/30daysoftesting). I wanted to focus on avoiding the temptation to get destination oriented and just finish the book. In the vein of [Testopsies](http://www.brendanconnolly.net/testopsies/) (a concept I learned about at from [Michael Bolton](http://http//www.developsense.com/) at CAST2016), I wanted to give time for both inspection and introspection.

To that end, the plan I arrived at was:
1. Read the book start to finish
2. Divide the book into 3 parts
3. Read each part twice (repeating before moving on)

In [part 1](http://www.brendanconnolly.net/reading-testing-in-devops-pt1/) I focused on the the first 2 sections of the book, *Testing In A DevOps Culture* and *Testing In Development*. This post will explore the next 2 sections.

## Testing in Production

> Testing in production is a way to tilt the balance towards speed.

The feedback cycle between the customer and development team is tightened. At first it might seem a unsettling to testers...

The risk here is your customer often becomes aware of your development methodology as they witness the product evolving in near real time. If its uncomfortable trying to test in this type of environment, take a moment and empathize with the your users. Software they may rely on for accomplishing day to day tasks at their job is changing in multiple ways hourly or even faster. //driving car with minor differences throughout the day or mid commute

> Decisions can be driven by data from actual users interaction with production software.

> Information provided by production monitoring and alerting, analytics events, and logging must be sufficient for the team to have visibility of both user and system behavior.

--more--

Monitoring as a part of a feedback loop, like tdd but at a team / feature level 

*Monitoring* is surveilling your application, system usage, health etc. *Alerting* is the ability to act on information provided by monitoring systems

Monitoring is a (somewhat suprisingly) big part of the context of testing in devOps.  
Benchmarking...

information is only as good as the actions taken that are informed by it. While many teams leverage other products or services as part of their monitoring and alerting strategy, in this section we are reminded that the integration and triggering of these systems warrant a testers attention. You don't need to test that something like [PagerDuty](https://www.pagerduty.com/) can send an alert, but you may want to verify that the events that should trigger an alert actually do. What happens when that 3rd party service is having its own set of problems? Do we need to simulate those conditions?

If you aren't certain what testers can contribute when pairing with a developer writing code, these types of questions are a nice example. Even if it doesn't uncover an issue, it deepens overall system knowledge which may help testers identify similar issues when new integrations occur. If it is an issue, then it came up during active development, instead of randomly in production, because chances are testing environments may have some integrations disabled or simply not have the volume of activity to trigger any degradation in services. 

### Monitoring vs. Automating

So much is made of automation in the testing space. In reflecting over this book, what has struck me is that the end to end (e2e) automated tests generated by testers seems like a means to hold fast to old tester activities in a changing world. Do the manual faster. This kind of testing wasn't great when we had months between releases in waterfall, it wasn't great in Agile when testing could easily slip into a sprint behind dev, and it certainly feels misguided now.

It's not that end to end tests are bad, but as a tester you have to recognize that even when well done, their quality and ROI in comparison to other types of automated tests is low. However, it's common to see efforts of upskilling testers to gain development skills so they can contribute to e2e test suites. 

Being able to code and automate is great, but a growing sweet spot for testers is going deep in tooling around production monitoring and analysis. I hadn't considered the rich value that monitoring as testing can give testers, but this book really highlights this.

>Understand how you can influence culture through collaboration  <-- quote is from earlier in book>

With the quote above in mind, consider what increases your ability to influence team culture towards quality: Adding e2e tests?  *or* learning tools that help you in deepening your knowledge about your customers usage of the product and the subsequent effects of the changes being applied to the application they are trying to use? I'm fairly certain a good sized part of the evolving role of the tester is monitoring and synthesizing that information into insights you can later share while features are being developed.


## Testing In DevOps Environments


## And more...
This is just what I took away from the second 2 sections of [A Practical Guide To Testing in Devops](https://leanpub.com/testingindevops). I'll be covering the rest in upcoming posts, but don't wait on me its a good read check it out for yourself!