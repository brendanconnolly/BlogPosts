This weekend I had the opportunity to attend another session of [WeekendTesting](http://www.weekendtesting.com).

This session was a little different than the last session I attended on [Mobile Testing](http://brendanconnoly.net/weekend-testing-experience-report) since we weren't going to focus on testing software but instead on [Bug Rehab](http://weekendtesting.com/?p=4191). 

### Bug Report Rehab
The goal of the session was to look at existing bug reports and see how we might improve them and at the same take those lessons and implement them in future bug reports.

It's easy to think of testing as the art of finding bugs but that's often just the beginning. Sometimes finding an issue is the easy part, convincing people that the issue is real and warrants attention and resolution can be much more difficult. A poorly communicated issue is easier to dismiss, it can also damage your credibility with the managers and developers that will read the report.

### What is a Bug Report 
We started by discussing what a bug report actually is. Just the word bug can cause some developers to get defensive, and [Carol Brands](https://twitter.com/CSBrands) suggested thinking of bug reports as change requests. I think that puts both testers and developers in a better mind space. We aren't placing blame, we are suggesting an alternative set of behaviors. 

We dove deeper into defining a bug report. Generally it was seen as any form of communication that relays information about a bug. I agree, bugs can be reported just like any form of news can travel. However, I believe there is a difference between a bug report and a "bug report". In the first case a report just happens to describe a bug. This could be a TV news report talking about issues customers are seeing in the latest iPhone release. A "bug report" is a more specific context, this is the difference between a customer talking about what they are seeing and a tester stepping through that same scenario and documenting its importance. In the same vein, bugs can be reported verbally. It's a valid report of an issue. My concern is what can occur if bugs start to consistently or primarily be reported verbally. Bug reports are used for more than logging the issue, they are used to track progress. I see the first definition as bug announcing.
 
 As you might expect if you've logged or viewed a bug report the standard and often required, expected behavior, actual behavior and reproduction steps came up. There were also mentions of including the environment specifics (OS, Platform, etc.) to help clarify the issue. These are all generally good things and help set a factual foundation for the issue, but there's more to good bug reports... 
 
### Selling It 
Well at least supporting your bug reports. Bugs are subjective, some are so obvious that they can't be ignored but that's not always the case. I suggested that testers need to advocate for resolution in their bug reports. I felt pretty proud of myself for this little tidbit of wisdom, but then [Michael Bolton](http://www.developsense.com) responds with testers need to advocate for an issues significance rather than just its resolution and that is just spot on. I meant something similar but that just wraps up the idea with a pretty little bow. It you prove and issue is significant, its much more likely to be addressed. 
 
This really highlights some of the value of weekend testing, it's experiential. I could have read that line from Michael on his blog but I doubt it would resonate the same as it did in real-time conversation. There's a ton of experience in that skype session, and you get full access to all of it.
 
Back to the bugs, [Michael Larsen](http://mkltesthead.com) also pointed out that all the factual data about your bug only matters if isn't rejected. This just hammers home the importance of showing the significance of the issue is just as important as the detailed reproduction steps and other fact. 
  
### Concrete Examples
After clarifying our ideas about what a bug report is we actually looked at some real world bug reports from the Mozilla Firefox bug database. For each bug report we discussed its overall quality and how it might be improved. It's a good exercise, and it highlights an interesting aspect of bug reports that I didn't immediately realize. It's not just testers that log bugs. In the case of the Firefox, anyone can log a bug. However, even on less public systems bugs may come from customer service teams, sales or product teams so you can see how widely the quality of bugs entered can vary. 

There had been talk of templatized bug reports throughout the session, but looking at examples of bug reports brought it to center stage. We questioned the value of always having things like expected and actual results or even test steps. Requiring this type of information can be constraining, can you not log a bug if you do not have complete reproduction steps? There are plenty of issues where the issue isn't clear cut enough to identify the exact steps. Then for explicit callouts for actual vs expected results, aren't there cases where it's possible or even preferable to only state the problem? 

Some interesting conversation came up about how tooling can affect the contents of the bug reports. A tester may not have full control of all that is included in the report. Bug tracking systems might include or require certain fields be filled out. The format may have also already been decided by team management. I felt that as long as tester is free to deviate from the format, then the format just acts as a set of guidelines. When you just start testing something it may be a good idea to be sure to try and include this data. As you learn you maybe able express the issue more clearly and at that point you might be drop some of the prescriptive format. 

### Wrapping things up
It is the second session I've attended, both have been part of the Americas group since the times fit nicely into my schedule but there are sessions for other regions/time zones. I can't recommend highly enough that you at least try a session. It's only 2 hours, but in that time you get to meet and share with testers from all over the world. It's a supportive community and discussing your craft with other professionals can really hone your skills or at least give you things to think about. 