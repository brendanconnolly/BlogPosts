Testing: Why this Tester Learned to Code
========================================

Where I first started testing, it was essentially all manual testers. Much of the work fell into 
what James Bach and Michael Bolton would refer to as checks rather than tests.<cite>[1]</cite> The team was the quality guardian.
The last line of defense before software could be released onto the world. The relationship between QA and Development
was rocky at best. What automated checking existed was brittle, out of date, and difficult to maintain. Tools were
limited and getting developer time to build anything for QA was a fools errand. There was constant pressure to release faster.

It wasn't all bad, in fact there was a lot of good. The main problem was theever increasing burden of manual checking that grew 
with every feature that was added. Often these checks were repitive, tedious and hard. It took time away from actual testing.

 In my heart I am a *lazy* tester in the Larry Wall sense of the word.<cite>[2]</cite> If I was confronted by a relatively mindless
 (read as: repitive, tedious and hard) task I was looking for some way to make the computer do the work for me or at least do the heavy lifting. 
 I did what I could with batch files and scripts but some cases just needed different tools. I knew I needed code.
 
  This was also around the time that our company started discovering Agile Development, at least talking about it.
  We had been pretty much waterfall, and had our share of long release cycles and delivering features that worked but weren't exactly what the customer 
  wanted. As I began to read about it, I saw developers testing via unit tests and thought "Wow, I might get builds that actually work?". In contrast to the fairly regular
 cycle of install the build, attempt to test the feature, immediately fail, then try to nicely convince the developer that something is very wrong and 
 wait for the next build, Agile sounded like a breath of fresh air. The more I read the more I saw no real mention of the test team. It seemed like the industry was 
 widely adopting a process that was actively thinking we don't need QA, we have unit tests and rapid feedback from stakeholders. I was concerned about what that meant
 for software and I was scared for what that meant for my career. I knew I needed to level up my skills.
 
 I had always wanted to program. I grew up on 80's 8bit video games and dreaming of writing my own. Some of my early exposure was looking at C and 
 being a little scared off. [metroid code] So I was uncertain of my success but I knew I had to try. I wasn't looking to jump from QA to development,
 I was looking to use development skills to improve my testing and remain an asset to the team.
 
 I didn't have anyone to go to for help, but I was on a mission. I'd scour the internet for tutorials and examples that I could use to build my skills. 
 (Unfortuately it was before Pluralsight, if you haven't used heard of or taken the training courses there I highly recommend it.)  It wasn't always easy,
  in fact many times it was very hard but there is a primal satisfaction is watching something you wrote in action. 
  
 In the beginning it was just very small utilities that looking back offered little value other than enabling the learning. But once I could have code execute SQL
 queries, read files and registry settings, I was Rockin and Rollin. I felt like a caveman hitting rocks together and then seeing a spark. 
 
 As I learned more I could do more, suddenly I was extensible.
 
 I no longer needed to manually check these things. My mind was more free to focus on the testing I was doing and not the checking. 
 Even the quality of the repititive checking went up since human error was removed. No more worrying if the xml had a typo, the utility I wrote would parse it.
 Long detailed checklists of verifications that took hours to do could be done in minutes with the results written to file for review by the tester.
 
 Through this process, other interesting things happened. My conversations and interactions with our developers changed. I has good relationships with the developers 
 I was working with, but there  as they ssaw that I was reading the code they were checking in I found they were more eager to work with me proactively. They also
 seemed to become more aware that other people were looking at their code so they were more self conscious of how it looked. It's like working on a project for your home
 if its somewhere few people (if any) will see then you might not be so concerned with how it looks, or how polished it is. However, if you know visitors will be looking
 you want to make the finished product look nice.  [better example]
 
 The more I looked at their code, asked questions about decisions they made, and began to spot potential bugs earlier the more they engaged. It was the basis of mutual respect. A little respect goes a long way, and it certainly makes people more open to listening to your 
 prespective. I wasn't just a tester looking to break their work, to critique their efforts or create new requirements for a feature. I was speaking their language, and we were collaborating on the
 quality of the product. 
 
Learning to code also improved my testing. There was often a pressure on the team to test everything "just in case".  It felt a little
like a mechanic diagnosing your car troubles without popping the hood. Sure they might find the issue that way but they could go way off track and spend a great deal more
time than needed. Just like with the mechanic example, a tester shouldn't blindly trust the developers, but you should be able to speak definitively about why you 
are performing the tests you have chosen to do, and target your testing efforts accordingly. Looking at the code (or the diff's between old version and new) is just another
tool to help reason and make decisions about what you are testing. The context of you testing matters,looking at the code can help you identify that context and question its
validity. The code also helps you see what the unit tests cover and help you judge if any of you boundary or other input checks are covered.   
 
 
 


[1]: Link to Testing vs checking  
[2]: http://www.threevirtues.com