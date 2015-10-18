One of the most important parts of an automated test is a clear intent. Test frameworks like xUnit, MSTest, Nunit, etc. offer some powerful tools for structuring and executing tests. However, their syntax and conventions can be constraining for people writing the tests and more challenging for people reading the tests. 

FluentAssertions uses 

### Reduced Friction
Knowledge work requires a good amount of concentration and focus. If I can get into the [flow](https://en.wikipedia.org/wiki/Flow_(psychology)) my productivity will skyrocket. If I am battling the test environments or test framework it makes finding that flow extremely difficult. 

Traditional assertions that are built into the test frameworks require a context shift from the system under tests domain to the tools domain. This might not seem like a major issue at first especially for straightforward tests and validations. As your tests grow and you start to dive deeper into what you need from the test framework the more friction you might find. This is especially true if your tests don't fit nicely into what your framework offer, or you aren't familiar with the frameworks particulars. 

Fluent Assertion's solves this issue by using (an extensive collection of) extension methods designed to be explored through intellisense. Except for a few special cases, all of you choices are accessed through the "Should" method. This means theres little to no context shift, for example:

```cs
 Assert.AreEqual(expectedName, testor.Name);
 
 // becomes
 
 testor.Name.Should().Be(expectedName);
```


### Dates and TimeSpans

### Object Comparison



To see more examples check out the Fluent Assertions test project in my [AssertionExamples](https://github.com/brendanconnolly/AssertionExamples) project on GitHub. 