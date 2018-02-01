# Leading By Example

Testers, even when embedded on teams are outsiders.  Their value is derived from, maintained by, and continually put at risk this status.

In the early days of software development there was a sense of sanctity around testing, testers were housed on separate teams, segregated in different organizational hierarchies in order to avoid the corrupting influence of developers. A testers vision was pure, the systems under test were black boxes to which testers could apply input and make judgments upon the outputs. While the intent was to remain unbiased advocates for quality,the tides turned adversarial and bureaucratic. As agile methodologies arose and more popularly accepted there was little place for dedicated outsiders proxying for customer feedback.

Large dedicated testing teams gave way to test or quality specialists embedded on smaller teams.  While the relationships have improved, outsider status remains. A testers value is not desribed by a set of tangible or measurable skills, it is linked to their unique *mindset*. The wielder of this mindset takes on mystic or supernatural qualities. Imbued with a unique world view that grants insight into circumstances and actions that when executed can expose critical issues or vulnerabilities in software. 

A testers value is now measured by how differently they think than the rest of their team. Their true skills and influence are easier to dismiss since their benefit is attributed to the intangible. A token offering to the quality gods. 

## Methodologies & Frameworks

Companies and individuals have placed a great deal of effort into creating and standardizing development practices. This provides a shared vocabulary for explaining and understanding. Teams can use that shared vocabulary to effectively communicate ideas and progress. There just isn’t a common framework for how testing is integrated onto teams. 


## Influence Through Alignment

If people don't really know what you do, how you do it, or how to talk about it how successful can you be? 

Just like development, testers need common practices and vocabulary to be able to communicate their intents and actions easily. The problem is that testing does not carry the weight and influence to support organizations and teams adopting whole new processes and terminology. 

It's not a slight to testing, testing simply isn't the dominant role or activity on a software team. This means testing practices and vocabulary need to align with accepted development standards, processes and terms. Additional semantics and processes only serve to invoke the historical baggage of testing as a bureaucratic and costly process. 

The process of aligning is a three step process:

### Comprehend
Everything begins with comprehending the principles and benefits of the methodology or process. This doesn't mean you need to become a world class expert in a subject but you need a comfortable working understanding. 

### Co-Opt
Armed with new understanding, we can identify when core concepts and vocabulary can be recontextualized to address or explain aspects of testing. This allows you to frame testing activities into processes that your team has already accepted and sees value in. 

### Communicate
The simple act of attempting to understand the core concepts to the point of being able to better engage in team discussions can have a dramatic impact on peoples perceptions of your abilities. You'd be surprised how eager and excited people are to share, teach or mentor you once you show interest.

This understanding grants a sort of credibility, and you can begin to integrate the co-opted versions of these processes into discussions about your work. 

Lets look at a couple examples:

## Test Automation
Automation has already followed this model it is an outcome of manufacturing's influence on software development. Organizations recognized that to gain efficiency and speed activities they needed to leverage computing power the way assembly lines utilized robotics. 

People saw a working blueprint and studied it. In gaining understanding were able to take those ideas and co-opt them into their own domain. This made acceptance and communication of these new ideas easier since there was a working and tangible example to point to. 

Automation is also the friendliest boundary between developers, testers and even product team members. It's a safe place where people can learn from each other, developers can talk test, and testers can talk code since generally each respective group isn't expected to be an expert in the others area but they are expected to collaborate on a shared output.  


## Sprint Planning
In sprint planning teams create estimates and identify the tasks required to complete user stories. Developers are commonly expected to dissect their work into functional tasks that are easily measurable, describable and shareable. 

This is much less likely to be true for testing work, its more likely to be a single "test it" task. A more detailed account of the testing effort may be tracked in separate systems or documented in test plans. Why is should testing functionality need to be tracked separately from implementing functionality?  It's because a testers are outsiders whose process is less defined and understood. At its root it is an alignment issue. 

So we recognize there is dissonance between a testers role in sprint planning and a developers. First we seek to comprehend why it is developers are expected to provide such transparency for their work. 

It wasn't that long ago that development was as much a black box of activity as testing often still is today. In that time developers expected to be given a project and some requirements then be left alone until it was ready. Development was spending a great deal of time and resources only to have the end result often be delivered late and frequently not be what people expected or wanted. Agile process sought to remedy this by breaking work up into smaller ore consumable pieces, that enabled more frequent communication and demonstration. In short they increased transparency in order to create an active feedback loop.

## Test Planning
In that problem description change to be test, instead of develop and you have a very real and current description of testing on many teams today. It's not unusual to see a stream of agile development leading to a mini testing waterfall. 

We have a blueprint for success, it just needs to be co-opted to so that test planning looks more like agile developments sprint planning. We want to replace the mini testing waterfall cycle in a sprint with a agile testing workflow. 

Skip the exhaustively documented test plan. It's not that we don't need a plan, but does development have a dev plan document? Is there a detailed requirements document for your stories or high level acceptance criteria?  Consider having a testing strategy discussion, outline acceptance criteria for the testing effort.

No more *bucket-o-testing*. If you would balk at a developer having a *code it* task or one single changeset checked in for a feature, then you should be equally outraged by testing following the same pattern. 

Start with a single task (or a few) in areas you know need testing. Make sure each one has a focused and explicit intent that can be verbally described, effectively time boxed, and with results or outcomes that can be easily communicated. Then take an iterative approach. As you complete a testing task reflect on what you have learned to asses progress then add or remove tasks as needed. 


## Code Review
Code review is a pretty straight forward concept, before code is integrated into a product it is shared with a person or group and is inspected and feedback provided. As you can imagine this process isn't universally liked, nor is there an explicit standard against which the code is evaluated. If code quality is subjective, what are teams looking to get out of code review. 

The first thing people think is it's done to catch bugs. Next in line is the belief its done to maintain the style, standards and conventions in the code are consistently applied. These things may occur in code review, but the true benefit is that people behave differently when they know they are being observed. The fact that a developer knows they will have to show their code to someone else changes decisions they make while writing code. 

Code review also provides an opportunity to converse about the code. Knowledge can be transferred about why things were done a specific way, increasing familiarity proactively instead of only looking at other peoples code when emergencies happen. 

You may be thinking the idea of sitting in a room and being interrogated and scrutinized sounds like an awful and time consuming proposition. To combat this often today code review is not done face to face or even in real-time. Teams often use tooling that allows a person to request review, share changes and provide feedback. This makes some of the subjective issues less likely to occur, and allows reviews to focus things like design and unit test coverage. 

## Test Review
Even if you team is writing detailed test cases, the act of testing can be ambiguous in nature. The issue is testers often do not have access to the feedback loop provided by code review. In code review the work the developer actually did is discussed and shared. If there is a test review it is usually focused on what will be tested (test plan), not the testing actually performed. This is justified by the idea that we want to make sure good testing will be performed. In this sense why have developers code up a solution first, isn't the risk the same? 

Instead of reviewing what might be done, shift towards discussing strategy up front then regroup as work is completed to review progress and provide an opportunity discuss coverage and feedback.

Taking it a step further consider an asynchronous tooling supported approach that developers are using to cut down on the time requirements for review meetings. Test plans and test cases are so often attributed value as a training tool. Instead of counting test cases and reporting everything in an often ambiguous pass/fail selection, consider having testers take notes of their actual actions and thoughts while testing. These can be review and archived for reference just like code.

## Communicating Leadership

In all theses examples the first step is seeking to understand.  The more deeply we understand the more insight we gain. The more insight, the more effective our communication. The more effective our communication the greater influence as tester has. This allows a tester to be a functioning example to their team. 

This can be tester to tester, modeling how testers can take successful processes from roles on their team and integrate them into testing practices to foster deeper alignment and integration of testers onto teams. 

It can also be tester to developer. You maybe able more successful in advocating for better sprint planning or healthy code reviews by modeling those activities successfully in a testing context first. It's hard to argue with a working example already occurring on your team. 

Take the opportunity to grow your influence and lead by example.





