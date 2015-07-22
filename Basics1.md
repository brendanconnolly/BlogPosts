Basics: What is Done, the beginnings of test case design
===============
Definition of Done in testing.

 When can we ship it? What do you have left? When will it be done? An implrtant question is, what is done?
 No matter what you can't ever test everything. For better or worse you cannot always understand ahead of time
 the complete stress that your users will put the product through.
 But really, do you need to? 
 
 Agile development spends a good deal of energy focusing on a definition of Done. [source] 
 It is used to make answering those initial question feel a little less esoteric. But still how do you know your 
 testing is done? 
 
 Unit tests have code coverage to help provide some guidance, but what about higher level testing? [more?] 
 Is it  just a gut check from your QA team in the standup? I think we'd all feel a little better if this were a bit more
 of a data driven decision.
  Is it a sum of sums for the number of test cases marked complete for the stories of the sprint? 
  Do all tests need to be run and passing? Can some be skipped or some be failing? 
  Like code coverage, there are diminishing returns and the percentage of 
  coverage increases and the effort to increase coverage does not necessarily correlate to the increase in quality.
  The real important thing is to have a consensus on the team. Agree ahead of time on how tests should be prioritized, 
  and what constitutes releasable quality. Then post those guidelines and adjust or review after releases. 
  
  Its intimidating to be the lone holdout as the release date arrives. The key is letting data drive decisions, data is impersonal. 
  Either the qualifications for release are met and we ship, or we have to make a plan to resolve the blockages.    
[source for choosing %]


So you know what done is, next is deciding the tests and categorizing them to fit your guidelines. 
I'll dig deeper in the next blog post but here's little tid bit to get you started

Priority 1 Acceptance Criteria [alternative names]]
Hopefully there is some meta data on the feature that you are testing to give you some insight on its overall goal.
In cases where acceptance criteria is defined there (you are off to a good start), these become the basis of your tests.
If you don't have this information, its up to you as an advocate for your users to try and begin modeling and setting expectations.
Talk/Interview to gain insight on what is expected to come out of this effort. 
This means conversations with theboth product team member(s) and developer(s) either separately or together. 
It doesn't have to be a big kick off meeting but we all understand things a little differently. 
Making sure we are all on the same page can resolve problems before they are introduced. 
It is the cheapest time in the development process and often leads to better designs and happier users.

[Some Conclusion]
[Next] Translating acceptance criteria to tests...
  
