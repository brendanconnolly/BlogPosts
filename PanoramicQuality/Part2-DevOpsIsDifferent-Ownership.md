## DevOps is Different

## Ownership
As development has shifted from waterfall to agile and now dev ops, at each stage you see developers taking on more responsibility and accountability. 

Waterfall was isolationist, developers owned the act of coding, and in the stereotypical developer way had little to no interest what happened before or after they coded. Other roles on the teams in many ways acted as insulators to keep external forces away from developers. 

Agile was developers pulling the insulation away and shifting themselves left and taking more ownership of the product creation process. Developers required a real time feedback loop to build the right things and successfully react to change. 

Dev Ops is essentially the same process on the right side of the spectrum. Development takes more ownership of deployment, monitoring and application support. It's just too slow and cumbersome to react to the requirements of maintaining applications by filtering feedback through separate teams at scale.  

The benefits of integration outweigh the cost of the additional responsibility. 

## Code Continuous
To cope with the additional responsibilities, developers turned to their trusty friend *code*. 

With agile we see rise of tooling developed for *Continuous Integration* to alleviate the pain and reduce the risk in iterative development. 

In DevOps we see the rise of code and tools supporting *Continuous Deployment*. Even when many teams already had product installers, or automated deployment what was missing was the integration of that information.  

If developers are owning more of the product, as well as the release and deployments then testing naturally gets swept up in the process. In fact we see this pattern emerging with the concept of *Continuous Testing*. Code is being written, tools created to help solve the issue of integrating test execution and reporting into teams release pipeline. 

## Continuous Testing

Automated testing is a loaded term. In developer circles it almost exclusively means unit and possibly integration tests. In QA it almost almost exclusively means end to end (e2e) tests, and is often synonymous with *Selenium*. 

On teams where both sets of tests exist their worlds may seldom interact. Developers may be aware of the *e2e* tests but they probably aren't writing them and less likely running them. 


Continuous Testing has nothing to do with the testing that most QA team members are most familiar with, exploratory testing. The purpose of the code and tooling the comprises a pipeline isn't for there to be some manual intervention required part of the way through it. Putting exploratory testing somewhere in the later stages for the pipeline is akin to pointing a fire hose at someone and asking them to direct the flow to the next stage. 

If the [speed of devOps]() wasn't enough, the presence of *continuous testing* only puts more pressure on testers, simply because more attention is being drawn to testing.  

Automation engineers and product engineers are being drawn closer together. The importance and relevance of end to end automated tests is becoming more of a reality for product developers as they become run regularly as a post deploy verification tests.

While code is being thrown at testing with newfound passion, exploratory testers need to be prepared for their time in the spotlight. If automated tests are running all the time what tests are you doing? What makes them special? Why are they required before we can deploy? 

## What do you do different than Selenium?

Before you dismiss that question, pause and consider what all selenium and the tests it drives truly provide. 

Selenium is cross browser, scalable, schedulable, repeatable, and can provide logs and screenshots of its tests. Can you compete with that? 

Flaky, slow, and wrong sometimes, you say? And you and all other humans aren't?

Conversations that try to explain using people instead of machines for testing software can end up justifying under the guise of *there are some tests that aren't good candidates for automation*. 

### Don't settle for executing tests that don't have enough ROI to automate.

This type of conversation relies on the belief that testing is comprised to two elements: *test case creation* and *test execution*. Perhaps at its most base level testing is just that, the value proposition of the role is in the nuance that a skilled tester can provide to teams through those elements. 

Testers do more than a fill a gap in automated test coverage. The problem is many testers express this nuance solely through actions. 

Developers produce code, a measurable artifact from their effort. The generation of that artifact is often backed by computer science, a formalized area of study. Artifacts of effort are reassuring, people like to see the fruits of their labors. Tangible results can be measure and quantified, they might even help estimate future effort.

A testers value tends to be recognized at the same rate as relationships develop. Testers get characterized as [folk heroes](https://en.wikipedia.org/wiki/Folk_hero) rather than members of a skilled profession. Theres no trade, or craft just individuals saving the day periodically.  

## Opensource Your Mindset

It's fun being a hero, but theres no skill in being *Superman* or *Superwoman* ( I was going to say Wonder Woman, but she actually trained and I think everyone recognized that. So if you are the teams Wonder Woman then kudos, you have serious skills but I digress). 

When testing goes smoothly the result is nothing. Testing isn't required for things to go right, it just might help prevent thing going wrong. 

Testers need to Actions, practices and motivations it can be verbalized puts testing on the level of superstitions and token time sacrifices to the quality gods. 

### The Intuition trap

Even when teams value testing, people are usually primarily concerned with the progression or regression of testing efforts. Testers comments in standups can easily turn into a user story status change report

>*Passed this ticket, working this ticket, no blockers*

If you aren't taking the opportunity to discussion your actual actions in stand ups then you may fall prey to the intuition trap. When you talk about your work this way, sometimes you end up actually working this way. 

[Testing is a performance](http://www.satisfice.com/blog/archives/1346), like acting or athletics there might be a script or gameplan to start with but there is a lot going on behind the scenes, being thought up on the fly, adapting to circumstance. It's intuition driven. 

Testers need to pry open this experience, expose the internals driving motivations.

### Replace Execution with Communication

Open sourcing your mindset means *teaching* developers another way to look at and interact with their code. 


### Replace Isolation with Collaboration

The additional ownership has changed relationship dynamics, what was at one point a contentious us vs. them relationship is much more open. Success at scale requires collaboration. This cuts both ways though. It can be uncomfortable or difficult to open up and share what goes through your *testing mindset*. 

Success means pairing with developers. Testing at their desk, against their local changes. 


### Replace Tedium with Stratagem 

