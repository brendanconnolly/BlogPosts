![light bot](http://www.brendanconnolly.net/wp-content/uploads/2016/04/lightbot.jpg)

This Weekend Testing session was a bug hunt on [LightBot](https://lightbot.com/hocflash.html), which is a game designed to help people learn programming concepts. 

### The Balancing Act 
One of the first things I realized is testing a game is hard! I put my testing hat on and started looking at the game. I had to try the game out right, interact with it in order to test it. Before I knew it I was just straight up playing the game, I was caught up in solving the puzzles. It's not like I wasn't analyzing the gameplay and usability, but I can't say that the focus was really testing. If I had found a bug it would have been more by chance than by design. 

It really made me wonder what approach actual game testers used. It felt like I needed to get the play out of me first, otherwise I would be constantly drifting in focus between gaming and testing. In a sense this is what typically happens with non-game testing, you *play* with the system to get and understanding of what it does and how it does it. I just got a sense of guilt with it being a game. 

It hammered home the importance of having a clear and focused charter for test sessions.  With a clear mission it's easier to avoid the losing focus. The play let me learn so I could perform more detailed analysis of the behavior and potential issues. 


### The Game

I got pretty caught up in the testing vs gaming struggle and that stunted my progress through the game. As someone that can already program, I was struggling to see how the levels in the basic grouping applied to programming concepts. At a very high level, you have a set of a few commands that you queue up then have a robot execute. Yes its programming something, but I don't know if that's what people struggle with when approaching code. 

Then I got to section 2, which is all about procedures. The game lets you create a reusable function or two that you can use to complete the level. It was coming together, and it made the game much more interesting. That's a nice positive reinforcement for an important programming concept. 

As I was playing I accidentally had the procedure call itself. I didn't realize what I had done until I had the game execute my commands.  Holy cr*p theres recursion...  
<iframe width="560" height="315" src="https://www.youtube.com/embed/t4MSwiqfLaY" frameborder="0" allowfullscreen></iframe>

But my excitement was quickly dampened as I got to section 3 and saw recursion was being used to teach loops. What was more concerning was gamers were creating infinitely recursive situations because there was no programmed exit condition. The level would complete because all the switches were flipped but that is external to the programmed commands. That's like designing a TV without a on/off switch because people can just pull the plug when they are done watching.  

Recursion is powerful and can be pretty cool, but its certainly not something most programmers use everyday and nor is it the most common form of a loop. I can see why the game implemented it this way, but I think it misses the mark. 

### Visual Cues

While playing I ran across a couple levels where the perspective used made it difficult to identify the appropriate action to use.  
For example on level 2-4 (pictured below), as the top row makes a right turn towards the middle of the scrren the angle of the layout makes it difficult whether the robot needs to jump down or if the surface is flat. 
![level 2-4 layout](http://www.brendanconnolly.net/wp-content/uploads/2016/04/ScreenShot_lightbot.png)

I got it wrong the first time and had to blink a few times before I could get the perspective to shift mentally. It's not a showstopper. since the game does not score based on the number of attempts. It was confusing and frustrating, the UI shouldn't get in the way of the game. 

That layout issue made me consider more about the overall visuals of the game. I was curious if the similar tonality of the level blocks might be and issue for people with color blindness. To test it out I used [Spectrum](https://chrome.google.com/webstore/detail/color-vision/ofclemegkcmilinpcimpjkfhjfgmhieb) which is a Chrome extension that lets you test a webpage with the different types of color vision deficiency. Turns out there wasn't any major issue with the color scheme, but I did get a chance to learn more about usability. 

### Final Thoughts

This session was different than the others I have attended. At first I wasn't sure what take aways I would have. What I found though was I was just outside of my comfort zone testing the game. The session gave me a chance to work through that and gain some insight and clarity into charters and dividing work and attention. 

Those insights are what make Weekend Testing so valuable. I learn every time I go. I take away insight, I meet fellow testers from all over the world and I get energized about testing.  So pick a session and just show up, practice your craft and you might just enjoy yourself... 

Feel free to check out my other [experience reports](http://www.brendanconnolly.net/category/weekend-testing/) if you need more convincing.






