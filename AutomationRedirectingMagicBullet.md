Automation: Redirecting the Magic Bullet

Automated testing is a pretty contentious subject in the testing world. We spend a great deal of time and energy distinguishing between what a tester does while engaging with a product and what the autoamted tests or [checks]() are doing. Justifying why we need to have a person actually interact with the software instead of using robotic verifiction. 

Automation isn't all bad though. In fact when its done reasonably well, it has some characteristics that make it downright appealing.
>**Disclaimer**: This post isn't about contradicting those benefits of automation with equally trite support for dedicated test roles on software teams. 


#### Explicit
Automated tests can only do what they are programmed to do. This is commonly identified a weakness of these checks, they miss the nuance and the tacit. They can't mimick a humans observation, intuition and experience. 
The issue here is that many testers often cannot succintly convey their practices, or explain their approach. It's as though we are divinely inspired all the time. It's not that I haven't uncovered my share of bugs that fit that description, where I find the magic set of circumstances without explicit intention. I'm not spending 40+ hours a week wandering around with my [divining rods]() looking for bugs. 

In the engineering centered world that testers occupy it seems like a leap of faith to expect that this won't be challenged or sought to be replaced by concrete approximations with explicitly defined intentions.

#### Quantifiable
Data makes people feel more comfortable about decisions. It allows the ownership of a decision to shift away from the individual.  This is baked into the nature of automated tests, there is a finite number of tests and they either pass or fail. Every time the suite runs a report makes the current status available for consumption. Automation feeds that data to it's customers regularly and on demand.

#### Extensible
Good automation evolves over time to maintain the symbiotic link it has with the software it is checking. Lessons are learned by the people authoring the tests or the underlying framework, and the assertions made in the automated tests improve. The quality of the product may remain unchanged but the quality of the automation should improve. 

### Yeah, Yeah, Yeah 

Fantastic, we've heard all this before in some form or fashion and it's gotten a little (ok, maybe a very) tiresome. The value of automation here is that the exercise of writing automated tests can help testers become better testers. 
>**Disclaimer**: This post is not about the benefits of testers learning to code.

It's about the thought exercise that has to occur. Writing an automated test involves distilling actions down into direct actionable and repeatable steps. It forces you to examine your software through a different lens. As great as humans are about identifying subtle or nuanced issues, we can be just as bad about overlooking those same types of issues. The very experience or knowledge you have may fundamentally bias your experience in a way that you miss whole classes of bugs or usability concerns. As testers we do our best to combat this with things like personas but it doesn't make the process perfect. 

### You are Teaching a Program
The act of trying to automate something turns you into an infant, bumping around your software trying to learn how to walk through it. You are forced to recognize your actions and then reproduce them artificially and this analysis often uncovers your internal bias. 

The act of automating also enforces repetition and pattern awareness. Part of your individual testing may be considering your products internal consistency, making sure the same behavior, patterns or workflows of existing functionality are maintained in new features. Having to build automation for those behaviors will give you an intimate awareness of them since you have to build the logic for driving through them. It will also help you recognize inconsistency since the patterns you taught your self may break down or not apply. You will then be frustrated because your tests should just work since they follow internal convention, this models the same frustration your customers may be experiencing. 

### Quantifying Intentions and Verifications
Once your automation can *walk* the education process still isn't over. You have to know what you need to test, to translate your internal testing process into actions. You may realize that not everything can be encoded into an automated check, but it will force you to reason about what you are actually doing while testing. It becomes easier to prioritize and speak definitively about your testing if you have thought about your actual process. 

Automated tests are about creating approximations. As you better understand your own process and what is possible inside an automated check you are better able to identify processes that may approximate some portion of what you are phyisically doing. Let the computer do some of the heavy lifting and allow you to focus your efforts. 

### Recognizing Strengths and Weaknesses

It's not that automation is enabling testers up to do other things or freeing them from repetition, that implies the two actions of the two are somewhat synonymous or interchangeable and they aren't. What it does do is help define what tasks people should do and what are best served by computers. We need to embrace these practices and learn how they can strengthen us. Many developers have adopted test driven development and had it change their perspective on software creation. It's not that TDD is the panacea that many describe it as and it's not a replacement for testing as we understand it but it doesn't mean it hasn't helped people be better at their craft.

Over the years we have done ourselves a disservice by trying to describe our actions and value through detailed test plans and testcases and scripts. These artifacts do nothing to help explain or describe the value that human execution of these plans adds. We need to be able to describe what we actually do and how that shows value, otherwise we legitimize the debate that our roles can be automated. 

Test Automation, or whatever you choose to call it isn't evil. It's just one more tool in your utility belt to help you understand your software and even give insight into your testing. 

