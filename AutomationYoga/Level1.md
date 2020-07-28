## Level 1: Framework Exists, Encapsulation

## Why mature to level 1

Don't let the 0 in level 0 fool you. Level 0 can be very productive and may actually deliver on the promises and hopes you, your mananger or your team may have had. 
Even when it all goes well, when the new to automation, or a new tool is picked up by someone or handed off to a team, theres going to be an element of ad hoc automation as excitement about automation or the tool leads to a tendency to automating all kinds of things. 

there may also be a lot of local machine tests where each person has their own suite tailored to their specific needs and environment [...]


You may also see varying quality across the test suite whether its the newness of the tool, or the drive to get more people involved in the automation effort. 
As the test suite grows and the number of contributors to the project grows reliability typically becomes more and more of an issue. 


you might also feel some tool churn based pain. 


### Problems Being Solved



The honeymoon kind of comes to an end once the newness wears off and some tests start to fail and the cost maintaining the test suite.  But you can't keep trust in a system where tests fail, frequently, sometimes or all of the time. It's harder keeping an automation suite than getting one.  It's a lot less fun getting tasked to fix exisitng tests, especially ones you didn't write. 

It's a lot less fun getting tasked to fix exisitng tests, especially ones you didn't write. The next level up is usually motivated by a need or want to unify your automation. 

We want tests that a framework where automation is: 

Portable - internally consistent
Maintainable
Reliable


### Pattern Focused

level 1 formalizes automation

What we are looking for at this level is uniformity and reliability of in our tests. At level 0 the only structures are self imposed or required by the tool.

Patterns 

Conventions
Technical ? 

Centralized
Conistent



#### I'm better than level 0, (Why not skip it)

Patterns and structure are generally a good thing. The thing is there is real value in addressing problems as you start to feel the pain rather than anticipating problems and trying to fix them before they arrive. When you feel the pain you can concretely identify the cause and start to allievate it. You decision is immediately supportable because you have real tangible things that you can point to. Without these tangible and visible issues you are asking at some level for people to just trust that you know whats best. 

[...] guessing more...
If a developer were making similar statements abotu a feature your team was developing, theres a good chance we might be a little more suspect of this decision. You might here words like *YAGNI*, *Premature Optimization* and one of my favorites *Premature Abstraction*. 

If we believe that building applications iteratively letting feedback guide our decisions is a good idea, what makes automation any different? Its just more softeware why excuse your automation framework and test suite from similar conceptual scrutiny? [...] its probably becuase theres carryover of that hope and magic level thinking 

[Order] Patterns and conventions are just process for your code. They help standardize the codebase, and create kind of a common language across your framework and test suite.  There are still trade offs, and a co##st to pay for standardization. The beuracracy of automation goes up, as well as the complexity and sometimes the barrier to entry into your codebase. Its not enough that these things exist they have to be maintaned and enforced. For the maturity of your automation to level up so do the expectations for your team of automators. 

The team side is where things get a little shaky. [... automation army of 1, employee churn, lack of understanding why]

It doesn't mean to ignore lessons you've learned before, but check some of your assumptions. How quick are you to accept the need for a base class and would you treat removing a base class with the same perspective. Inheirtance, and other optimizations like shared components are often lauded and feel good when introduced. But just like when code hits production, sometimes you start to see that maybe the real world landscape isn't quite as uniform as your abstractions assumed they would be. 

The more your code is code is consoliodated, shared and abstracted, the harder it becomes to reason about the risk in changing it. 

Its then a lot harder to unwind that deicision than to introduce it. Once you stack up a few of these cases,  sooner or later someone is going to pitch a reboot project because the pain and friction involved. 

Automation can feel like a race to a solution. For automation to be successful we really need to take the long view and have the maturity to prefer emergent abstractions and optimizations. Building up the willpower to create strong abstractions. [green lantern abstractions]




**Are we more judgemental of automation because we have a limited feedback loop and limited audience.**


### What is lost
The transition from ad hoc automation with individual team members scripts being collasced into a more formal structure, means you are leaving autoamtion behind. Its easy to condescend an unstructured or somewhat unreliable peice of automation that someone hacked together. 
If that script is accruing value for the author or consumer then it should have a place in your automation strategy. But we get so swept up in making automated tests fit into the cookie cutter "good candidate" for automation. 

False dichotomy, non binary world with arbitrary standards. I think sometimes we are so focused on proving and justifying and satisfying the engineering side of testing 
