Once you start to have a larger number of tests it can be important to be able to break them down into different categories or groupings. From a functionality perspective this allows you to only run a subset of tests. They can also help to provide clarity or insight to your test code, by replacing comments or bloated test names with code based cues to preconditions or domain of the tests. 

Both NUnit and MSTest make use of the *Category* verbage. NUnit using the [Category Attribute](https://github.com/nunit/docs/wiki/Category-Attribute) and MSTest using the [TestCategory Attribute](https://msdn.microsoft.com/en-us/library/dd286683.aspx). You might expect xUnit to also have something named similarly, but instead they have chosen the *Trait* attribute. 

### Traits

If you atre used to using categories from other frameworks, the *Trait* attribute is slightly confusing when you first look at it. 
Instead of:
```cs
[Category("MyCategoryName")]
public void ...

```
The trait attribute uses a name and value pair

```cs
[Trait("Category","MyCategoryName")]
public void ...
```

When I first saw this I wasn't sure if the name property value had any significance, i.e. is it a set of magic strings I ended up peeking through the framework code on GitHub to confirm that the name parameter is up to user preference. If you are familiar with NUnit then it's like a hybrid of the category and [property](https://github.com/nunit/docs/wiki/Property-Attribute) attributes. 

### Test Runner View

Another benefit to organizing tests using traits is that when using a GUI based test runner, like the test runner in Visual Studio the tests can be sorted accordingly. 
For Example:
```cs 
[Fact]
[Trait("Category","Unit")]
public void Test1(){
    ...}

[Fact]
[Trait("Category","Integration")]
public void Test2(){
    ...}

[Fact]
[Trait("Category","UI")]
public void Test3(){
    ...}

```
Results in the following display where you can run tests individually or by category. 
![test view by categories]()

### On The Commandline

When executing tests from the commandline you can run only a specific category or cateogries. 
```
xunit.console.exe ... -trait "Category=Unit"
-or-
xunit.console.exe ... -trait "Category=Integration" -trait "Category=UI"
```

Exclude a category or categories
```
xunit.console.exe ... -notrait "Category=Integration"
-or-
xunit.console.exe ... -notrait "Category=UI" -notrait "Category="UI"

```

Or you can mix and match to your hearts content.

### Custom Traits

I found *traits* to feel a little messy, it felt very flexible but at the price of being less inutitive to people that are not already familiar with xUnit. It may not be a huge issue but there seems to be a higher liklihood of misspellings or typo's causing tests to not be run. Luckily xUnit supports creating custom traits. 

In ealrier versions it was as simple as subclassing the trait attribute but in later versions that class has been [sealed](https://github.com/xunit/xunit/issues/394). The current process involves implenting the *ITraitAttribute* *ITraitDiscoverer* interfaces for your custom trait. The xUnit Samples repo on GitHub provides [sample code for Category](https://github.com/xunit/samples.xunit/tree/master/TraitExtensibility). 

The only issue is the Visual Studio and Resharper test runners do not use the newer process to discover traits. This means that you cannot currently visually group test by custom traits until they update their test runners. 


### Friendly xUnit Categories

If you want to run tests by trait, both key and value of a trait must be specified on the commandline. This makes sense when the trait name is generic like category. What if you want something more specific like marking tests related to bugs like **[Trait("Category","Bug")]**. It looks fine, but the problem is you can't run only tests for a specific bug unless you add another attribute  like **[Trait("Bug","8675309")]**.

To make the process more friendly and to add a little flexibilty/functionality I created [xUnit.Categories](https://github.com/brendanconnolly/Xunit.Categories) or use the [nuget package](https://www.nuget.org/packages/xunit.categories/).

``` cs
        [Fact]
        [Bug]
        public void TestBug()
        {
            throw new NotImplementedException("I'm a bug");
        }
        
        [Fact]
        [Bug("777")]
        public void TestBugWithId()
        {
            throw new NotImplementedException("I've got your number");
}

```

Using this attribute you get descriptive information and flexibility when running tests. 
You can run all tests marked as Bugs

``` bat
xunit.console.exe ... -trait "Category=Bug"
```

or get more granular
``` bat
xunit.console.exe ... -trait "Bug=777"
```