![cooties sloth meme](http://www.brendanconnolly.net/wp-content/uploads/2016/06/cootiesMeme.jpg)

There's a lot of fear and mysticism associated with code. As a result some testers treat interacting directly with code like its covered in [cooties](https://en.wikipedia.org/wiki/Cooties). Immediately taking evasive action to avoid the potential exposure to that life threatening imaginary playground disease. 

Seriously though, no matter how readable it may seem to those familiar, it's easy to forget that just because its code many people will tense us or get a mental block before they even get a chance to start looking at it. 

The purpose here isn't really to teach you to code. The goal is instead to get you more comfortable with what you are seeing on the screen so you can feel a little more at ease when you pair / chat with a developer, even if just at a common vocabulary level. 

Before we dive into the test file just a couple notes:

C# *case sensitive*, so in theory the code below would cause an error.
``` cs 
 string Player1 ="george";
  player1="paul";
```

You'll also see a lot of curly braces *{ }*. If you aren't used to them don't be intimidated they basically just group portions of code. So if you are familiar with HTML/XML think of them as open and closing tags.

Lastly C# uses the semi colon *;* instead of newline as the line terminating character. 

With that out of the way lets walk through a C# file that has a sample integration test to get a feel for some key concepts.

### [References](https://msdn.microsoft.com/en-us/library/sf0df423.aspx) 

Using statements you see below are called references. They basically serve as a declaration that the code in this file will be using functionality from the following external sources. 

``` cs
using ApprovalTests;
using ApprovalTests.Reporters;
using SUT.TestDriver;
using Xunit;

```

### [Namespace](https://msdn.microsoft.com/en-us/library/z2kcy19k.aspx)

Namespaces are  a means of organizing and grouping. By default a namespace is generated using the project structure. That means if you add a new file at the root of your project the default namespace will be that of the project. If you add a folder and then create a new file inside that folder the default namespace will be *projectName.folderName*. 

Namespaces are important because they help prevent naming collisions. Say your company sells dictionaries, and part of your code base includes things you've named dictionary. It just so happens that the .Net framework includes its own defintion of a dictionary, how could your code tell when you wanted to use your companies dictionary or the one provided by .Net? Namespaces allow you to specify which one you want to use.

```cs
namespace SUT.Tests.Integration
{
```

### [Class](https://msdn.microsoft.com/en-us/library/0b0thckt.aspx)

``` cs 
 [UseReporter(typeof(DiffReporter))]
    public class GivenATestScenario
    {
```


### [Access Modifiers](https://msdn.microsoft.com/en-us/library/wxh6fsc7.aspx)

You may see *public* and *private* in front of the names of different things in the code you are looking at. These are referred to as *access modifiers*, and as the name describes they govern what pieces of your code can be accessed when other people try to use it. Things that are marked public will be available for others to access, whereas private means it will be hidden from them. There are other modifiers like *protected* or *internal* but generally if it is not *public* then it is private to some degree. Check out the link above if you are interested in more specifics. 


### [Constructors](https://msdn.microsoft.com/en-us/library/ms173115.aspx)

Constructors are a special kind of function that is called by the .Net runtime when new things are created. They allow the author to have code that will prepare the object for use, like buildings are constructed. The constructor is guaranteed to be called, and like other functions may or may not accept input parameters. 

In the example below you can see that when the test class is created the constructor is loading configuration data from the Config.json file and storing it in a variable so tests will have access to it. 

How can you tell a constructor from other functions? The constructor must have the same name as the class and will not have a return type.

``` cs
        private readonly dynamic _config;


        public GivenATestScenario()
        {
            var configAccessor = new ConfigurationAccess();
            _config = configAccessor.GetConfig("Config.json");

        }
```

### [Comments](https://msdn.microsoft.com/en-us/library/aa664667.aspx)
You've probably heard of code comments, but if you haven't they are basically notes in or around code that hopefully make it easier to understand, or explain the authors choice. C# has 2 different options for comments:

*Single Line* 
```cs 
// single line comments begin with 2 forward slashes
```

*Multi Line / Intra Line*
```cs
/* this comment can be on multiple lines 

or placed between some statements */
```


### [Attributes](https://msdn.microsoft.com/en-us/library/mt653979.aspx)
Attributes, sometimes referred to as *decorators* allow you to associate behavior with a class and/or function. In this case we have examples of attributes on both a class **[UseReporter(typeof(DiffReporter))]** and function **[Fact]**. 

Fact, is the attribute that xUnit requires be added to functions to indicate that they are tests, so test running tools can easily identify them.  

UseReporter, is used by ApprovalTests to identify what type of tool to use for the tests verification. This example also shows that attributes can accept parameters. 

So you can see in both examples we are associating new behavior with our classes and functions without having to explicitly execute it. 


### [Data Types](https://msdn.microsoft.com/en-us/library/ms228360.aspx#Anchor_1) 

Since C# is a *typed* language, whenever you want to store data in a variable you need to specify what kind of data it will be. 
The kind of data is called the data type, let's peek at a few of the core types. 

**Text** is referred to as a string, like a word is *string* of letters or characters. 

**Numbers** are a little more tricky, the type that you need is based on the precision of number you are using. You'll see *int*, *decimal*, *long* and others. For more detail check out the data types link above. 

**Collections of Data** have a few options as well, but the most basic is an *Array*. You can recognize an array because at the end of the usual type name you'll see **[]**. 


### [Functions](https://msdn.microsoft.com/en-us/library/ms173114.aspx)

Functions (also reffered to as *methods*) are where are the logic and behavior are defined. So in this case each test is an individual function. Functions may or may not return data. You can tell because between the access modifier ( in this case public) and the name of the function you will see the *return type*. When the function returns nothing the return type will be *void*, otherwise the proper data type will be specified. 

Functions may also accept parameters. When a function accepts no parameters (like the test below) the only thing after the function name is empty parenthesis *()*. When parameters are accepted inside the parenthesis will be a comma separated list of data type and parameter name pairs ex. *(string name, int age)*. This is referred to as the methods signature. It's important to note that when using/calling a function (except in some more advanced cases) the code invoking the function has to include parameters that match the methods signature. So when a function accepts no parameters you can't have anything inside the parenthesis. Conversely if parameters are specified, then you have to specify values for all of them and the order matters.

```cs

        [Fact]
        public void When_SomeCondition_ThenResultsShouldMatchExpected()
        {
            ITestClient driver = new TestDriver().WithServer(_config.Server);

            var firstResponse = driver.Request1
                .WithClientData(_config.ClientData)
                .WithFinancials(_config.SomeConditionalTestValues)
                .Send();


            driver.Request2
               .WithClientData(_config.ClientData)
               .WithInvoiceId(firstResponse.InvoiceId)
               .Send();

            Approvals.VerifyAll(driver.History,Scrubber.Clean);

        }

```

 
 