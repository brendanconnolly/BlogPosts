Testing: Benefits of using a custom Assertion Library
========================

When writing automated tests there is always some form of validation, typically called assertions. Typocally the tool or framework you are using usually provides some form this functionality out of the box. For example whenever you create a test project in Visual Studio by default you are going to be using MSTest. 

I've used MSTest and xUnit but mostly Nunit. I found MSTest harder to use, and more limited in syntax, xUnit had limited documentation, but Nunit well I love NUnit[1]. It's very flexible, well documented, has good options for data driven tests, plus a very broad and powerful set of assertions.

After that love fest over Nunit, why wouldn't you just use that? Why go beyond its greatness?

###Readability

###Lock In
Each framework has its own syntax. Special attributes to identify tests, special syntax for assertions.

- Reduces Lock in
- Readability
- Easier Test Writing
- Better Failure Messages

[1]:http://www.nunit.com