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
expanding and enabling testing in production. Production is no longer reserved for fully formed features, production becomes a shared workplace for customers and engineers. Shipping doesn't mean done, it just means ready to evaluate in the realm of our customers. feature flags isolate changes...

Developers can't punt code over the wall because they now have  direct line of visibility and responsibility to customers. Testers don't need to be quality cops, we act as a service to developers, since developers own supporting features as much as creating them. Testers are no longer shackled to quality through testing. 


> Testers may struggle to find the balance of investigating new features without impending release

With small frequent changes, we can't be focused on executing tests. Testers are required to act more as oracles of insight, tracking causality 

Monitoring over Automating, automation seems more of a means to hold fast to old tester activities in a changing world. Do the manual faster. This kind of testing wasn't great when we had months between releases in waterfall, it wasn't great in Agile when testing could easily slip into a sprint behind dev, and it certainly feels misguided now. 

Agile delivered software and value at the end of each sprint, DevOps introduces a steady stream changes. 
Agile helped enable the cultural shift that makes DevOps possible. Agile helped break down disicipline silos, enabling healthier communication

Testing may not be referenced explicitly in DevOps literature, because it doesn't require specific attention, it is a part of each and every step. This is what testers sought for years, quality has to be integrated at all steps. Mindful collaboration across all phases design to support. In fact it surfaces many tester owned tasks to the entire team. Customer problems etc. I'm not sure about continuous testing, but I like the sound of continuous quality

> When testing is expected to be part of everything. What exactly is your responsibility? How should you contribute?


>Understand how you can influence culture through collaboration
 
### test strategy retrospective
share and level set to gain consensus, consensus lowers individual risk as the decisions are not solely owned by testers. 

Get to the middle of your teams, in the mix so as to facilitate quality
--Own (this seems good for mnemonic)
own overall quality

what does our testing look like, from unit to manual...

more about the understanding of risks involved in changes than test cases

### Agile testing assessment
Because of its collaborative nature, if you aren't comfortable testing in an Agile environment you might struggle to leap straight to devops

How do you identify quality...

### Communicating
Be more than the testing status announcer in standups, people know you are the tester, saying testing this, finished testing that isn't good enough. You are being opaque instead of transparent. I think testers are quiet because they are uncertain about their status on the team. Are people going to care about the details of my work? By not sharing though you make it easier for testing activities to be dismissed. If you talk like its just checking a box, then people will think you are just checking boxes doing surface verifications.

> Take the opportunity...to verbally create an image in someones mid of the activities you're undertaking.

This provides surface area for other members to collaborate with you. 
Pictures may prove more beneficial than written notes. (what if I did x days of visuals for standups, a visual daily update)

Debrief vs. Peer review -> peer review is before an activity, like pairing on strategy.

> Pairing is high productivity

It forces focus in those pairing and discourages interruptions

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
