![ I Regress](http://www.brendanconnolly.net/wp-content/uploads/2018/01/IRegress.png)
Part 2 of a series of Core values for Regression Testing

## What is Common?

> just satisfying accustomed criteria 

This definition is related to the concept of "*common decency*"

There's a secondary definition that colors our view
> lacking refinement

It may give you pause to consider it a good idea to describe something you get paid to do as lacking refinement. Test strategy should be refined, it should be honed and tailored to best fit your team, skills and product needs. Regression though, is a fraction of that overall vision. 

How often are the most newest or most junior testers on your team asked to be heavily involved in regression testing? Whether it's seen as lower risk, a learning opportunity or some other reason, it reduces to the same general reason. A less refined understanding of the product is deemed acceptable to accomplish the task. Teams want the more refined resources freed up to apply those skills to new areas that require the deeper levels of understanding. 

It's not a slight, it's just that in healthy software these trails have already been blazed, these should be well worn paths safe for customers to confidently meander.

## What is Complete?

> having all parts or elements; lacking nothing; whole; entire; full
 
When dealing feature testing we are confronted with the [*Impossibility Of Complete Testing*](http://www.testingeducation.org/BBST/foundations/Kaner_impossibility.pdf). If we can't hope to completely test everything when first implementing new functionality then we certainly don't have that possibility during regression testing. 

If not complete then what?  Testing is an exercise in focusing available energy and attention on mitigating the most amount of risk. Testers use tools like boundary conditions and equivalence partitioning to try to increase coverage while minimizing number of test cases required. This is simply average set of conditions that testing confronts every day, from initial planning, through feature testing and into regression cycles. There is not a moment where a tester isn't compromising, seeking the closest approximations of certainty that stakeholder demand.

By accepting this reality, regression testing can only ever hope to cover a fraction of the functional feature testing. While this may be understandable to testers it may cause some managers and stake holders to be uncomfortable. If we aren't testing everything then it is very important to be able to clearly elucidate our actions and their motivations.


## Respect the boundaries of previous phases of testing

Regression is an assessment rather than an investigation. Feature testing is where the deep dive investigation occurs. Regression testing is the follow up appointment to assess the current state of things. 

Like a doctor reviewing the patients medical history and current prescriptions before providing a diagnosis. It is meant to determine if previously implemented functionality remains intact as viewed through the lens of these recent changes.  

This does not mean it is not fertile ground for testers, be aware of the opportunity regression testing provides. Regression allows testers intelligently add additional coverage through mindful awareness of varied inputs, data sets, etc. This can add new and deeper value to a process that is often dismissed as wasted effort without consuming additional time. 

## Know your Elevator Pitch

Every tester around release time sooner or later gets the a classic questions like "*Did we test everything?*" or  "*What percent of testing is left?*". 

The person asking this isn't usually a tester, and it's fairly likely they aren't really all that interested in understanding testing. 

What you need is [elevator pitch](https://www.themuse.com/advice/perfect-pitch-how-to-nail-your-elevator-speech).
> a concise, compelling introduction that can be communicated in the amount of time it takes someone to ride the elevator to her floor.

When people talk about complete testing or coverage, they have uncertainty about changes and they are looking for is assurance that risk is being managed. Trying to explain that complete testing is impossible only feeds that uncertainty.

The testing elevator pitch should be crafted to quickly express how the test process is trying assuage that uncertainty without the false impression that somehow every possible test case has been identified and is being executed. 

If you try to sell complete testing, blame will follow. Testers can't say there are no bugs remaining, but we can briefly but clearly express how tests were identified, prioritized and given the current rate of progress estimate the unit of time required to work through these tests. 

### Elevator Pitch Testing 
This elevator pitch approach also applies to how actual testing can be done. Start with knowing the bare minimum testing needed to ship an emergency release. If you know that and can describe what you doing, the situations and reasoning behind them then you have a foundation to build from. 

This foundation is the equivalent of the 3-5 minute elevator pitch. In the conversational metaphor, the longer you have to discuss and explain the greater detail and depth you can convey. Additional testing is just a matter of prioritizing effort with a sliding window of time. 

In our case (regression) testing becomes a function of all most common tests that can be executed within the confines of the window of time we have before we have to release.

## The place to strive for *complete* is in test strategy. 

The solution as a tester isn't to test more, it's to have a plan. I don't mean a massive document using old test plan templates. You want a test strategy that you can explain to someone in a couple minutes.

This doesn't mean your strategy ends with the elevator pitch. The pitch just sells certainty, you still need to be able to dive deeper to explain motivations and execution. The goal is to refocus issues to be framed in the evolution of strategy not on people and the amount of testing they performed.

Strategy can grow incrementally, and scale. Exhaustive attempts at complete testing are a sunk cost, the benefits of which are lost the moment the product ships.


