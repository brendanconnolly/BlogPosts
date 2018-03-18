
One of the most popular ways the TDD process is described is referred to as the red-green-refactor cycle. Start with a failing test (red), make the test pass (green), clean up and polish so you are leaving things in better shape than when you arrived (refactor).

It's a very relatable process that can help you visualize following the [three laws of TDD](http://programmer.97things.oreilly.com/wiki/index.php/The_Three_Laws_of_Test-Driven_Development). The cycle isn't magic though, exactly how to start, or what the best next step is doesn't just [emerge]() and jump to the forefront of our minds as soon as the test passes or refactoring is done. 

The red green refactor cycle can belie the fact there needs to be time allotted to active design throughout the development process. [James Shore](http://www.jamesshore.com/Blog/Red-Green-Refactor.html) introduces the *Think* step at the beginning of the cycle.

> Figure out what test will best move your code towards completion. (Take as much time as you need. This is the hardest step for beginners.)

This takes the voodoo out of TDD, and creates a cycle of continuos design. We can take advantage of a micro-feedback cycle while still keeping our sights on on design at both functional levels and high level design level. 

[Cecil Williams](https://www.sourceallies.com/2014/06/updated-tdd-mantra/) extends the cycle by appending a *commit* step after refactoring. 
> Making a commit at this point will improve your process even more. You will have autonomous chunks of work that are small and easy to understand.

With this addition developers are checking in their changes after each cycle. This encapsulates each iteration, making forward progress extremely safe. At any point we can travel back to a point where we know things were in good working order. We also get the benefit of being able to visually compare how code is progressing over time. 

## A Test Driven Testing Mantra

By doing a mashup of the standard red-green-refactor cycle with both the additional *think* and *commit* steps we end up with a process we can transpose onto a testers workflow.

### Think

This initial step is basically the same for testers as developers. Consider the high level testing strategy being utilized for the project, then take the time to decide what small chunk of testing should I pursue to best make progress toward those goals.

### Red

Now we know what we want to accomplish, decompose that goal into the smallest series of tests you can perform to satisfy that goal. We are establishing a clear set of intentions and outcomes we seek from upcoming actions. A helpful way to establish these intentions can be establishing testing charters in the *Explore*, *With*, *To Discover* format which [Elizabeth Hendrickson](http://testobsessed.com/) defines in her book [Explore It!](https://pragprog.com/book/ehxta/explore-it).

### Green

Here is where we translate intention into actions. Step through the software to measure how your expectations compare to the reality of implementation. The [FEW HICCUPS](http://www.developsense.com/blog/2012/07/few-hiccupps/comment-page-1/) mnemonic is a good heuristic tool to help you identify dimensions of consistency that you may want to consider.

Be cognizant of how the system under test may differ from you mental model and consider what that inconsistency implies. Do we need to reevaluate our understanding of the system under test, the persona we are utilizing or is this a bug that we need to draw attention to. 

We need to stay true to our charter and not actively pursue the questions that are rising to the surface. Instead we are mindful and aware of our process and actions. We are translating our theoretical intention into a factual reality. Like scientists on an expedition we note observations but avoid jumping to conclusions so as to not interrupt current subject of study. 

### Refactor

We have now have gathered information and can make more informed decisions about what we need to do next. This is where we start to unpack our observations. Armed with this new insight, we can refactor our future actions and assumptions. We are shifting from an intuition driven process to a data driven process. It's not that we want to ignore our intuitions, we just want to remove over dependence on it. Intuition can serve as our inspiration for future data gathering expeditions. 

### Commit

We have foregone the process of upfront test case documentation. In lieu of that we have a high level strategy and an iterative learning based approach. That doesn't mean we don't need to document testing activities. 

When developers check code in they are generally required to associate a message describing the work that is being committed into source control. The message acts as a context to view the series of changes being applied. 

Testers can follow the same practice and take the time to document our findings. Take a moment, summarize actions and outcomes or clean up the notes you may have taken during testing and link this to the work item you are testing. This can increase visibility into the testing process. 

This also may be a good time to investigate or log or communicate any bugs or issues you uncovered. 

