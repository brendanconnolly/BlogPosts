

### Getting Started

Nuget makes setting up your test project easy just grab the xUnit package and start writing tests. The catch with xUnit is out of the box your tests are not recognized by the Visual Studio test runner. In addition to the xUnit package you will need to install the xUnit.runner.visualstudio package then you can run your tests as usual. If you have Resharper you will need to install the xUnit runner extension. 


### Facts vs. Theories

xUnit breaks tests down into two categories *Facts* and *Theories*.  It's may seem a litle unusual at first, but it's essentially how xUnit differentiates a test from a parameterized test. Think *Test* vs. *TestCase* in NUnit. The theory attribute also behaves differently than in Nunit or JUnit.  

### Setup and Tear Down

xUnit does not have attributes for test setup and tear down. Instead it leverages the tests classes constructor and dispose methods, so each test creates a new instance of the test class so by default the constructor becomes the test setup. If your test needs additional cleanup just have your test class implement *idisposable* and put your cleanup code there.

### Debugging Statements

### Assertions

I looked at xUnit several years ago and what I really liked about NUnit was the documentation, and looking at it again now it hasn't changed. The xUnit site has enough stuff to get you started but after that I felt like I was on my own to search either through the github repo or google. There is a great [xUnit Cheatsheet](http://dontcodetired.com/blog/post/xUnitnet-Cheat-Sheet.aspx) and [Pluralsight](http://app.pluralsight.com/courses/xunitdotnet-test-framework) course from Jason Roberts which help fill in the gaps. 


  