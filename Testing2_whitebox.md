Pair and Peek

Once I started to code, I was always peeking at other peoples work especially the code I was going to tbe testing. I was self conscious about how my own code looked, so I looked at other peoples to get a better understanding. Soon I got in the habit of reviewing every bug fix and feature that I was assigned to test. 

First I'd read the user story or bug report. Then I would begin modeling in my head the behavior I expected to see, the personas and scenarios I would need for testing. With that model in mind, I could clarify things with the owner if neccessary then I would jump into looking at the changes that were checked in. 

It wasn't always easy, the project at the time used three different languages (c++, c# and vb6) and spanned two source control systems. The test team worked closely with development but this wasn't standard practice.

###Dialog and Context
When you can frame your conversation to the context of your audience you can begin to have some powerful interactions. You can sit with the developer as she is writing the code and share ideas, or discuss corner cases. You can have a technical or domain based conversation. If you can't pair with a developer while the code is written, starting a conversation with * I saw your latest check-in and have a couple questions...* can be agood place to start. Things are still fresh in the developers mind and you've primed the situation by clearly indicating you have taken the time to look their work already. 

This isn't carte-blanche to start an unrequested code review. There's alot that goes into writing production code that new eyes often don't immediately grasp. It might be legacy code that doesn't live up to current standards and conventions. The implemementation might be based on some complex state caused by other related code or a third-party api. Just as you wouldn't want someone telling you how you should test and how what you are doing is wrong. The point is not to be a style cop, but to focus on content Look through the lens of testability, be that for regular or automated testing purposes.

It ended up being a very cooperative relationship. Through talking with the developer early in the process they came to know the types of tests I would run through first and what tools I would use. In some cases they even started using the tools and performing of the tests pre-checkin. Test cycles got shorter and quality improved.

###Another tool in the toolbox
I see the code as one more oracle for a tester. It shouldn't be the only one or you can easily fall into the trap of just testing what the feature does and not what the feature is supposed to do. It also helps to start getting familiar with the source control system your team is using. I've worked on test teams where the source control system is clearly marker *Here be dragons*. Each check in usually has a corresponding description or notes that might be interesting or provide insight. You can also view a diff between the current and previous versions. So even if you aren't fully literate in the code and can't understand everything you are seeing you can see what things were changed. If your team is following decent practices with descriptive names and comments or readable code then theres a good chance you can still follow the logic and flow of the code. I can see how it might be intimidating at first but its a powerful tool, I even use Git on my blog to track and backup my posts.

Testing is hard, and as testers we need to use every resource we can. Not every test team has a good relationship with the dev team. The code is a window into how the developer is thinking about the feature, and that kind of resource is not something to ignore.    

###Growing Technically
Part and parcel to working in the software industry is being able to cope with the pace of change. Testers aren't immune this and we need to be continually learning. As the industry continues to *shift left* there is a growing expectation that all roles will be more technical. As testers we shouldn't hide from this, we should embrace it and run with it. Becoming comfortable with code and development practices will only deepen your skillset and increase your marketability. 
