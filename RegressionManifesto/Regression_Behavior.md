![ I Regress](http://www.brendanconnolly.net/wp-content/uploads/2018/01/IRegress.png)
Part 3 of a series of Core values for Regression Testing

## What is Behavior?
> the way in which something functions or operates 

Behavior is the personality of the software under test. Behavior stretches beyond just what your software does to also include how your software does things. 

## What are Bugs?
> an unexpected defect, fault, flaw, or imperfection 

Bugs can be thought of like personality flaws. Some personality flaws are deal breakers, some cause frustration, some we turn a blind eye to. 

## Regression isn't about Rediscovery

Regression testing isn't a no holds barred bug hunt, we are trying to spot anomalies. Unexpected behavior in areas that that are either thought to be unrelated or functionally equivalent to the existing release version. 

As time, new releases and employees pass by, different testers are going to be tasked with regression testing existing functionality. It's very easy to fall into attempting to blaze a trail retesting what has already been done, only now its weeks, months, years out of peoples minds.

If you aren't already familiar with the area that you are regression testing it may be worth starting your regression testing on your current release before you dive into the new release. Then you to start to build up a relationship with the product as it is, rather than what it might be. 

You can refine your radar for issues without clouding your judgement with the overhead of the possibility any problems are regressions from current work. 

If you start seeing issues in current release, then you pump your brakes. Don't let existing bugs block progress, take notes of what you are seeing then re-evaluate you approach. This might be a good time to ask team members some questions to make sure your expectations match up with domain or user requirements.

### Why not focus on Bugs

Each time you test something there are differences, whether intentional or not. This may include things like: system state, application state,  rate/speed of execution, input values, etc. If variances between test runs / regression sweeps uncover new bugs that is great, it doesn't mean that testers should be explicitly seeking out these differences. 

You might be asking why a business wouldn't want to address these issues, or why a previous tester didn't catch these bugs? Before you count yourself an expert, consider that customers have not reported these issues.

We all have personality quirks, some may rise to the level of character flaws and effect our relationships with other people, and others are overlooked or not noticed. 

It's the same with software, if it was a bug before, it's still a bug now. The presence of bugs, or lack there of is not necessarily an indication of quality. It may seem counter-intuitive but not all bugs require a fix, existence is not the main driver for resolution a defect needs to represent potential impact to users etc. 

New bugs in existing code just mean more time spent investigating functionality that may only tangentially be related to release. It's not that they may not be real bugs but at this point they are out in the field and it takes time to confirm reproduction steps, log the bug, etc. The bugs you find right now may just be distractions during release time. 

## Boundaries of Trust

### Would you Party with your Software?

People have a sliding scale of trust for the individuals we accept into our lives. There are acceptable levels of trust required for different roles in our life depend on the circumstances in which we interact. 

We group people into these categories naturally, coworkers, bosses,friends, acquaintances, family... These relationships are determined through experience, intuition and this is reinforced over the course of time. 

As new events and shared experiences are accrued the status of the relationship is re-evaluated. Co-workers may be promoted to friends, long term friends can naturally progress to a familial connections. Conversely, we may decide to let some relationships fall to the side.

We don't stop to redefine our friendship with someone before we answer if we are up for karaoke this weekend. 

Think about who you party with and why. When you are out to have a good time, you want to be comfortable, at a minimum you want people who won't detract from the experience. As the night progresses and depending on how hard you party, the risk level might rise. Maybe you need people you trust with your privacy and well being.  

It's not any different with software, users develop relationships with it and that in turn adds related expectations. The behavior of software needs to respect the type relationship users are required to have with it. 

### Know your Role

Depending on the market you serve, there are drastically different requirements for what makes a shippable product. 

Go / no go decisions are based on the perceived risk of the action and the participants. This *perceived risk* is a summary of previous experience, a snapshot. It is not a detailed unwinding of all past events. In the party metaphor, its a question of would I do this type of activity with these types of people.  

What works for an app on a mobile phone is going to be different than a personal medical device. Not all distinctions are so easily discernible, but as testers it's critically important to maintain a holistic view of software. This includes integrating understanding of the personality of the product, its specific behaviors and knowledge gained throughout the development life cycle. 

Testers develop of the behavioral familiarity relationships and categorizations at the time of feature testing. We actively search out bugs, so we can effectively define boundaries of trust with the system under test. When release approaches we can then quickly communicate these boundaries as a proxy for our users, to enable better, more informed decision making by product owners. 


 

