![testing you gotta be kitten me meme](http://www.brendanconnolly.net/wp-content/uploads/2016/04/testingCatMeme.jpg)

In [my last post](http://wp.me/p6vwxg-41) I took a look at some software testing definitions provided by the [ISTQB](http://http://www.istqb.org/). In that post I stated I did not think there was such a thing as static testing, which has sparked some debate so let's dive a little deeper. 

### Static Testing

It's defined by the ISTQB as:
>Testing of a software development artifact, e.g., requirements, design or code, without execution of these artifacts, e.g., reviews or static analysis.

The [Wikipedia](https://en.wikipedia.org/w/index.php?title=Static_testing) entry for static testing redirects to *Static Program Analysis* which falls more in line with how I would describe it. 

In [Cem Kaners' response](http://programmers.stackexchange.com/a/191735) to the Stack Overflow question on *Why do some consider static analysis testing and others do not?* explains that it depends on your definition of testing and provides two examples.
>Execution of the program with the intent of finding bugs -Glen Myers

Which Kaner concludes under this definition, static testing is a misnomer since the program must be running in order for testing to occur. This narrows the scope of software testing to investigations only occurring while the program is running. Ok, that may seem obvious but it also exposes an implied context that the static testing definition ignores. When talking about testing in the context of software, the words software testing and testing can and often are used interchangeably. Following that logic *static testing* and *static software testing* are synonymous. Just off the cuff, does that sound right to you? 

Consider other descriptors here that follow the same pattern: Performance Testing, Security Testing, Acceptance Testing, etc. None of these terms change the context of the system under test the way that static testing does. Static testing shifts the focus to artifacts related to the running software. 

Kaner then gives his definition of testing at the time:
>Empirical investigation of a software product or service in order to learn quality-related information about it

Even under this definition, he says it depends, but to quote him:
>It doesn't much feel like testing.

That sentiment pretty much sums up my feelings on static testing, but since it depends on the definition of testing lets take a look...
 
### Testing

#### ISTQB
>The process consisting of all lifecycle activities, both static and dynamic, concerned with planning, preparation and evaluation of software products and related work products to determine that they satisfy specified requirements, to demonstrate that they are fit for purpose and to detect defects.

It's been pointed out to me that the ISTQB has some definite credibility issues in testing community, so I don't want to beat a dead horse but that definition reads like an after thought to wrap other concepts instead of being the primary concern. 

So let's take a look at the context driven testing worlds testing definition from James Bachs' post [Testing and Checking Refined](http://www.satisfice.com/blog/archives/856)

>Testing is the process of evaluating a product by learning about it through exploration and experimentation, which includes to some degree: questioning, study, modeling, observation, inference, etc.

Let's contrast that with checking:
>The process of making evaluations by applying algorithmic decision rules to specific observations of a product.

Adding more detail:
>Checking is a process that can, in principle be performed by a tool instead of a human, whereas testing can only be supported by tools. 

and
>Testing is an open-ended investigation– think “Sherlock Holmes”– whereas checking is short for “fact checking” and focuses on specific facts and rules related to those facts.

Michael Boltons' earlier post [Testing Vs. Checking](http://www.developsense.com/blog/2009/08/testing-vs-checking/) offers some further insight. 
>Testing is, in part, the process of finding out whether our checks have been good enough.

Bolton is also quoted in the Bach posts which describes my reaction to static testing:
> there’s a world of difference between sheet music and a musical performance

These definitions do a much better job of describing testing, and as tester they resonate with my experience. But consider this you could change the word evaluate to *write* or *codify* in testing definition and you end up with an apt description of a software developer. After years of tension between testers and developers is the line that thin? 

Static testing frequently occurs as a developer writes their code. Developers are evaluating requirements, specifications, reference material and investigating until the code is checked in that process isn't completed and is open-ended. Along the way they may create unit tests to help confirm and define their findings, this then adds dynamic testing into the mix. The process may even repeat as code maybe formally or programmatically reviewed, and/or integration tests are written to test component interactions. This isn't a new revelation, Michael Bolton describes this (better) in the *Testing vs. Checking Is A Leaky Abstraction* segment in Testing vs. Checking.  

 By definition developers are both static and dynamic testers, which essentially covers the fully defined test spectrum. Let that fry your synapses as you think about it. Using those definitions, I can see how managers and developers could infer they do not need to hire a person with the dedicated role of testing. 

Maybe the real problem is that the terms testing and tester are both too general and too confining. I think I'll start referring to myself as a developer of quality, and if questioned explain testing is just a part of my process...
