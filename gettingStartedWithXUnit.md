![xUnit title](http://www.brendanconnolly.net/wp-content/uploads/2016/02/xunit.jpg)

I've been an NUnit user and fan for years now, but it has limited support for dotNet core and Microsoft has adopted xUnit for many of its current open source projects. Between that and my current team using xUnit it's a good time to start getting familiar with the framework. Even if you aren't writing unit tests, many automated integration or even end to end tests still use unit test frameworks as a harness for running tests. 


### Getting Started

Nuget makes setting up your test project easy just grab the xUnit package and start writing tests. The catch with xUnit is out of the box your tests are not recognized by the Visual Studio test runner. In addition to the xUnit package you will need to install the xUnit.runner.visualstudio package then you can run your tests as usual. If you have Resharper you will need to install the xUnit runner extension. If you are on the latest and greatest and writing tests on dotNet core you can use the xUnit.runner.dnx package and get console and visual studio test running support in one place. 

### Facts And Theories

xUnit breaks tests down into two categories *Facts* and *Theories*.  It's may seem a litle unusual at first, but it's essentially how xUnit differentiates a test from a parameterized test. Think *Test* vs. *TestCase* in NUnit. The theory attribute also behaves differently than in Nunit or JUnit.  

### Setup and Tear Down

xUnit does not have attributes for test setup and tear down. Instead it leverages the tests classes constructor and dispose methods, so each test creates a new instance of the test class so by default the constructor becomes the test setup. If your test needs additional cleanup just have your test class implement *idisposable* and put your cleanup code there.

```cs
 public class gettingStartedTestsWithSetupAndTearDown:IDisposable
    {
        private ITestOutputHelper _outputter;

        public gettingStartedTestsWithTearDown(ITestOutputHelper output)
        {
            _outputter = output;
            _outputter.WriteLine("Setting Up Test");
        }

  //... tests
  
        public void Dispose()
        {
            _outputter.WriteLine("Tearing Down Test");
        }
    }
```

### Debugging Statements

It may not be pretty but it's pretty common to write to console for debugging or logging purposes in tests. This doesn't work in xUnit, its a bit surprising at first but it is for a good reason. xUnit will by default run tests in parallel, so debug, trace or console output could end up pretty confusing. 

To help bridge the gap xUnit offers the TestOutputHelper. To use it you need to have a constructor on your test class that has an ITestOutputHelper as a parameter. xUnit will then handle injecting into your class when tests are executed. 

```cs
    public class gettingStartedTests
    {
        private ITestOutputHelper _outputter;

        public gettingStartedTests(ITestOutputHelper output)
        {
            _outputter = output;
        }

        [Fact]
        public void FactsAreAlwaysTrue()
        {
            var testor = new TestorTheBarbarian();
            var expectedName = "Testor The Mighty Barbarian";
            
            // have to call .ToString since Health is an Int 
            // and WriteLine only accepts strings
              _outputter.WriteLine(testor.Health.ToString());

            Assert.Equal(expectedName, testor.Name);
        }
    }
```

I really like that xUnit supports parallelized test running, but the more complex the test classes are to read or maintain the easier it is to lose some of the intent of the tests. It's fine if you already have or need the test setup that the constructor provides but it seems a little over the top just to do some logging. Another minor irritation is that the output helper doesn't offer all the same overloads that the console or other output methods provide. It only takes a string or format string and parameters. So if you are migrating tests you may need to make changes or at least call *.ToString()*. 

### Assertions

I looked at xUnit several years ago and what I really liked about NUnit was the documentation, and looking at it again now it hasn't changed. The xUnit site has enough stuff to get you started but after that I felt like I was on my own to search either through the github repo or google. There is a great [xUnit Cheatsheet](http://dontcodetired.com/blog/post/xUnitnet-Cheat-Sheet.aspx) and [Pluralsight](http://app.pluralsight.com/courses/xunitdotnet-test-framework) course from Jason Roberts which help fill in the gaps, but comparing it to intellisense it looks like it might be slightly out of date.

You may notice that the list of assertions is pretty short and the syntax is a little short. My inclination is just to skip xUnit assertions and use [FluentAssertions](http://www.brendanconnolly.net/level-up-tests-using-a-custom-assertion-library-fluent-assertions/) or [Shouldly](http://www.brendanconnolly.net/level-up-tests-using-a-custom-assertion-library-shouldly/) instead.

 ### Digging Deeper
 There are a couple interesting options for data driven testing, as well as xUnit equivalents for *test fixture* setup and teardown that I'll be going deeper on in an upcoming post so stay tuned...