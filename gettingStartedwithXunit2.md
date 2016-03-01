### Test Fixture Setup and Teardown


In the last xUnit post we covered how xUnit handles setup and tear down of tests by using the constructor for setup and implementing IDisposable for tear down instead of the usual attributes. That's great but since xUnit instantiates an instance of the test class for each tes,t what if your tests require some common setup that you'd rather not have happen for every single test. 

Again no attributes for test fixture setup or test fixture teardown. Instead you create a separate class to contain the required actions.



 
### Built In Data Driven Options


### External Sources

