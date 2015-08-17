Basics: What is Done, the beginnings of test case design
===============
Definition of Done in testing.

 When can we ship it? What do you have left? When will it be done? An important question is, what is done?
 No matter what you can't ever test everything. For better or worse you cannot always understand ahead of time
 the complete stress that your users will put the product through.
 
 But really, do you need to? 
 
 Agile development spends a good deal of energy focusing on a definition of Done. [source] 
 It helps to make answering those initial question feel a little less esoteric. But still how do you know your testing is done? 
 
 Unit tests have code coverage to help provide some guidance, but what about other types of testing? 
 Is it just a gut check from your QA team in the standup? I think we'd all feel a little better if this were a bit more
 of a data driven decision.
  
 Is it a sum of sums for the number of test cases marked complete for the stories of the sprint? 
 Do all tests need to be run and passing? Can some be skipped or some be failing? 
 Like code coverage, there are diminishing returns and the percentage of coverage increases and the effort to increase coverage does not necessarily correlate to the increase in quality. The real important thing is to have a consensus on the team. 
 Agree ahead of time on how tests should be prioritized, and what constitutes releasable quality. Then post those guidelines and adjust or review after releases. 
  
  Quality guidelines can useful even in day to day interactions. People can take bugs personally, and data deflates blame.
  So much of testing and development is how the interactions between team play out. How the people logging and fixing the bug percieve each
  other can play a major factor. Archetypes of the overzealous tester or the dismissive developer can easily lead to animosity between teams.
  I bet we've all seen arguements over the validity of a logged bug or it's severity. So let data bear the brunt of the friction instead. 
   
    "Hey Joe, I know this bug may not seem critical but I checked against our guidelines and I think it meets the criteria. 
      Lets bring it up at the meeting and discuss maybe we need to clarify or update the standards."  
  
  It's not a magic bullet, but it is a useful tool and it scales from individual bugs/issues to release time.   
  Either the qualifications for release are met and we ship, or we have to make a plan to resolve the blockages. 
  No individual polling, no raise your hand if we can't ship today pressure just direct actionable data.    

So you know what done is, how do you start designing, categorizing and modeling your testing? 
I'll dig deeper in a later blog post but here's little tid bit to get you started

Priority 1 Acceptance Criteria 
Hopefully there is some meta data on the feature that you are testing to give you some insight on its overall goal.
In cases where acceptance criteria is defined there (you are off to a good start), these become the basis of your tests.
They are the minimum requirements that you must confirm in testing.

If you don't have this information, its up to you as an advocate for your users to try and begin modeling and setting expectations.

Talk/Interview to gain insight on what is expected to come out of the feature. 
This means conversations with both the product team member(s) and developer(s) either separately or together. 
It doesn't have to be a big kick off meeting but we all understand things a little differently. 
Making sure we are all on the same page can resolve problems before they are introduced. 
It is the cheapest time in the development process and often leads to better designs and happier users.

Fleshing out the requirements can be a treasure trove for test creation, especially when the initial feature definition is minimal or unclear.
  
