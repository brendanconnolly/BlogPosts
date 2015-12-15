

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

### TestCaseSource
now required to be static

### Setup and Teardown
teardown only called when a setup has previously been called.

changes in nunit 3
https://github.com/nunit/nunit/wiki/SetUp-and-TearDown-Changes

### Thoughts on Nunit 3
This was really more than a version bump for nunit is has been a [rewrite](). While it's officially released it seems like there is a fair amount of work to be done. Pulling in or updating the nuget package for nunit 3 requires a new test plugin for visual studio.
#### Runners

#### DotNet Core Support
