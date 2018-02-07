
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

That definition inspired a vision of a person battling the elements...


## Respect the boundaries of previous phases of testing

Regression isn't about rediscovery, if it was a bug before, it's still a bug now. 

Each time you test something there are differences, whether intentional or not. This may include things like: system state, application state,  rate/speed of execution, input values, etc. If variances between test runs / regression sweeps uncover new bugs that is great, it doesn't mean that testers should be explicitly seeking out these differences. Testers being aware of the opportunity regression testing provides to intelligently add additional coverage through mindful awareness of varied input is great <better, clearer wording>.  It adds new and deeper value to a process that is often dismissed as wasted effort.  

Regression is an assessment rather than an investigation. Feature testing is where the deep dive investigation occurs. Regression testing is the follow up appointment to assess the current state of things. 

## Know your Elevator Pitch
When people talk about complete testing or coverage, they have uncertainty about changes and they are looking for is assurance that risk is being managed. Trying to explain that complete testing is impossible only feeds that uncertainty.

The place to strive for *complete* is in test strategy. 

 The solution as a tester isn't to test more, it's to have a plan. I don't mean a massive document using old test plan templates. You want a test strategy that you can explain to someone in a couple minutes.

This doesn't mean your strategy ends with the elevator pitch. The pitch just sells certainty, you still need to be able to dive deeper to explain motivations and execution. The goal is to refocus issues to be framed in the evolution of strategy not on people and the amount of testing they performed. Strategy can grow incrementally, and can scale, exhaustive attempts at complete regression testing is a sunk cost, which benefits are lost the moment the product ships.

### Elevator Pitch Testing 
This elavator pitch approach also applies to actual testing. 
Prioritize with a sliding window of time. 5 minute pitch, follow up
