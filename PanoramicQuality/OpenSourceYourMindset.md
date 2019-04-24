# Open Sourcing Your Mindset

As development has shifted from waterfall to agile and now DevOps, at each stage you see developers taking on more responsibility and accountability.

Waterfall was isolationist, building silos around different groups in software development. Developers owned the act of coding and in the stereotypical developer way, had little to no interest what happened before or after they coded. Other roles on teams in many ways acted as insulators to keep external forces away from developers.

Agile was developers pulling that insulation away, shifting themselves left and taking more ownership of the product creation process. Developers found they required a real time feedback loop to build the right things and successfully react to change.

DevOps is essentially the same process on the right side of the spectrum. Development takes more ownership of deployment, monitoring and supporting the applications health. It's just too slow and cumbersome to react to the requirements of maintaining applications by filtering feedback through separate teams at scale. 

The benefits of integration outweigh the cost of the additional responsibility.

## Code Continuous
To cope with the additional responsibilities, developers have turned to their trusty friend *code*.

With agile we see rise of tooling developed for *Continuous Integration* to alleviate the pain and reduce the risk in iterative development.

In DevOps we see the rise of code and tools supporting *Continuous Deployment*. Even when many teams already had product installers, or automated deployments what was missing was the integration of that information.

If developers are owning more of the product as well as release and deployments, then testing naturally gets swept up in the process. In fact we see this pattern emerging with the concept of *Continuous Testing*. Code is being written, tools created to help solve the issue of integrating test execution and reporting into teams release pipeline. The feedback loop is extended to provide rapid information to make it easier and faster for development to be responsive to change.

## Continuous Testing

Automated testing is a loaded term. In developer circles it almost exclusively means unit and possibly integration tests. In QA it almost almost exclusively means end to end (e2e) tests, and is often synonymous with *Selenium*.

On teams where both sets of tests exist, their worlds may seldom interact. Developers may be aware of the *e2e* tests but they probably aren't writing them and even less likely running them.

Continuous Testing has nothing to do with the testing that most QA team members are most familiar with, exploratory testing. The purpose of the code and tooling that comprises a pipeline isn't for there to be some manual intervention required part of the way through it. Putting exploratory testing somewhere in the later stages for the pipeline is akin to pointing a fire hose at someone and asking them to direct the flow to the next stage.

If the [speed of DevOps](https://www.brendanconnolly.net/quality-at-the-speed-of-devops/) wasn't enough, the presence of *continuous testing* only puts more pressure on testers, simply because more attention is being drawn to testing. 

Automation engineers and product engineers are being drawn closer together. The importance and relevance of end to end automated tests is becoming more of a reality for product developers as they become run regularly as a post deploy verification tests.

While code is being thrown at testing with newfound passion, exploratory testers need to be prepared for their time in the spotlight. If automated tests are running all the time what tests are you doing? What makes them special? Why are they required before we can deploy?

## What do you do different than Selenium?

Before you dismiss that question, pause and consider what all selenium and the tests it drives truly provide.

Selenium is cross browser, scalable, schedulable, repeatable, and can provide logs and screenshots of its tests. Can you compete with that?

Flaky, slow, and wrong sometimes, you say? And you and all other humans aren't?

Conversations that try to explain using people instead of machines for testing software can end up justifying them under the guise of *there are some tests that aren't good candidates for automation*.

### Don't settle for executing tests that don't have enough ROI to automate.

This type of conversation relies on the belief that testing is comprised to two elements: *test case creation* and *test execution*. Perhaps at its most base level testing is just that, the value proposition of the role is in the nuance that a skilled tester can provide to teams through those elements.

Testers do more than a fill a gap in automated test coverage. The problem is many testers express this nuance solely through actions.

Developers produce code, a measurable artifact from their effort. The generation of that artifact is often backed by computer science, a formalized area of study. Artifacts of effort are reassuring, people like to see the fruits of their labors. Tangible results can be measured and quantified, they might even help estimate future effort.

A testers value tends to be recognized at the same rate as relationships develop. Testers get characterized as [folk heroes](https://en.wikipedia.org/wiki/Folk_hero) rather than members of a skilled profession. There's no trade, education, or craft just individuals saving the day periodically. 

### The Intuition trap

Even when teams do value testing, people are usually primarily concerned with the progression or regression of testing efforts. Testers comments in stand-ups can easily turn into a user story status change report:

>*Passed this ticket, working this ticket, no blockers*

If you aren't taking the opportunity to discuss your actual actions in stand ups, then you may fall prey to the intuition trap. When you talk about your work this way, sometimes you end up actually working this way.

## Open Source Your Mindset

It's fun being a hero, but there's no skill in being *Superman* or *Superwoman* ( I was going to say Wonder Woman, but she actually trained and I think everyone recognized that. So if you are the teams Wonder Woman then kudos, you have serious skills but I digress).

When testing goes smoothly the result is *nothing*. Testing isn't required for things to go right, it just might help prevent a thing going wrong.

Open sourcing your mindset means *teaching* others another way to look at and interact with their code, or the product. This cuts both ways though, it means being willing to accept a pull request of outside perspective. Openly integrating new ideas into your *testers mindset*.

### Replace Execution with Communication
[Testing is a performance](http://www.satisfice.com/blog/archives/1346). Like acting or athletics there might be a script or gameplan to start with but there is a lot going on behind the scenes, adapting to circumstance and being thought up on the fly. It's intuition driven.

When actions, practices and motivations are not being verbalized and expressed to the team and stakeholders it puts testing on the level of superstitions and token time sacrifices to the quality gods.

Testers need to pry open this experience, expose the internals driving motivations. Breaking out of that shell grants visibility into a testers actions and motivations to provide a context for team members to attribute value.

### Replace Isolation with Collaboration

It can be uncomfortable or difficult to open up and share what goes through your *testing mindset*.

The additional ownership developers have taken in DevOps has changed relationship dynamics. What was at one point a contentious us vs. them relationship is much more open. There just isn't the time to have as much formal process driven communication. Success at scale requires collaboration, pairing and mobbing more. 

When with developers, it's an opportunity to test at their desk, against their local changes.  There are risks testing here, the developers local setup is definitely different than production but so are the testing and staging environments. Let go of the taboo of ** it works on my machine** and consider what can be tested here and what needs to be covered on a different stage. Take the opportunity to work together when the code is the freshest in the developers mind and where they are most comfortable.

It's not only about working with developers, Mob testing with *UX* and *Product* alongside developers is a way to draw the entire team together. When the team is together seeing how the application is working it bypasses all the communication gates. There is no need for a separate follow-up conversations to loop someone in, that person can see and feel how things are working by being a part of the group experience.

### Replace Tedium with Stratagem
Teams are more open to testing and sharing in quality than ever. Testers have been building quality mindsets for years. Developers are building tooling but teams are looking for guidance and mentorship in *Quality*. 

Testing isn't just button pressing, by showing that through communication and working together we elevate our status. Draw people together, into the quality circle and enable the team to be more comfortable and aware of testing. We can set working agreements, talk about overarching strategy for how testing throughout the development cycle builds quality in. We can embrace automated testing as a team activity where unit, integration and end to end coverage is part of a teams strategy for mitigating risk. We can forgo complete control of testing and opt into being a voice of authority and expertise in quality.





