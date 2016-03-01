### Test Fixture Setup and Teardown


In the last xUnit post we covered how xUnit handles setup and tear down of tests by using the constructor for setup and implementing IDisposable for tear down instead of the usual attributes. That's great but since xUnit instantiates an instance of the test class for each tes,t what if your tests require some common setup that you'd rather not have happen for every single test. 

Again no attributes for test fixture setup or test fixture teardown. Instead you create a separate class to contain the required actions. Then you have the class containing your tests inheirit IClassFixture<T> where T is the class containing the fixture setup. xUnit will then recognize that the class needs to be instantiated before the tests are run. If you need to access members or methods inside the setup class you then need to have your test class contain a constructor with that type as a parameter and xUnit will inject it for you. 


```cs
public class FixtureState:IDisposable
{

public void FixtureState()
{
//Fixture Setup Here 
}

public void Dispose()
{

//Fixture Tear Down Here
}


}

public class Tests:IClassFixture<FixtureState>
{

private FixtureState _fixture;

//if you want access to members of the shared fixture FixtureState
public Tests(FixtureState theState)
{
  _fixture=theState;
}

//tests

}

```
I'm not sure exactly how I feel about this arrangement. I felt like using the constructor for setup and and IDisposable for teardown made logical sense. This however seems like it might start to convolute your test classes.  It may seem like a heavy solution to some, since  a whole separate class has to wired up and injected. Part of me says that it makes sense to start separating the concerns like this. Looking at the code though it feels a little harder to consume for newcomers. 
 
### Built In Data Driven Options

#### Internal Sources

There are three different attributes to start with when using data driven tests where the data provided will be code based. *MemberData* and *PropertyData* attriutes accept a name of a static member or property that needs to return an IEnumerable<object[]>  where the object array contents match the method signature of your test. There is also *ClassData* which accepts a type name of a class which is enumerable that xUnit will instantiate and use to supply values to your tests. 

#### External Sources

xUnit offers some nice options for utilizing external data to drive you tests. They follow the same convention as the internal sources of being *Data, however you won't find them documented on the xUnit site.  *ExcelData*, *SqlServerData*  