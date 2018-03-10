

Test Driven Development is rooted in a test first approach to  developing software. This is concretely defined in the first of the [three simple laws of TDD](http://programmer.97things.oreilly.com/wiki/index.php/The_Three_Laws_of_Test-Driven_Development):

> 1. You are not allowed to write any production code unless it is to make a failing unit test pass

This is a pretty counter intuitive concept, it flips the traditional development process on its head. To those that aren't already believers in the benefits of TDD, you can expect some immediate and serious [side eye]() at the very thought of this.  

### But there's nothing to actually test, it won't even compile... My IDE will be lit up like a Christmas Tree

Funny enough, this is exactly the point. 

Getting started is hard, even when there are good requirements. The requirements generally only include the what the software should do, the how software goes about satisfying the requirements, its implementation is largely at discretion of the developer writing the code.

What happens next is that someone sits down to solve a high level problem with a high level understanding of what they want to do. It's only natural for a person to focus on the destination rather than the road to get there. The resulting solution has a tendency to then be a byproduct of organic growth rather than explicit design, functional but not necessarily testable.    

## Software's a Journey not a Destination 

Everyone's got deadlines, the immediate need is functioning code in a timely manner but, building software is almost never a one way trip. The fastest code to write isn't necessarily mean the code is the fastest to maintain, and [teams in general spend more time in existing code than writing new code.]((https://blog.codinghorror.com/when-understanding-means-rewriting/)) 
 
The requirement to create a failing test first forces the developer to consider how the end result of her code will be utilized. This shifts the immediate focus away from completing the feature as a whole. The developer then becomes both the first consumer and reviewer of their code, work transitions away from organic growth to explicit intent.

## Organic Testing

Whats the first thing you do as a tester when you get handed a piece of software and are asked to test it? Now, you might ask some questions to clarify its purpose or to identify expected personas, but on average most testers dive right in and start taking a tour and exploring. 

This isn't pointing a finger at that process and passing judgement, testers need to learn about the software they are testing. But let's pause and ask, *what's driving this process?* Where does it start? When does it end? Does it stop when you find the first bug? Or do you take note and carry on? 

While exploratory testing, testers efforts can sometimes drift, ending up meandering through intricate use cases or hunting for the minimum reproduction steps for a bug. There is value in these practices, it may not always best serve stakeholders. The value of all bugs found isn't equal, and breadth of testing coverage across the system under test may be more important than more in depth testing of certain areas. 

Contexts vary, so should our approach. Just as the first law of TDD acts as a lens to focus on structuring code in an intentional and testable fashion, testers can benefit from a guiding principle to concentrate their actions. 

## First Law of Test Driven Testing 
> 1. No testing unless you have identified and defined objective

This likely sounds just as counter-intuitive as the first law of TDD. If you are new to a project, how can you identify and clearly define objectives about software you know little about? 

One of the concepts TDD is associated with is [emergent design](https://en.wikipedia.org/wiki/Emergent_Design). This is something we can recognize from agile replacing waterfall development practices, idea that a better more effective design will result working iteratively rather than the effort to design everything upfront. Just like adopting agile process didn't mean there was no planning, TDD doesn't presuppose all high level design or architecture discussions or considerations.





## Exploration vs. Expedition



