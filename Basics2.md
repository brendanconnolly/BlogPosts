Some Basics of Functional Testing: Getting Started and Using Equivalance Classes and Boundaries
==============================


[we need a sample app for test scenarios]

So you've got your feature to test. You've read through the requirements/acceptance criteria to start planning your tests.
If none exist, you've started planning out questions so you can interview/discuss with the developers / feature owner to set and confirm expectations.

Next to begin imagining how the feature will function. Step through the process in your mind. 
Think about the Who, What, When, and How for the system under test. 
This is just a heuristic to get you thinking so don't feel pressure to flesh out all the details in the beginning.

>***Who***  This is where we start to develop basic personas/actors for test scenarios. This sets the stage for everything else. It defines the roles that have access to
>and make use of the new functionality. Is it Admin only? Is a login required? This is the start of establishing the state required for the test.   

>***What*** This is the feature. The others establish context for the action, this is the action. What information will have to be entered? 
>What will you expect to see while in the process and what will the outcomes be? 

>***When*** Goes beyond a question of time. This is a control point for where state is set. Precondition and post conditions are established here.  

>***Where*** This refinement of the context in which the user experience will occur. Think localization, globalization. Mobile or desktop, client or server.  

>***How*** Here we look at usability, testability, performance.   [more]
 
Now you have your basic mental model for testing, you want to focus your time where it will have impact and business value. 
Equivalence classes help to avoid repetitive testing with little chance of finding new issues. 
This is a industry standard term so lets define it

>***Equivalance Classes ***: If you expect the same results from two tests, you consider them equivalent. A group of tests forms an equivalence class if you believe that:
> - They all test the same thing.
> - If one test catches a bug, the others probably will too.
> - If one tests doesn't catch a bug, the others probably won't either.
><cite>[1]</cite> 


What you want to do is break down your test scenarios you just modeled into equivalance classes. [Example]
There are positive and negative classes  

###Testing you Boundaries

Boudary testing uses the equivalence classes described above and looks for values at the edges of those partitions. It can go beyond basic input fields though.
The first time an app or page loads is a boundary. After login and logout are boundaries.  

 Why focus attention on the boundaries? Think about how software is written, inputs are given then evaluated to determine what is done. 
 The code is going to be defined based on equivalence classes and boundaries they will just most likely be in if-else or case statements. 
 So testing boundaries narrows our focus to finding cases where differences control logic are likely to be, hence a higher liklihood that issues can be found. 
 
 Just like in equivalence classes there are positive and negative boundaries. The line were input goes from valid to invalid can be fertile grounds for 
 finding software issues. We are typically venturing into the area of the unexpected and unspeced. The main focus of development is usually 
 [Explain based on example]   
  

Allow for exploration. I don't have a problem with scripted tests but I do believe it minimizes the effectiveness of the testing if only scripted tests can be run. 
Some of my best insights come from unstructured interaction with the product and feature. Learning the product and understanding your customer are some basic tenents
for quality. 

[1]: Testing Computer Software Second Edition, Cem Kaner, Jack Falk, Huing Quoc Nguyen    