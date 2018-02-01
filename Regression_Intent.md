# Intent over Implementation


## What is Intent?

>*the state of mind with which an act is done : volition*

Digging deeper looking at volition,

**Volition:**
> *the power of choosing or determining* 


## What is Implementation?
>*The process of putting a decision or plan into effect; execution.*

## Regression Testing is an intention centric endeavor. 

Framing this into a software context, it's not about personal intent as a tester,  *intent* is how your software has chosen to solve problems for its domain, how it's trying to service your customers needs.

Intent is a major part of what separates the system under test from its competitors. *Implementation* is how technology is applied / utilized to help realize the intent behind a software solution. 

Regression testing is about preserving the business value of software in the face of new changes. As testers we want to ensure that our customers experience remains uninterrupted even if the original implementation has been modified.

When changes are made that are not visible to our users to we want the effects of those changes to be exactly that, invisible to users. 

### Example
 Over time a product has added 3 different yet inter-related check boxes to a form. Depending on the permutation specific behavior is expected, however not all permutations are valid. In a later release the UI is updated so instead of the old 3 options, the user is presented with a choice of valid states but behind the scenes, the same 3 options are configured. 

### How does this effect testing?

Feature testing of that change verifies that the UI changes set the 3 options correctly. Going forward regression testing of the existing functionality 

Whether tracked in test cases or automated tests, regression testing of any behavior dependant on those feature remain unchanged. Worst case only minor changes to the preconditions to the tests change.

The intent of the test remains unchanged, how the test was setup is an artifact of the implementation and has no bearing on future testing. 

The same process applies to your product if you add a mobile app or migrate from a desktop to web based experience. By having core of your regression testing centered around what an end user intends to do rather than explicitly how or where things are done testers can more deeply 



