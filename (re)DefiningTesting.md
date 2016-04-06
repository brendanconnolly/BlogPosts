It's really hard to explain to people why testing is a valuable activity if you can't describe what it is you are doing and why you are doing it. Intuition is a big part of testing, but intuition is fed by understanding. A good detective or doctor might have a hunch, but that hunch is supported by years of experience and education. If it's not then it's really just a guess. 

So being able to speak clearly and effectively about testing is a big deal. A stepping stone in clear communication is a shared vocabulary. It makes sense then that an organization like the [International Software Testing Qualifications Board (ISTQB)](http://www.istqb.org/) would make part of its certification understanding common terms in testing. To be completely transparent I am not certified by the ISTQB or all that familiar with their materials. I noticed their definitions being shared on twitter by the [ISTQB Tester](https://twitter.com/istqb_tester), and a few caused me to raise an eyebrow so I have selected a few to dig into from the [ISTQB Glossary](http://www.astqb.org/glossary/). 

### Accuracy Testing

>Testing to determine the accuracy of a software product. 

I question my understanding of a subject if I have to use the term I am defining within its definition, so it set my spidey-senses a tingling when I first read this definition. There are mixed feelings within the testing community about certifications, so my first thought was this might be someone trolling on twitter. This is not the case. [Accuracy Testing](http://www.astqb.org/glossary/search/accuracy%20testing) as defined above is part of the *Advanced Test Analyst* body of knowledge. 

At its core, isn't any or all testing in some way *determining the accuracy of a software product*? In what context is the accuracy being measured? Is it the accuracy between the developers and end users expectations? Is it about precision, like the testing the [department of weights and measures](http://www.nist.gov/pml/wmd/) does on scales and other devices? 
  

### Compliance Testing

> Testing to determine the compliance of the component or system.

Seeing a second example of the using the word in its own definition made me wonder if all the definitions would be like this. I understand the intent of this definition, it's referring to verifying if software is conforming to the rules prescribed by a regulated standard or governing body. The definition doesn't state that though, it's relying on an implied context, which probably means that it's not worth defining. 

Would testing client integration with an external api really be referred to as compliance testing? I think I could make a case where it would fit that definition. However, I would seriously question a tester's competency if they used compliance testing to describe that activity. The difference here is that I can have that conversation with a tester, and we might both come out of it learning from each other. Definitions are put into place to avoid needing these types of conversations.  


### Dynamic Testing

>Testing that involves the execution of the software of a component or system.

This one marked is as part of the ISTQB Foundation level certification, and I have to say it was quite a let down. How exciting does *Dynamic Testing* sound, seriously the name sells itself. Looking at the definition, doesn't testing itself require the software to be running? Seems like a non starter if you are trying to test without the software. 


### Static Testing 

>Testing of a software development artifact, e.g., requirements, design or code, without execution of these artifacts, e.g., reviews or static analysis.
 
I looked this one up in the glossary after seeing the dynamic testing definition, and thinking is there really static testing? No, that would be [*analysis*](http://stackoverflow.com/questions/49716/what-is-static-code-analysis), like the code analyzing tools [JSLint](http://www.jslint.com/) or [NDepend](http://www.ndepend.com/). But ISTQB beat me to the punch, and even included static analysis as an example. 

I draw the line here, there's no such thing as static testing. Testing is an interactive process, it's cause and effect. Analysis of code, or requirements or other artifacts can help inform your testing, [White Box Testing](https://en.wikipedia.org/wiki/White-box_testing) is fairly standard example.  Saying looking at an artifact is testing is kind of like calling spell and grammar check  *static editing* and sending a your writing to a book editor *dynamic editing*. These are just not the same class of things, both may catch errors or potential issues but just because they may find the same issue does not mean they are the same thing. 


### Test

All these very specific definitions for different types of testing made me wonder... How are they defining a test? 

> A set of one or more test cases.

Seems fairly obtuse, a test is essentially a term for quantification or grouping. That seems troubling, lets see what a test case is:
>A set of input values, execution preconditions, expected results and execution postconditions, developed for a particular objective or test condition, such as to exercise a particular program path or to verify compliance with a specific requirement. 

I'm not sure all aspects of a program are specifically required, software usage is highly subjective. I don't have a problem with the test case definition, that is generally how I understand them. They are explicit and prescriptive, and based on that I find their value dubious. The big issue here is that a test is just a series of these test cases. Therefore testing is entirely scriptable right? It's just a matter of documenting all the conditions...

Well, I see they also have a defintion for testing, maybe I'll save that one for another post...
 