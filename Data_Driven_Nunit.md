

We'll be using nunit 3 for these examples so I'll be covering the option for data driven tests and some of the changes for nunit 3.0

### Why Write Data Driven Tests


### Values

 You start by annotating the test method with the usual Test attribute that NUnit uses to identify tests. Then you use the Values attribute to specify a range of inputs for each parameter inside of the tests method signature. 
 

``` cs

        [Test]
        public void testGetShippingRate_Combinatorial(
            [Values("60050", "22015", "32043")] string sourceZipCode, 
            [Values("60050", "93108","11111")] string destinationZipcode, 
            [Values(5D,0.5D,100.55D,993D)] decimal packageWeight)
        {
            decimal src = 0;
            decimal dest = 0;

            decimal.TryParse(sourceZipCode, out src);
            decimal.TryParse(destinationZipcode, out dest);

            decimal expectedResult = src + dest + packageWeight;

            decimal actualRate = _shipper.getShippingRateByZipCode(sourceZipCode, destinationZipcode, packageWeight);

            Assert.That(actualRate, Is.EqualTo(expectedResult));
        }

```

#### Combinatorial and Pairwise

By default tests for all permutations of the different parameters will then be automatically generated. This is referred to as the *Combinatorial* approach. It can be a very powerful tool and helpful to remove boilerplate code and/or reduce the number of copy and paste style tests inside your test fixture. 

However, it can also lead to test explosion since all possible permutations are generated. It is tempting to add more and more values to each parameter and end up with hundreds of tests. It gets challenging to reason about the tests that are generated as the number of parameters and inputs grow.  You also need to consider that all permutations that get generated may not be valid or may actually be duplicate cases.

The *Pairwise* attribute is an option to try to reduce the number of tests generated. [Pairwise](http://www.pairwise.org/) creates tests for all the unique pairs of inputs. So for example the example above would generate 36 different tests. Applying the Pairwise attribute shown below reduced the number for tests created to 12.

```cs
        [Test]
        [Pairwise]
        public void testGetShippingRate_Pairwise([Values("60050", "22015", "32043")] string sourceZipCode, [Values("60050", "93108", "11111")] string destinationZipcode, [Values(5D, 0.5D, 100.55D, 993D)] decimal packageWeight)
        {
            decimal src = 0;
            decimal dest = 0;

            decimal.TryParse(sourceZipCode, out src);
            decimal.TryParse(destinationZipcode, out dest);

            decimal expectedResult = src + dest + packageWeight;

            decimal actualRate = _shipper.getShippingRateByZipCode(sourceZipCode, destinationZipcode, packageWeight);

            Assert.That(actualRate, Is.EqualTo(expectedResult));
        }

```

#### Sequential
If you want to use the Values attribute and want to specify specific parameter sets you can apply the Sequential attribute. This guarantees that parameters will be applied in sequential order, so the first value of each parameters will be a test. It is important to note that this does not guarantee the order that the tests will be executed. The sequence is about the parameter order not the test order. 

```cs 
        [Sequential]
        public void testGetFlatRateByWeight([Values(4.5D, 15D, 55D, 125D)] decimal packageWeight, [Values(10.99, 29.99, 75.55, 999.99)] double expectedRate)
        {
            double actualRate = _shipper.getFlatRateByWeight(packageWeight);

            Assert.That(actualRate, Is.EqualTo(expectedRate));
        }
```
Unless you are using sequential to maintain a convention throughout your tests or some other specific reason, using *TestCase* may be a better and more readable fit.

### TestCase
For each permutation of a test you want to run you add a *TestCase* attribute with the parameter values desired for the test. This removes some of the magic that the *Values* attributes introduces. Each test permutation is clearly listed separately above the test method signature. There is no question what inputs will be passed to the tests. There are also named parameters for TestName and Description that allow each test case to have a clear intent.

```cs
        [TestCase("60050", "17042", 1D, 86.02D)]
        [TestCase("22015", "30040", 50D, 802.5D)]
        [TestCase("32043-5694", "30040-6941", 0.5D,  2D)]
        public void testGetShippingRate(string sourceZipCode, string destinationZipcode, decimal packageWeight, decimal expectedResult)
        {
            decimal actualRate= _shipper.getShippingRateByZipCode(sourceZipCode, destinationZipcode, packageWeight);

            Assert.That(actualRate, Is.EqualTo(expectedResult));
        }
```

You can also use a named parameter to specify the result value of a test. To use this the test method needs to return a value, then NUnit will automatically compare the return value of the test method to the result value specified in the *TestCase* attribute. The test itself does not contain an assert statement, so this approach may rub some people the wrong way. I'm sure there are circumstances where this is a good fit, but I prefer not to have an implicit assertion in the test. It also requires some understanding of the test framework being used to avoid confusion.

```cs

        [TestCase("60050", "17042", 1D, ExpectedResult = 86.02D, TestName = "Source Greater Than Destination")]
        [TestCase("22015", "30040", 50D, ExpectedResult = 802.5D, TestName = "Source Less Than Destination")]
        [TestCase("32043-5694", "30040-6941", 0.5D, ExpectedResult = 2D, TestName = "9 digit zipcodes with dashes")]
        public Decimal testGetShippingRate_withImplicitAssert(string sourceZipCode, string destinationZipcode, decimal packageWeight)
        {
            return _shipper.getShippingRateByZipCode(sourceZipCode, destinationZipcode, packageWeight);
        }   

``` 

This is also an area that has changed between NUnit 2.X and 3. In 2.X the parameter name used was *Result* in NUnit 3 this has changed to ExpectedResult. 

### TestCaseSource
You may have noticed that the methods above have used primitive types for the different test permutations. What if you want to use complex types, or want to load test cases from external sources? The *TestCaseSource* attribute steps in to allow you to use separate methods or properties to hold the test data. This attribute expects the a string that is the name of a field, property or method that will return an IEnumerable. 

```cs
        static decimal[] under5PackageWeights = new decimal[] { 0.01m, 2m, 4.99m };

        [TestCaseSource(nameof(under5PackageWeights))]
        public void test_GivenPackageWeightLessThan5_ThenFlatRate_10_99(decimal packageWeight)
        {
            double actualRate = _shipper.getFlatRateByWeight(packageWeight);

            Assert.That(actualRate, Is.EqualTo(10.99));
        }


```

NUnit also provides a *TestCaseData* object that allows you specify simple or compex types while also giving access to extended test information. Each instance of *TestCaseData* exposes methods to set test name, categories and a host of other options. It makes data driven tests a first class citizen since you can how the tests will look when they are loaded into a test runner, or for results reporting. You could have test data parsed out of a csv file and instead of it showing as a cryptic string of data in the test runner you can set a friendly name or set categories to allow for more refined test runs.

```cs 
        public static IEnumerable<TestCaseData> bulkSource()
        {
            yield return new TestCaseData(new List<iContainer> { new Box(3, 1, 2) }).SetName("Bulk-Box Only");
            yield return new TestCaseData(new List<iContainer> { new Box(10, 2, 5), new Bag(10) }).SetName("Bulk-Box and Bag");

        }

        [TestCaseSource("bulkSource")]
        public void testBulkRate(IEnumerable<iContainer> items)
        {
            double expectedPrice = 0;
            foreach (iContainer item in items)
            {
                expectedPrice += item.getPriceToShip();
            }

            var actualPrice = _shipper.getBulkRate(items);

            Assert.That(expectedPrice, Is.EqualTo(actualPrice));

        }
```
Previously these sources could be instance or static members. In NUnit 3 the sources are required to be static members of a class. 

### Thoughts on NUnit 3
This was really more than a version bump for NUnit is has been a [rewrite](http://www.infoq.com/news/2015/12/nunit-3-charlie-poole). As you might expect from a rewrite there are quite a few [breaking changes.](https://github.com/nunit/nunit/wiki/Breaking-Changes)

One of the most obvious changes was to [setup and teardown](https://github.com/nunit/nunit/wiki/SetUp-and-TearDown-Changes). The *TestFixtureSetup* and *TestFixtureTearDown* attributes have been rename to *OneTimeSetup* and *OneTimeTearDown*. Their behavior is also changed, teardown (either one time or regular) will only called when the respective setup method was previously been called.

NUnit is also late to the party in DotNet Core support. Despite all the changes and enhancements, DotNet Core tests still require using work arounds to be run. DotNet Core and ASP.Net 5 are all using xUnit as their chosen framework, and most [examples](http://blogs.msdn.com/b/webdev/archive/2015/08/06/unit-testing-with-dnx-asp-net-5-projects.aspx) you find will be about using xUnit rather than NUnit or MSTest. 

I have been reading about the update to version 3 for years and was excited to see it finally available. While it's officially released it seems like there is a fair amount of work to be done. There is no GUI runner yet, and pulling in or updating the nuget package to nunit 3 requires a new test plugin for visual studio. 

I'm not sure if I am just adjusting to the new version, but while it works, in some areas it feels like a 1.0 release of a new framework. So far the [documentation](https://github.com/nunit/nunit/wiki), which previously one of my favorite things about NUnit is a little lacking compared to previous versions. I have been a big NUnit fan to date but it seems like a harder sell today, and I think I'll be taking a deeper look into xUnit.






