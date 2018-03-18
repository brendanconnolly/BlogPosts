![Test Driven Testing](http://www.brendanconnolly.net/wp-content/uploads/2018/03/driven.jpg)

As we take inspiration from TDD practices, an important thing to recognize is that TDD is a [discipline not a solution](http://blog.cleancoder.com/uncle-bob/2017/03/03/TDD-Harms-Architecture.html).

The first two laws of test driven testing are intended to [increase the testers awareness of their actions](), and [reduce the scope of testing](). We need to step beyond thinking just about what you are testing and consider how you are testing.  

Turning to the third of the [three simple laws of TDD](http://programmer.97things.oreilly.com/wiki/index.php/The_Three_Laws_of_Test-Driven_Development), you will see that it requires the developer to implement the same constraints previously applied in their test code onto their production code. 

### 3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

This treats testing and development as two sides of the same coin as opposed to wholly separate processes.

When you really think about it, it sounds odd to think of it any other way. If unit testing is just going to be attended to once code is completed, it reflects a hierarchy of value. A developer may start with intentions to write tests after the complete a single class or function but it's easy to get caught up implementing something so maybe they push testing a little further down the road. Now when they do start writing tests, they may find some parts harder to test than expected. Perhaps they find issues and need to make changes, if they had written tests first they could quickly see if these changes had unintended side effects. 

TDD is about building up discipline to let the process drive your actions.  Tests are written first because that is when willpower is the strongest. The cycle has to feed itself though, so in turn you have to maintain discipline and carry the process forward into the production code. You can't test small if you don't develop small, anything else is really a test of self-restraint. 

## Holistic Testing

When you sit down and want to start testing, what happens the moment you think you might have a bug on your hands? Do you dig in? Iterate over the same scenario trying to nail down the reproduction steps? 

Sometimes the bugs testers find feel like [merit badges](http://meritbadge.org/wiki/index.php/Main_Page) they get to wear around. Medals of honor that represent the value that a tester brought to the team. 

In reality bugs are a distraction, wouldn't you rather be objectively evaluating software on its merits rather than its flaws? 

Outside of the time sink for other team members prioritizing and resolving bugs, the impact on a tester is severe. Testers cycle through the discovery process, then begin defining the bug through reproduction steps. Next might be refining the reproduction steps, the investigation of related areas to get a sense of scope and impact. Then we transition to the reporting process, logging and communicating possibly even defending the bug.

### Functionally Focused
It's not just bugs though, there many dimensions to testing. That feature that has different roles or personas associated with it. It might seem faster to address all the functionality at once, switching accounts as you step through. Maybe you start peek at some other minor changes while you are testing a moderately related change. 

It might seem like no big deal, but it's a distraction. 

## Third Law of Test Driven Testing 
### 3. No Activities outside the objective

Distractions, even small ones add up and add friction to work. Friction slows throughput.That bug you thought you saw, it'll still be there once you wrap up your current objective. Tackle those related tasks in series rather than attempting to do it in parallel. Speed doesn't have to be measured in how fast we do multiple things, let your speed via throughput.

If we are going to take the time to define intent before we start testing, then attempt to constrain our testing to explicitly stay within the boundaries of that intent, it requires diligence. In order to maintain that level of discipline, it stands to reason that attempting to do other tasks within that cycle will only serve as a distraction. 

## A Place for Everything and Everything in its Place

It seems like everything in testing revolves around some priority or another. What areas to test? What tests to perform? How serious is this bug? How many users may be effected?

We want to maintain the same discipline the TDD teaches developers while we test. We can't test small, if we don't work small. A way to ensure scope of work stays small is to not simply cede control to intuitive actions. 

When we break focus to endeavor to pursue something else we implicitly grant it a higher priority than our original pursuit. Context matters, some things warrant an immediate escalation in priority and that is fine. What we want is to be cognizant of this shift so as to make an explicit decision.



