There's pressure to find bugs. If testers are not reporting bugs it leads to all kinds of uncomfortable questions.

There's the usual management need to provide tangible and quantifiable evidence that the cost of testing is being balanced or offset by some improvement in quality. Customers may also be question the test cycle, and its effect on the release date. If you aren't finding bugs what are you doing and do we need you or your services? 

There's also internal pressures to find bugs. It's not like I am hoping to find bugs, the whole "I'm a tester, I break stuff" routine really rubs me the wrong way. However, finding bugs often offers a sense of validation to my efforts and approach. When none are found its easy for self-doubt to creep in.

You might be thinking, but testers increase quality in ways besides the bugs that are reported. That is true, but what metrics support them? Better design, improved usability, customer insights, I won't try to list all the value that testers and testing adds because I don't feel the need to justify that value. That doesn't mean other's won't question it.

As a means to compensate, enter heavily structured, prescriptive test cases...

### The Fallacy

It's well intentioned, and sounds great, you just document the steps you will be taking while testing. Plan it out, get it reviewed, then get started. The planning helps structure your approach. The review is an opportunity for risk mitigation and training. At the end we have a beautiful document that quantifies progress of the testing, offers protection against doubters/finger pointers in the event a problem is uncovered after release, and it that can even be handed off as a training tool. 

### The Impossibility 

We already know we [can't test everything](http://www.kaner.com/pdfs/imposs.pdf), how can we document everything?

Testing is a human process, it's a performance. We don't ask actors to document each step of their process before stepping on the stage for earlier review and to serve as a record for other actors to study. Could you imagine if the Academy of Motion Pictures or the Broadway League had to review these notes before giving an Oscar or Tony Award. 
 
### The Friction

Just like usability is a concern when testing software, usability of a process is also a serious concern. 
A common starting place is using spreadsheets to track tests, your team may even have its own template to ease the process. How hard is it to fit and describe the test and its steps in excel rows? It may seem easy at first but it gets complicated (or ugly fast), nested steps, complex validation criteria. If you shift the wrong row or column you might throw off formulas downstream or you may end up with a document that is as complex to read was to write. It's also a chore to maintain, since you may add, change or remove tests the format my change and need updating. Not to mention. Do you also have to take the status from excel and update it elsewhere?

There are whole software suites sold for test case management. If nothing else this let's you know that some businesses believe that this is enough of a problem domain there is potential for profit in selling a solution. Even with the perfect solution, does it integrate with the rest of tools the team is using? 

If the process is cumbersome it slows people down and makes it harder to get started testing rather than surf the web, get some coffee, or talk to a neighbor.


### The End Result
Whats recorded in the test cases, rarely reflects an accurate representation of the tester performing the testing. This goes for the original tester and any subsequent tester that may use that document as a reference. Prescriptive test documentation is not really a training tool, at best it's a placebo, at worst it's a license to mindlessly follow directions. You end up just following directions rather than testings, tuning out rather than plugging in. 

It's heavy and slow. These detailed test cases are just like the heavy detailed spec's that agile processes have ran away from. I'm not saying we shouldn't plan our test approach or document what we have done, but these heavily detailed testcases and test plans are not the solution. If it's not capturing all that we are doing while testing, and its not encouraging / teaching new testers to do quality work why are we doing it? 



