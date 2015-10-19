One of the most important parts of an automated test is a clear intent. Test frameworks like xUnit, MSTest, Nunit, etc. offer some powerful tools for structuring and executing tests. However, their syntax and conventions can be constraining for people writing the tests and more challenging for people reading the tests. 

[Fluent Assertions](http://www.fluentassertions.com/) is an open source custom assertion library that has almost 1 million nuget downloads. It works with most of the common .Net unit test frameworks like MSTest, Nunit and xUnit.Lets take a deeper look at how it might help improve your tests. 

### Reduced Friction
Knowledge work requires a good amount of concentration and focus. If I can get into the [flow](https://en.wikipedia.org/wiki/Flow_(psychology) my productivity will skyrocket. If I am battling the test environments or test framework it makes finding that flow extremely difficult. 

Traditional assertions that are built into the test frameworks require a context shift from the system under tests domain to the tools domain that can interrupt that flow. It might not seem like a major issue at first especially for straightforward tests and validations. As your tests grow and you start to dive deeper into what you need from the test framework the more friction you might find. This is especially true if your tests don't fit nicely into what your framework offer, or you aren't familiar with the frameworks particulars. 

Fluent Assertion's solves this issue by using (an extensive collection of) extension methods designed to be explored through intellisense. Except for a few special cases, all of you choices are accessed through the "Should" method. This means theres little to no context shift, for example:

```cs
 Assert.AreEqual(expectedName, testor.Name);
 
 // becomes
 
 testor.Name.Should().Be(expectedName);
```

### Failure Messages
When a test fails ideally the failure message makes the reason for the failure very clear. The last thing you want to have to do is rerun the test just to get into a debug session to figure out what went wrong. Test frameworks like Nunit can do a decent job, but they aren't exactly user friendly especially when not viewed by the test author. 

Fluent Assertions has a more reader friendly representation of the failure. It also offers an optional "because" parameter that can be used to add additonal details.  
```cs
        [Test]
        public void stringEndWith_Test()
        {
            var testor = new TestorTheBarbarian();
            var expectedText = "Barbarian";
            //to fail test
            //expectedText = "Gentle";

            //Nunit Classic Model
            StringAssert.EndsWith(expectedText, testor.Name);
            //--> Expected: String ending with "Gentle" But was: "Testor The Mighty Barbarian"

            //NUnit Constraint model
            Assert.That(testor.Name, Is.StringEnding(expectedText));
            //--> Expected: String ending with "Gentle" But was: "Testor The Mighty Barbarian"

            //FluentAssertions syntax
            testor.Name.Should().EndWith(expectedText);
            //--> Result Message:	Expected string "Testor The Mighty Barbarian" to end with "Gentle".

            //with optional description
            testor.Name.Should().EndWith(expectedText, because: "appearances can be deceiving");
            //--> Result Message:	Expected string "Testor The Mighty Barbarian" to end with "Gentle" because appearances can be deceiving.
        }
```
To be clear, Nunit also has an optional message parameter on its assertion methods. I'm not a huge fan of using it with Nunit or  Fluent Assertions for that matter. It can start off helpful but over time, like code comments test authors may not update it or it may get copy and pasted into other tests and not changed. It adds some maintenance overhead and may be a bit of a test/code smell that may be better addressed through a different approach inside the test.  However, if I was going to use it, I much prefer the "because" syntax. It not only improves the failure message, it has a clear intent inside the test. 

### Dates and TimeSpans
Dealing with dates and times inside of tests can be challenging and a little hard on the eyes. This may not be an issue if you are already using a library like [Noda Time](http://nodatime.org/) but if you are not Fluent Assertions offers some really nice extensions for handling dates. 
 
 ``` cs
 DateTime dt = new DateTime(2015, 3, 1);
   //becomes
 DateTime dt = 1.March(2015)
 ```

Notice how much easier to read the second example is. There's no confusing the order of parameters in the constructor and no need to use the new keyword.

It get works just as well with a date and time.

```cs
 DateTime dt = new DateTime(2015, 3, 1,22,30,0);
   //becomes
 DateTime dt = 1.March(2015).At(22, 30);
```
That first instantiation is just ugly. The Fluent Assertions example is very clear and hard to misunderstand. 

Its just as nice for TimeSpans.

```cs 
TimeSpan ts = new TimeSpan(0, 0, 1);
   //becomes
TimeSpan ts = 1.Seconds();
``` 
Thats just plain handy, can you really tell how long that first example represents at first glance? 

### Object Comparison
A common best practice for writing tests is to only have a single assertion in a test. Outside of test design issues, multiple assertions in a test often leads to only partial test completion since the first failure will stop the test. If you are checking the value of multiple properties of an object, when one fails you won't know if any subsequent assertions passed or failed.

To try to work around this I've seen some relatively nasty hacks. Things like concatenating all the values into a single string and asserting on that value or a series of try catch blocks that maintain the test state. It makes tests harder to read, investigate and even worse can hide real failures.

Fluent Assertions enables object graph comparison in a single assertion. Fluent Assertions will walk each object and compare it to another and report any discrepencies. 
```cs
 [Test]
        public void objectGraph_EquivalentTo_test()
        {
            var player1 = new Player("Joe Tester");
            var p1_teamMember1 = new TestorTheBarbarian() { Health = 99 };
            var p1_teamMember2 = new MasterCodo() { Health = 0 };

            player1.Party.Add(p1_teamMember1);
            player1.Party.Add(p1_teamMember2);

            var player2 = new Player("Joe Tester");
            var p2_teamMember1 = new TestorTheBarbarian() { Health = 99 };
            var p2_teamMember2 = new MasterCodo() { Health = 100 };
              p2_teamMember1.AddAttack("Bug Be Gone");
              
            player2.Party.Add(p2_teamMember1);
            player2.Party.Add(p2_teamMember2);

            //FluentAssertions syntax
            player1.ShouldBeEquivalentTo(player2);
            // --> Result Message:	
            //            Expected member Party[0].Attacks to be a collection with 2 item(s), but found 1.
            //            Expected member Party[1].Health to be 100, but found 0.
            //            With configuration:
            //             - Use declared types and members
            //             - Compare enums by value
            //             - Match member by name(or throw)
            //             - Be strict about the order of items in byte arrays
        }
``` 

Sounds great right, but what if I have properties that I want to ignore? What if one object does not have all the properties of the other? For those and a variety of other situations ShouldBeEquivalent has an overload that takes an options parameter that allows you set the rules for comparison. This is a very powerful tool, especially in cases when testing at integration or higher levels. You can make an api call and verify the entire contents of the response in a single assertion that when failures occur provides a detailed message.

### There's More
I've tried to highlight some of what makes Fluent Assertions special, but it offers a wide variety of assertion types and options. 

To see more examples check out the Fluent Assertions test project in my [AssertionExamples](https://github.com/brendanconnolly/AssertionExamples) project on GitHub. 

Or check out Fluent Assertions [wiki](https://github.com/dennisdoomen/fluentassertions/wiki) on the projects GitHub site.  

Happy Testing!