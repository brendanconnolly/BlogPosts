![SoapUI with Rest service meme](http://www.brendanconnolly.net/wp-content/uploads/2016/06/SoapUIWithRestMeme.jpg)
Last week we took a look at [Getting Started with SoapUI](http://wp.me/p6vwxg-4Q) using a SOAP based web service. 

Despite the what the name [SoapUI](https://www.soapui.org/) supports restful API testing as well as SOAP based testing. We'll use a [pet store api](http://petstore.swagger.io/) provided by the [Swagger](http://swagger.io/) team.

Let's fire up SoapUI and jump right in...

Start by going to:  **File --> New REST project**

The you will see this dialog:
![New Rest Project](http://www.brendanconnolly.net/wp-content/uploads/2016/06/NewRestProject.png)

While it may not look like it, from here you have three different options for getting your services requests added into the project. 

### Using WADL

[WADL](http://www.nurkiewicz.com/2012/01/gentle-introduction-to-wadl-in-java.html), is kind of like a WSDL but for REST based services. The implementation is different but it was designed to serve a similar purpose which is to define a contract for applications or services interacting with the service.

If your service provides a WADL, on the **New REST Project** dialog click the **Import WADL** button.

Enter the location of WADL this can be a local file or a url. 

![New Wadl Project](http://www.brendanconnolly.net/wp-content/uploads/2016/06/NewWadlProject.png) 

Click Ok and your resources and requests will be added to the project.

![Wadl Import](http://www.brendanconnolly.net/wp-content/uploads/2016/06/WadlImport.png)

### Using Swagger

If you aren't familiar with Swagger and your team is using restful api's it's worth taking a look at. To quote their web site:
>With a Swagger-enabled API, you get interactive documentation, client SDK generation and discoverability.

As a tester the interactive documentation is awesome, it's hosted as part of the web service, so theres no pulling up a separate site or document. You see all the endpoints and can execute requests directly from it, and when you do in addition to the request and response information it also includes the [curl](https://curl.haxx.se/docs/manpage.html) command you can run to recreate it. 

On top of all that, SoapUI supports importing Swagger just like we did with the WSDL for SOAP based services.

To use Swagger, do not enter any information on the **New REST Project** dialog. From here you click on the project name in the navigation tree then go to **Project --> Import Swagger** or you can right click on the project name and select **Import Swagger** from the context menu.

From here you can browse to the swagger file or enter a URL where SoapUI can download the Swagger definition. You also have the option to set the default media type but it will default to JSON.

![add swagger definition](http://www.brendanconnolly.net/wp-content/uploads/2016/06/AddSwaggerDefinition.png)

Once imported, you see a screen that shows all the resources added and seems to talk a lot about WADL's considering you just used Swagger...
![Swagger Import](http://www.brendanconnolly.net/wp-content/uploads/2016/06/SwaggerImport1.png)

SoapUI automatically generates a WADL file for you so you can export it if you need to use it later or for some other purpose.
![Create Wadl](http://www.brendanconnolly.net/wp-content/uploads/2016/06/GeneratedWadl.png)


### Manually Adding Endpoints

If WADL or Swagger isn't an option for you SoapUI allows you to manually enter the resources and requests. At the **New REST Project** dialog you can enter your first endpoint in the Uri text box. 

If you have additional resources to add you'll need to right-click on the navigation tree item with the 2 blue arrows that lists your base uri and select **New Resource**. 

#### New Resources
![New Rest Resource](http://www.brendanconnolly.net/wp-content/uploads/2016/06/NewRestResource.png)

Then configure the request method, message body or any parameters in the request editor window.
![Request Editor](http://www.brendanconnolly.net/wp-content/uploads/2016/06/RequestEditor.png)

To add additional methods to a resource, right-click the resource and select **New Method** 
#### New Methods
![New Rest Method](http://www.brendanconnolly.net/wp-content/uploads/2016/06/NewRestMethod.png)

If your api is fairly small this process may not be too painful, but beyond that it feels a bit cumbersome so good luck!

### Creating TestSuites

From here on out the process is pretty similar to what we walked through last week using a SOAP service. Right click on your project and select **Generate TestSuite**
 
![Generate TestSuite](http://www.brendanconnolly.net/wp-content/uploads/2016/06/ConvertSwaggerToTestSuite.png)

![GenerateTestSuite](http://www.brendanconnolly.net/wp-content/uploads/2016/06/GenerateTestSuite.png)

In the **Style** section you chose how some default tests will be created:

* One TestCase for each Resource - This will create separate tests in the TestSuite at the resource level which basically means if you have multiple HTTP methods associated with a resource they wil lbe grouped in a single testcase. So you could have a single test that includes your CRUD (create, read, update, delete) operations. 

* Single TestCase with one Request for each Method - This will create a single test in the TestSuite with each request inserted as a test step.

One thing in particular to watch out for here is that  as the TestSuite is generated if requests have identical names you will be prompted for a unique name. The trouble is the prompt doesn't include the requests HTTP verb so get to guess the first time through. Then when the process completes you can go through the test steps and see the properties and rename if necessary. 

### Customizing Tests

Again the process here is just like with a SOAP service. You use property steps and property transfer steps to arrange your requests and Assertions for validation.

The biggest difference is in addition XPath and XQuery since many REST interfaces use JSON either instead of (or in addition to) XML we have [JSONPath](http://goessner.net/articles/JsonPath/). 

There seems to an issue that SoapUI 5.2 is having with Property Transfers on with JSON and JSONPath due to a parsing error. You can read more about it on their [support forums](https://community.smartbear.com/t5/SoapUI-Open-Source/SOAP-UI-5-2-is-throwing-JSON-invalid-error-while-property/td-p/105075). It's too bad I find JSONPath easier to use if nothing else due to the lack of namespacing required for XPath.

This may cause issues if you need transfer values from one request to the next but Assertions on JSON are unaffected. If you want to see more on properties, property transfers and assertions check out my [Getting Started with SoapUI](http://wp.me/p6vwxg-4Q) post.

Good luck and happy testing!


