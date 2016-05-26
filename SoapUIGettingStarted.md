![learning soapui meme ](http://www.brendanconnolly.net/wp-content/uploads/2016/05/SoapUImeme.jpg)
Every few weeks or so I see a new question on the LinkedIn's Test Automation group about getting started writing API tests and there's almost always a flurry of responses recommending [SoapUI](https://www.soapui.org/). There are definitely alternatives, but if you are just getting into automation or API testing in general SoapUI offers a visual interface that may help ease you into the process. It does take a little getting used to since it can feel a little less than intuitive at times. Hopefully this will help smooth some of the rough edges...

We'll use [Global Weather Service](http://www.webservicex.com/globalweather.asmx) since it's free, publicly accessible and provides a *web service description language* definition or [WSDL](https://en.wikipedia.org/wiki/Web_Services_Description_Language). If you aren't familiar with WSDLs they define the contract that a client application needs to use to successfully communicate with a web-service. 

So lets fire up SoapUI and jump right in with creating a test suite for a SOAP based web service.
 
 Start by going to:  **File --> New SOAP project**
 
 You will be greeted by this prompt:
 ![new soap project prompt](http://www.brendanconnolly.net/wp-content/uploads/2016/05/NewSoapProject.png)
 
We need to provide a name for the project and a location for where the WSDL for the service can be found. The WSDL location can be a flat file or as you can see in this example a url. By default the *Create Requests* box is checked, since we will be adding tests we will also check the *Create Test Suite* box.

Next we need to enter some details about our test suite:

![test suite prompt](http://www.brendanconnolly.net/wp-content/uploads/2016/05/GenerateTestSuite.png)

In the **Style** section you chose how some default tests will be created:

* One TestCase for each Operation - This will create separate tests in the TestSuite  for each request contained in the WSDL.

* Single TestCase with one Request for each Operation - This will create a single test in the TestSuite with each request inserted as a test step.

The **Operations** section lists the available requests provided by the WSDL. So if you only wanted to target a few of the requests for testing or maybe certain requests function together to create a workflow you make that choice here.

You will go through this process 2 times, it might seem surprising at first but the reason is that there are different versions of SOAP (1.1 and 1.2). These differences result in the communication between client and service being handled differently. The contents of the request may look the similar but under the hood they are bound to the different SOAP versions. SoapUI goes through the configuration process for each binding. 

### Customizing Tests

The test suite will now look like this
![project view](http://www.brendanconnolly.net/wp-content/uploads/2016/05/ProjectView.png)

You can see that for *GlobalWeatherSoap12* I chose the *Single TestCase* style and for *GlobalWeatherSoap* I chose the *One TestCase for each Operation*.
TestCases are comprised of TestSteps, by default the wizard will insert steps for the request operation(s). 

#### Editing Requests Steps
When you double-click on one of the SOAP Request steps you have the option to edit the request contents. By default SoapUI inserts a **?** in the fields of the request where input is expected. 

You can also try out the request with the any changes you have made by pressing the play button. The response will be displayed in the text box next to the request.
Don't be too concerned about making changes to the request here, if you get into a state where you need to go back to a clean slate use the refresh button to regenerate the request from the WSDL.  

![get cities request view](http://www.brendanconnolly.net/wp-content/uploads/2016/05/GetCitiesRequestView.png)

#### Inserting New Steps
I felt a little dirty going directly into the xml to make changes for each test. It's fine for static content that really isn't in scope for your tests you can use the request xml as a template but you might want to visibly separate real test input so the tests intent is more clear. What if you want to extract data out of the response and feed that into another request? 

All this is handled through adding new tests steps. You can add steps by right clicking on an item in the TestCase tree
![test step via context click](http://www.brendanconnolly.net/wp-content/uploads/2016/05/TestStepViaContext.png)

Or if you are in the Test Case Editor, the same options are available as icons above the test step list
 ![test step via editor](http://www.brendanconnolly.net/wp-content/uploads/2016/05/TestStepViaEditor.png)

#### Passing Data to Requests

Passing test input to a request is a 2 step process. First we need to create a *Property Step*. This basically allows you to add name value pairs that you can reference later in the test. You have the option to input them all directly or load them from a properties file.  
![create property step](http://www.brendanconnolly.net/wp-content/uploads/2016/05/CreatePropertyStep.png)
The properties file can also be specified when running tests from the command-line allowing you to vary your test data. Other dat driven options are available but not in the free version of SoapUI.

Once you have your properties created you need to create a *Transfer Step* to pass them to the request. This step maps the source to the target location. It's very straight forward when using a property step like we create above. SImply select the name of the test step you want to retrieve data from in the source drop-down and the property drop-down will populate with available options for you to select. You can ignore the path language when using a property step.

The target destination can be a little trickier. In this case we are injecting the property value into our request, so we choose SOAP request step and for property choose *request*. To tell SoapUI where to place our input we have 2 options: XPath and XQuery. The default is XPath, this works well in this case since the request is a fixed format. The harder part now is generating the correct XPath to use. To assist in defining the namespaces within the WSDL xml there is tiny *ns* button next to the 2 green triangles. Clicking this will insert the namespace declaration into the textbox for you. There are plenty of tools online to help you generate the XPath you will need, but don't be discouraged if you are new and feel a little intimidated at first. The play button will let you test out the transfer and will log any issues if they occur. 

![create transfer step](http://www.brendanconnolly.net/wp-content/uploads/2016/05/CreateTransferStep.png)

To feed data from one request to another its just a matter of adding another transfer step and getting the XPath or XQuery statements you need. 

#### Assertions 

What would any test be without assertions to validate the tests actions. You can add assertions to any of the request test steps by double clicking the step and clicking the green plus icon. There are a ton of [built in assertions](https://www.soapui.org/functional-testing/validating-messages/getting-started-with-assertions.html#2-Assertion-categories). Most of the time you'll probably be using the ones listed below (there's also a *not* contains). 

![add assertion](http://www.brendanconnolly.net/wp-content/uploads/2016/05/AddAssertion.png)

Since the api being called returns the details of its response in an xml cdata block that gets interpreted as a text string instead of xml, I can't use XPath or XQuery. Instead I use the contains assertion and I can at least validate that somewhere in the response the value I am looking for is present. 

![contains assertion](http://www.brendanconnolly.net/wp-content/uploads/2016/05/ContainsAssertion.png)

### Wrapping Up
Once your assertions are in place, to run tests double click the test suite, or test case you want to run and click the play button. 

There's plenty more in Soap UI but hopefully this is enough to get you up and testing!

 
 