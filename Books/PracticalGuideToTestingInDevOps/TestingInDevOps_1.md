When deciding to read [A Practical Guide To Testing in Devops]() by [Katrina Clokie]() for [#30DaysOfTesting](). I wanted to focus on avoiding the temptation to get destination oriented and just finish the book. In the vein of [Testopsies]() (a concept I learned about at from [Michael Bolton]() at CAST2016), I wanted to give time for both inspection and introspection. 

To that end, the plan I arrived at was:
1. Read the book start to finish
2. Divide the book into 3 parts
3. Read each part twice (repeating before moving on)

## In the Beginning

The book sets the stage by describing how testing has transitioned as software development practices have evolved from waterfall to agile and further into *devops*.

> In waterfall, testers have sole ownership of test strategy and execution. There is comfort in knowing that testing as an activity belongs to us. Testing is our role and our identity in the team

The ownership of testing acting as a means of identity really resonated with me. While it was an unhealthy and unreasonable expectation for testers own quality, it was a mantle I tried to uphold with pride. In the face of hopeless odds I was doing my bit for my customers. 


> Agile Challenges our definition of testing and its ownership

> DevOps pushes testing outwards

It expands and enables testing in production. Production is no longer reserved for fully formed features, production becomes a shared workplace for customers and engineers. Shipping doesn't mean done, it just means ready to evaluate in the realm of our customers. feature flags isolate changes...

Developers can't punt code over the wall because they now have  direct line of visibility and responsibility to customers. Testers don't need to be quality cops, we act as a service to developers, since developers own supporting features as much as creating them. Testers are no longer shackled to quality through testing. 

> Testers may struggle to find the balance of investigating new features without impeding release

With small frequent changes, we can't be focused on only executing tests. Testers are required to act more as oracles of insight, tracking and anticipating causality of changes. 

## Testing in a DevOps Culture

### Where does a tester fit

Agile delivered software and value at the end of each sprint, DevOps introduces a steady stream changes. 
Agile helped enable the cultural shift breaking down disicipline silos, enabling healthier communication, and devops in general.

Testing may not be referenced explicitly in DevOps literature, because it doesn't require specific attention, it is a part of each and every step. This is what testers sought for years, quality has to be integrated at all steps. Mindful collaboration across all phases design to support. In fact it surfaces many tester owned tasks to the entire team. Customer problems etc. I'm not sure about continuous testing, but I like the sound of continuous quality

> When testing is expected to be part of everything. What exactly is your responsibility? How should you contribute?

One of the first things this section recommends is starting with a  **test strategy retrospective**. This isn't something I had really considered before, I'm kind of accustomed to testing being marginalized either by organizations or by individual developers. While I won't get into the model that Katrina shares, the concept seems extremely healthy for teams. 

It provides an opportunity for team members to share what testing activities you think are going on, who is performing those activities and how you think its working out. As the overall testing straategy is discussed it level sets expectations and allows for consensus to be gained. This consensus lowers individual risk as the decisions are not solely owned by testers. 

Many times in my career I've felt like testing was a black box to people outside of the role. As time went by and trust and relationships got built individually this changed but it could be a slow and sometimes painful or blame-filled process, I think the testing strategy retrospective would have helped alleviate some of that friction. 

It also seems like nice mechanism to allow testers gain a better grasp of what testing activities are being done by developers or other members of the team. Stepping beyond just writing test cases and focus more on getting an understanding of the risks involved in changes.

It like a map for where you cna start pairing with other roles, so you move away from the periphery and  get to the middle of your teams, nestled deep in the mix so as to facilitate quality. 

### Collaborating and Communicating

Much of the later half of the section *Testing in a DevOps Culture* dives into some specifics as to how testers can *blaze a trail* and build pathways for collaboration with different areas of their organizations. 

It's good stuff, but what struck me more than these specifics was about the importance of a testers communication inside of their teams. 

Testers need to be more than the testing status announcer in standups. People know you are the tester, saying testing this, finished testing that isn't good enough. You are being opaque instead of transparent. 

I think testers are quiet because they are uncertain about their status on the team. Are people going to care about the details of my work? By not sharing though you make it easier for testing activities to be dismissed. If you talk like its just checking a box, then people will think you are just checking boxes doing surface verifications.

> Take the opportunity...to verbally create an image in someones mid of the activities you're undertaking.

This provides surface area for other members to collaborate with you. 

This section also defines a distinction between

#### Debrief vs. Peer review 
Katrina states that peer review is before an activity is done, like pairing on strategy. Conversely debrief is after, like a post mortem. 

This didn't ring entirely true to me as my understanding of peer review (which may be flawed) is different. It is about reviewing the findings of work completed before it goes to be published or shared. In software it seems similar to code review, a problem was identified a strategy was worked up and implemented and now feedback and validation is sought before moving forward further. It's a minor quibble though, and likely a matter of perspective.

#### Pairing

> Pairing is high productivity

It forces focus in those pairing and discourages interruptions. This is a nice insight and pro tip especially for those of us in open office arrangements frought with interruptions. 


## Testing In Development
> Unit tests, integration tests, and end0to-end tests... focus on confirming behavior at different levels of abstraction

automation provides information but not thoughtful insight, this is where testers add value through holistic understanding of the SUT

inspection vs. introspection ? does this work

Automated testing will almost always be shallow, humans add the depth even in basic testing scenarios. [this is the sell for semi automated tests]

>automated deployment (commit-> deploy) squeezes exploration into either end of the pipeline (in dev | in production)

feature flags can enable incremental development and reduce risk of large merges in an active code base.
Testers need to be aware of the toggles, the potential states and conditions and potential related toggles nd how the toggles are managed. If theres an external dependency what happens when it fails?
Complexity in managing and testing feature toggles can be a smell that strategy and implementation of toggle may need attention/remediation

Bug bash & Crowd testing interesting but less applicable to my experience.
