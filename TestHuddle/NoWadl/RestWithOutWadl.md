Despite the name, SoapUI can be used for testing Restful as well as SOAP based apis. There are many differences between SOAP and REST but the biggest when it comes to SoapUI is that SOAP apis provide a [WSDL](). The wsdl defines the contract for the client application, so SoapUI takes that and generates the navigation tree with all possible requests and even populates template xml for them so you can quickly start testing.

The REST equivalent to WSDL is [WADL](). SoapUI can take a REST services WADL just like it would take a WSDL for SOAP. The difference is not all REST api's provide a WADL. So what do you do if your api has no WADL, can you still use SoapUI?

One option you may want to consider is having you dev team take a look at adding [Swagger](http://swagger.io/getting-started/) in your service. There are other benefits but the most pertinent is SoapUI can automatically generate a WADL from the api documentation Swagger provides. 

If you don't have access to a WADL or Swagger, don't worry theres still hope. SoapUI supports manually configuring REST services and here's how...

## Setup

### Base Url
Now you'll need to set the base url for the service.
![test](NoWadl/ConfigureBaseUri)
![](./NoWadl/ConfigureBaseUri)
### Adding Resources

## Adding Methods

## Adding Parameters
Parameters can be added at the Resource, Method, or Request level. SoapUI uses a hierarchical approach to organizing parameters. Pratically speaking it means that parameters added at the Resource level will show up across all child requests of that resource. 

### Resource vs Request

If you are on a request node and select 

### Template
path= template

### Query String

### Header







