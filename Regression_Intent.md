
## What is Implementation?
>*The process of putting a decision or plan into effect; execution.*

Implementation is how technology is applied / utilized to help realize the intent behind a software solution. This includes things like is data stored in relational database like SQL or in a document database link MongoDB, is it hosted in AWS or Azure, down to even what language its written in. 

## What is Intent?

>*the state of mind with which an act is done : volition*

Digging deeper looking at **Volition:**
> *the power of choosing or determining* 

Framing this into a software context, it's not about personal intent as a tester.  *Intent* is the explicit decision where your software has been designed to solve problems for its domain, how to best try to service your customers needs. It's also a major part of what separates your product from its competitors.

## The Needs of the User over Technological Choice

Implementation is then just an artifact of search for the best means of acting on that intent given the team available.

Regression testing is about preserving the business value of software in the face of new changes. As testers we want to ensure that our customers experience remains uninterrupted even if the original implementation has been modified.

When changes are made that are not visible to our users to we want the effects of those changes to be exactly that, invisible to users. 

### Example: User Interface Update
Over time a product has added 3 different check boxes to a form. Depending on the permutation specific behavior is expected, however not all permutations are valid. In a later release the UI is updated so instead of the old 3 options, the user is presented with a choice of valid states but behind the scenes, the same 3 options are configured. 

### Regression Effects?

While the UI has been cleaned up to provide a better experience the intent of the form remains the same. Feature testing of that change verifies that the UI changes set the 3 options appropriately. Going forward regression testing of the existing functionality remains unchanged since the intent of the test remains unchanged. 

How the test was setup is an artifact of the implementation. Any manual test cases (or automated tests) structured to reflect this focus on intent, will then also remain unchanged. Worst case only minor changes may be needed to reflect the forms new implementation.

The same process applies to your product if you migrate from a desktop to web based experience or change from Azure to Amazon Web Services. By having core of your regression testing centered around what an end user intends to do rather than explicitly how or where things are done testers can more deeply 

## You Know What I Mean?

You may be thinking hold on, without precise (implementation) steps to follow people testing in the future may make mistakes and/or miss things. 

How often you hear people say "**you know what I mean**"? Maybe something similar? 

That everyday phrase is a person expressing that their actual words may not reflect what they were really trying to express.  If people do this when speaking to one another when they already have additional expressive cues like tone and body language, imagine the potential effect it has when writing things like test cases or code. 

Explicit does not guarantee results, or clearer understanding of actions and results. In fact you may see this when a person you are speaking with does not know what you mean. Sometimes no matter how hard to try to be more clear you just can't get the message across. It results in both people walking away frustrated and confused.

If you've ever said "you know what I mean" or even felt compelled to, you know how gratifying it can be when the other person clearly does understand. Perhaps even better, the person stops you before you have a chance to say it, and says "**I know what you mean**".  That feeling, the unspoken mutual understanding of intent that testers should strive create in test design and to maintain in their product release to release. 