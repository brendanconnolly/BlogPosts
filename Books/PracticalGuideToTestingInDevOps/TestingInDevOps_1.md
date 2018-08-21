![book cover](http://www.brendanconnolly.net/wp-content/uploads/2018/08/devops.png)

When deciding to read [A Practical Guide To Testing in Devops](https://leanpub.com/testingindevops) by [Katrina Clokie](http://katrinatester.blogspot.com/) for [#30DaysOfTesting](https://twitter.com/hashtag/30daysoftesting). I wanted to focus on avoiding the temptation to get destination oriented and just finish the book. In the vein of [Testopsies](http://www.brendanconnolly.net/testopsies/) (a concept I learned about at from [Michael Bolton](http://http//www.developsense.com/) at CAST2016), I wanted to give time for both inspection and introspection.

To that end, the plan I arrived at was:
1. Read the book start to finish
2. Divide the book into 3 parts
3. Read each part twice (repeating before moving on)

## In the Beginning

The book sets the stage by describing how testing has transitioned as software development practices have evolved from waterfall to agile and further into *devOps*.

> In waterfall, testers have sole ownership of test strategy and execution. There is comfort in knowing that testing as an activity belongs to us. Testing is our role and our identity in the team

The ownership of testing acting as a means of identity really resonated with me. While it was an unhealthy and unreasonable expectation for testers own quality, it was a mantle I tried to uphold with pride. In the face of hopeless odds I was doing my bit for my customers.

> Agile Challenges our definition of testing and its ownership

> DevOps pushes testing outwards

It expands and enables testing in production. Production is no longer reserved for fully formed features, production becomes a shared workplace for customers and engineers. Shipping doesn't mean done, it just means ready to evaluate in the realm of our customers. feature flags isolate changes...

Developers can't punt code over the wall because they now have direct line of visibility and responsibility to customers. Testers don't need to be quality cops, we act as a service to developers, since developers own supporting features as much as creating them. Testers are no longer shackled to quality through testing.

> Testers may struggle to find the balance of investigating new features without impeding release

With small frequent changes, we can't be focused on only executing tests. Testers are required to act more as oracles of insight, tracking and anticipating causality of changes.

## Testing in a DevOps Culture

### Where does a tester fit

Agile delivered software and value at the end of each sprint, DevOps introduces a steady stream changes.
Agile helped enable the cultural shift breaking down discipline silos, enabling healthier communication, and devops in general.

Testing may not be referenced explicitly in DevOps literature, because it doesn't require specific attention, it is a part of each and every step. This is what testers sought for years, quality has to be integrated at all steps. Mindful collaboration across all phases design to support. In fact it surfaces many tester owned tasks to the entire team. Customer problems etc. I'm not sure about continuous testing, but I like the sound of continuous quality

> When testing is expected to be part of everything. What exactly is your responsibility? How should you contribute?

One of the first things this section recommends is starting with a **test strategy retrospective**. This isn't something I had really considered before, I'm kind of accustomed to testing being marginalized either by organizations or by individual developers. While I won't get into the model that Katrina shares, the concept seems extremely healthy for teams.

It provides an opportunity for team members to share what testing activities you think are going on, who is performing those activities and how you think its working out. As the overall testing straategy is discussed it level sets expectations and allows for consensus to be gained. This consensus lowers individual risk as the decisions are not solely owned by testers.

Many times in my career I've felt like testing was a black box to people outside of the role. As time went by and trust and relationships got built individually this changed but it could be a slow and sometimes painful or blame-filled process, I think the testing strategy retrospective would have helped alleviate some of that friction.

It also seems like nice mechanism to allow testers gain a better grasp of what testing activities are being done by developers or other members of the team. Stepping beyond just writing test cases and focus more on getting an understanding of the risks involved in changes.

It like a map for where you cna start pairing with other roles, so you move away from the periphery and get to the middle of your teams, nestled deep in the mix so as to facilitate quality.

### Collaborating and Communicating

Much of the later half of the section *Testing in a DevOps Culture* dives into some specifics as to how testers can *blaze a trail* and build pathways for collaboration with different areas of their organizations.

It's good stuff, but what struck me more than these specifics was about the importance of a testers communication inside of their teams.

Testers need to be more than the testing status announcer in standups. People know you are the tester, saying testing this, finished testing that isn't good enough. You are being opaque instead of transparent.

I think testers are quiet because they are uncertain about their status on the team. Are people going to care about the details of my work? By not sharing though you make it easier for testing activities to be dismissed. If you talk like its just checking a box, then people will think you are just checking boxes doing surface verifications.

> Take the opportunity...to verbally create an image in someones mid of the activities you're undertaking.

This provides surface area for other members to collaborate with you.

This section also defines a distinction between

#### Debrief vs. Peer review
Katrina states that peer review is before an activity is done, like pairing on strategy. Conversely debrief is after, like a postmortem.

This didn't ring entirely true to me as my understanding of peer review (which may be flawed) is different. It is about reviewing the findings of work completed before it goes to be published or shared. In software it seems similar to code review, a problem was identified a strategy was worked up and implemented and now feedback and validation is sought before moving forward further. It's a minor quibble though, and likely a matter of perspective.

#### Pairing

> Pairing is high productivity

It forces focus in those pairing and discourages interruptions. This is a nice insight and pro tip especially for those of us in open office arrangements fraught with interruptions.

## Testing In Development
> Unit tests, integration tests, and end-to-end tests... focus on confirming behavior at different levels of abstraction

Unit tests and their relationship (and impact) to end-to-end tests is a tricky thing for testers to reconcile. They are so wholly different that they can feel irrelevant to a tester, just one more thing a developer does.

When I read this, I immediately loved it. I hadn't really thought about different testing levels being testing different abstractions. It's certainly true, just a truth I hadn't realized, somehow in my mind the layers were mostly separate with some overlap.

Instead, I see it more clearly as a length of chain. Each method a developer writes is meant to encapsulate some logic. Then methods are chained together to further encapsulate some form of behavior. Finally behaviors are chained together to form a solution. That's oversimplifying things, but it gives a more holistic view of the relationship between the traditional layers of testing. Unit tests focus on a single link in the products chain. Integration tests focus on logical groupings of multiple links in the chain. Finally, end-to-end is where the entire length of chain is evaluated.

### On Systems of Feedback

Feedback while testing in development is broken up into two categories *Automation* and *Exploration*.

> Testing that happens during development is best spent exploring...

This counters what testers are so frequently expected to do while code is being written, which is write end-to-end tests based on current expectations. I hadn't questioned this sentiment much before, but after reading and reflecting on this section of the book it strikes me as waterfall-ish. Developers, go code it. Testers, go prep your tests.

Automation provides information but not thoughtful insight. It's not that automation doesn't have value, it's just that while features are being developed is the best time to examine and question what is trying to be accomplished.

Exploring while there is potential for change makes a lot of sense. Once code has been deployed and customers are using it, any newfound insight or issues a tester shares can be difficult to address. Customers might be impacted, or designs may need to change, those potential risks devalue the insight and value a tester can provide.

True insight, is where testers add value through holistic understanding of the system under test. Automated testing will almost always be shallow, humans add the depth even in basic testing scenarios. This makes automation that testers typically develop a perfect candidate for later cycles before release.

Maybe the question isn't just are you automating the right things, but is the right thing being automated?

### Testing Timeline
> Automated deployment (commit-&gt; deploy) squeezes exploration into either end of the pipeline (in dev | in production)

The evaporation of a "testing" phase is a real challenge for testers. Testing has to adapt in devOps, testers need to find ways to contribute before code is complete and after its deployed. When code is deploying multiple times a day, there just isn't room for extended periods of testing most development. It can be easy to fall into the verification trap, just checking the developers changes do what they say. If you take too long, you slow the whole team because you are disrupting a stream of work often spread across different developers.

#### Feature Toggles

Feature flags can enable incremental development and reduce risk of large merges in an active code base.
Testers need to be aware of the toggles, the potential states and conditions and potential related toggles and how the toggles are managed. If there's an external dependency what happens when it fails?

This is also a means to safely test in production. Feature flags allow teams to control the impact of change on actual consumers, while getting code safely and quickly into the environment it will be used in. Testing and staging servers just aren't the same as production. First pass of testing may just be that old behaviors are not affected by the latest changes. This way you are more free to test safely in production.

Complexity in managing and testing feature toggles can be a smell that strategy and implementation of toggle may need attention/remediation.

## And more...
This is just what I took away from the first 2 sections of [A Practical Guide To Testing in Devops](https://leanpub.com/testingindevops). I'll be covering the rest in upcoming posts, but don't wait on me its a good read check it out for yourself!