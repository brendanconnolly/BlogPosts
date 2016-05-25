Every few weeks or so I see a new question on the LinkedIn's Test Automation group about getting started writing API tests and there's almost always a flurry of responses recommending [SoapUI](). There are definately alternatives, but if you are just getting into automation or api testing in general SoapUI offers a visual interface that may help ease you into the process. It does take a little getting used to since it can feel a little less than intuitive at times. Hopefully this will help smooth some of the rough edges...

We'll use [Global Weather Service]() since it's free, publicly accessible and provides a *web service description language* definition or [WSDL](https://en.wikipedia.org/wiki/Web_Services_Description_Language). If you aren't familiar with WSDLs they define the contract that a client application needs to use to successfully communicate with a webservice. 

So lets fire up SoapUI and jump right in with creating a test suite for a SOAP based web service.
 
 Start by going to:  File --> New SOAP project
 
 You will be greeted by this prompt:
 ![new soap project prompt](http://www.brendanconnolly.net/wp-content/uploads/2016/05/NewSoapProject.png)
 
We need to provide a name for the project and a location for where the WSDL for the service can be found. The WSDL location can be a flat file or as you can see in this example a url. By default the *Create Requests* box is checked, since we will be adding tests we will also check the *Create Test Suite* box.

Next we need to enter some details about our test suite:

![test suite prompt](http://www.brendanconnolly.net/wp-content/uploads/2016/05/GenerateTestSuite.png)

#### Style

#### Request Cotent


 
 