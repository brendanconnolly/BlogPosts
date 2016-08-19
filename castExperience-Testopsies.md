![muppet autopsy](http://www.brendanconnolly.net/wp-content/uploads/2016/08/muppetautopsy.gif)

Testing isn't dead but it doesn't mean we can't dig into it to better understand it.

I attended the [Testopsies - Dissecting Your Testing](https://www.associationforsoftwaretesting.org/conference/cast-2016/cast-2016-tutorials-2/) tutorial at CAST 2016. Lets open up the experience and take a deeper look.

### What is Testing
We broke up into groups to define / draw out what exactly we though testing looked like. Our group started out by creating a list of our thoughts. Later we found out we might be sharing/presenting our results to the other groups so I tried to capture our list into a [sketchnote](http://royanlee.com/?p=4414) style mind map. 

I've never actually done any sketchnoting before but since I was already in a new place in a room full of strangers why not try something else new... 

![What is Testing SketchNote Mindmap](http://www.brendanconnolly.net/wp-content/uploads/2016/08/cast2016TestopsyTestingMap.jpeg)
It was done in a bit of a rush so I'm not sure I got all our thoughts in (I probably didn't). I also ran out of sketch ideas after a bit, looking at it now I wish I turned the *exposer* box into a towel and had a person behind it. In any case I liked sketchnoting and plan to dig into it a little more.

### What is a Problem?
Testing is about identifying things, risks, bugs or more generally problems. Let's not get caught up in pedantic definitions, the value here isn't in the result it's the process. Can you verbally express without resorting to vague platitudes, truisms what is a pillar of your role as a tester? 

This is important because it directly effects the strength of another testing pillar, reporting problems. [Translating](http://www.brendanconnolly.net/testers-translators/) the tacit into explicit is a direct reflection on the value of a tester
We can all recognize what a problem feels like but without being able to express it we accept the risk of shallow agreement which often leads to mismatched expectations. A tester needs a clear understanding of what a problem is in their context in order to effectively relay their findings to stakeholders. 

### Coding System

Next we dug a little deeper into our testing process to come up with a list of different activities and aspects of testing with the goal of quantifying them into recognizable categories. 

It's a surprisingly interesting exercise, to paraphrase Michael Bolton:

>Do something (perhaps naively) with intention to recognize patterns
become aware of them name them and make explicit.

The group I was in chose to model our coding system after the scientific method. I'm a big fan or wrapping testing processes in terms and methods that are already accepted or in practice by non-testing groups. 

![scientific method](http://www.brendanconnolly.net/wp-content/uploads/2016/08/scientificMethod.jpg)

Once you understand and recognize what you are actually doing when you are testing it offers you perspective. 

For each category of action you can now examine their value and impact. 
- Do we need to do it? 
- Should we avoid it? 
- Do we like it?

Then based on the answers to your questions you close the loop with intentionality.

### Testing and Observation

Armed with the coding system we broke up into pairs with one person as tester and the other person acting as observer. To further aide in observation Michael suggested recording the testing with a screen recorder. 

![Group Working with Michael Bolton](http://www.brendanconnolly.net/wp-content/uploads/2016/08/cast2016TestopsyGroup.jpeg)

I was surprised to find that recording testing sessions was not an entirely uncommon practice amongst the group. Observation and recording leads to the question of narration / transcription. As you might expect, just viewing a testers actions does not capture with fidelity all that is going on. 

You can see the video of one of the testing sessions in [Neil Studd's blog post](http://neilstudd.ghost.io/2016/08/09/cast-2016-monday-lean-coffee-tutorials/) on the tutorial. He also describes the CHRISTMAS heuristic in this session that he created during the tutorial it's definately worth the read.

#### Verbalization

Not surprisingly, the people doing the testing began to describe what they were doing and thinking to the observers. Speaking as an observer, I'm pretty sure most testing would look very random and possibly incoherent without something explaining the testers intent along the way. This made me wonder if this is why non-testers may struggle to understand its complexity and value since intent is not always clear from observation.

I found the benefit of talking out my testing to another person helped me stay focused. It also helped my own personal test note taking by giving context for what information should be relayed. Too much explanation breaks the testing flow, but when the mix is right the slight interruptions gave me time to process what I was seeing and minimize the drift from charter. Michael Bolton referred to this as **The Pause**, it gave me just enough time to acknowledge something, a bug, a potential new charter and then comfortably move forward while staying on mission.

#### Coverage

 > Coverage is how much you know about something and how well we know it, quality is what you know about it

 Coverage needs to be relayed as a composite measure that relates to the different dimensions of the product and the environment in which it is being tested. To be able to have a meaningful discussion on coverage, what coverage generally constitutes needs to be agreed upon before we can accurately discuss or summarize it. 

#### Tempo

As we all took turns testing it was pretty common for the person testing to just jump into testing. The result is a hybrid bug hunt and ad-hoc learning session. This isn't a slight at those testers, it's my first inclination to poke at the app, see how it responds, learning as I go. What Michael helped clarify here was that this approach leads to generally superficial testing which in turn will most likely turn up superficial bugs. 

 > Every bug takes away from our coverage

It's validating to find bugs, but not all bugs are equal. Every bug you log represents time spent finding, documenting, discussing, prioritizing, fixing and retesting. This is all time spent not finding new problems.  

I opted to be the observer first in my pairing, so when my turn came up to be the tester my first action was to set a charter for my time.  Walking up to testing something new I feel this need to try and cover everything. It's overwhelming just trying to find a starting place. It's surprising how just expressing your intent immediately filters out the surrounding noise. It sets expectations for both the person performing the testing and those observing. 

We also discussed using structuring testing so that initially you are testing to learn, then shifting your testing to find bugs. This inverts the typical workflow. You might uncover problems as you are learning but that doesn't mean you need to log them all in real-time. 

### Introspection, Intent & Self Awareness

How often do people say they wonder where the day went, or wonder why they can't get anything done? At some level these expressions just indicate some level of self-awareness and lack of intent. Without an explicit mission, implicit missions take over.

At its core the tutorial using introspection of actions to gain self-awareness. Then armed with this awareness adjust and refine your processes. I'll admit while I enjoyed the tutorial some of my first impressions were that some content felt very intuitive, like a more formal presentation of things I intrinsically understood. 

I wasn't really sure how or if I was going to write about it. Something interesting happened when I did sit down and start writing, I started going over my notes, reflecting on what happened. Thinking about the day step by step, activity by activity, categorizing, measuring, analyzing  I realized I was doing exactly what Michael described and I was finding new things that I hadn't picked up on the initially. 

What is blowing my mind a bit as I write this is how the experience I'm describing maps directly to the superficial testing leads to superficial bugs scenario described above. I was in the tutorial eagerly trying to soak everything in waiting for insight to be dropped into my lap. Then the result was average, I caught some things (probably the more obvious) and missed some of the nuanced and more complex things. 

Given this result I'd be even more curious to rewatch the session and work through the feedback cycle again and see what else I can glean.




