 Level Up Tests using a custom Assertion Library: Shouldly
========================

When writing automated tests there is always some form of validation, typically called assertions. Typically the tool or framework you are using usually provides some form this functionality out of the box. For example whenever you create a test project in Visual Studio by default you are going to be using MSTest. 

I've used MSTest and xUnit but mostly Nunit. I found MSTest harder to use, and more limited in syntax, xUnit had limited documentation, but Nunit well I love NUnit[1]. It's very flexible, well documented, has good options for data driven tests, plus a very broad and powerful set of assertions.

After that love fest over Nunit, why wouldn't you just use that? Why go beyond its greatness?

###Readability
Nunit has two models for its assertion syntax. The original "classic" style, which follows the convention 
```cs
Assert.AreEqual(expected, actual, optional_message);
```

This seems fine at first, but it can get clunky. It also requires you to always remember the correct order of the parameters. Its not a big deal but many people invert the order and it can end up with some confusing failure message. 

To address some of the short comings Nunit introduced the "constraint" model.
```cs
Assert.That(actual, Is.EqualTo(expected), optional_message);
```
 This style is much more readable but it also switches the order of the parameters, so it's best to choose one style.
 
 Shouldly steps in and removes the context shift between your domain and the unit test framework. Validations  start with "Should" and in most cases are accessed as extension methods which elliminates any expected vs. actual confusion.
 ```cs
         [Test]
        public void stringEndWith_Test()
        {
            var testor = new TestorTheBarbarian();
            var expectedText = "Barbarian";

            //Nunit Classic Model
            StringAssert.EndsWith(expectedText, testor.Name);

            //shouldly syntax
            testor.Name.ShouldEndWith(expectedText);
        }
 ```
 Choose the property you are testing and start typing .Should and Shouldly springs to life. 

### Failure Messages
The next major boost Should adds to your testing is helpful failure messages. Both nunit assertion models failure message are the same and can leave you a little short of information if you are just looking at the test output trying to resolve failing tests from your nightly build.

 ```cs
        [Test]
        public void stringNotNullOrEmpty_Test()
        {
            var testor = new TestorTheBarbarian();
            testor.EquipWeapon("Fists of Fury");

            //Nunit Classic Model
            Assert.IsNotNullOrEmpty(testor.ActiveWeapon);
            // --> Expected: not null or empty string   But was: null

            //shouldly syntax
            testor.ActiveWeapon.ShouldNotBeNullOrEmpty();
            // --> testor.ActiveWeapon should not be null or empty
        }
 ``` 
 Shouldly includes the name of the actual input being tested. In the case above the failure message clearly shows that the ActiveWeapon property was the problem. Nunits message only indicates we expected not null but it wasn't. 
 
 This may not be a major issue if your tests are well names and fine grained with a single assert. If your tests have multiple asserts then this is very handy and saves having to include a custom fail message to tell which assertion is the problem.

### Shouldly Special Features
Shouldly includes some enhanced assertion methods that just don't exist in the Nunit standards. 
Here are a few examples, you can also check out my [AssertionExamples](https://github.com/brendanconnolly/AssertionExamples) on GitHub, or the Shouldly documentation[2] for more.

####Collections
Shouldly allows a predicate to be applied to all members in an IEnumerable.
```cs
        [Test]
        public void listAll_test()
        {
            var player1 = new Player("Joe Tester");
            var teamMember1 = new TestorTheBarbarian();
            var teamMember2 = new MasterCodo();

            player1.Party.Add(teamMember1);
            player1.Party.Add(teamMember2);
            //to fail test
            //teamMember2.Health = 0;

            //Nunit does not have an equivalent either separate asserts or a boolean which 
            // will loose detail and have a generic message 
            Assert.That(player1.Party.All(p => p.Health > 0), Is.True);
            
            //shouldly syntax
            player1.Party.ShouldAllBe(p=>p.Health >0);
            //-->player1.Party should satisfy the condition (p.Health>0) but
            // [TestorTheBarbarianDemo.MasterCodo] but do not
        }
```

####Multiple Assertions 
Should also provides a mechanism for having multiple assertions in a single test that will all be rexecuted regardless of failures.
```cs
        [Test]
        public void multipleAsserts_Test()
        {
            var testor = new TestorTheBarbarian();

            //change either or both value(s) below to fail test
            var expectedText = "testor";
            var expectedHealth = 100;

            //Nunit does not support this in 2.X but similar functionality is in discussion for v3 (Assert.All)

            //shouldly syntax
            testor.ShouldSatisfyAllConditions(
                () => testor.Name.ShouldContain(expectedText),
                () => testor.Health.ShouldBe(expectedHealth)
                );
            //--> testor should satisfy all the conditions specified, but does not.
            //       The following errors were found...
            //-------------- - Error 1-------------- -
            //  testor.Name should contain "bugra" but does not
            //-------------- - Error 2-------------- -
            //  testor.Health should be 10 but was 100
            //-------------------------------------- -
        }
```

####Timed Tests
You can also assert that methods complete in an expected time.

```cs
[Test]
        public void timedResult_Test()
        {
            var testor = new TestorTheBarbarian();
            //set sleep to >1000 to fail test
            var sleepyTime = 500;

            //nunit closest option MaxTime attribute on the test method. 

            Should.CompleteIn(
                () => testor.Rest(sleepyTime), TimeSpan.FromSeconds(1)
                );
            //--> Task should complete in 00:00:01 but did not

        }
```

### Framework Lock In
Most frameworks consist of a set of attributes to mark your tests and classes and also special syntax for assertions. It may not happen frequently but changing frameworks (say MSTest to Nunit) is simple a simple find and replace for the test decorators. The assertions however are more complicated. Shouldly provides an abstraction on top of the frameworks syntax.  

###Easier Testing
Adding Shouldly just makes the test process easier. Easier to investigate failures, and easier to write with simple extension methods. It also methods to make some complex test scenarios easier to write and read. 

To see more examples check out my [AssertionExamples](https://github.com/brendanconnolly/AssertionExamples) project on GitHub. 


[1]:http://www.nunit.com
[2]:http://docs.shouldly-lib.net/
