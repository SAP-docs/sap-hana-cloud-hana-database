<!-- loio57920551c8ed4dea996c895ea05c6843 -->

# Defining OData v2 Services for JavaScript Applications

Create the OData service definitions consumed by your multitarget JavaScript application.

An OData v2 service definition for your multitarget JavaScript application is described in an “xsodata” artifact, for example, `myOdataService.xsodata`; the definition for your OData version 2 service should be placed in the `js/src/odata/services/` folder of your JavaScript project module. The following example shows two OData services \(`srv1.xsodata` and `srvN.xsodata`\) consumed by a JavaScript application.

> ### Caution:  
> The `XSODATA` infrastructure for OData services based on OData version 2 will no longer be extended or improved. Please also bear in mind that although the `XSODATA` solution supports SAP HANA as a Service, it does **not** support SAP HANA Cloud services, as described in SAP note: [3013788](https://me.sap.com/notes/3013788). If you are developing a new OData service, it is recommended to use the SAP Cloud Application Programming Model \(CAP\). For more information, see the related links below.



## Example

> ### Sample Code:  
> ```
> JavaScript-AppName
> |- db/                         
> |  |- package.json             
> |  |- src/                     
> |     |- .hdiconfig            
> |     \- mytable.hdbtable         
> |
> |- web/                        
> |  |- xs-app.json
> |  |- package.json               
> |  \- resources/ 
> |- js/                          
> |  |- start.js                 
> |  |- package.json             
> |  \- src/                     
> |     \- odata/                   # XSOData v2 service resources
> |        |- resources/            # XSOData v2 service resources
> |        \- services/             # XSOData v2 services
> |           | - srv1.xsodata      # XSOData v2 service definition
> |           \ - srvN.xsodata      # XSOData v2 service definition
> |- security/                   
> |  \- xs-security.json         
> \- mta.yaml  
> 
> ```



## Exposing a Database Table

You can expose the database table `db/src/mytable.hdbtable` as `'My Entity Set'` as follows:

1.  Create the project structure \(as shown in the example above\) in your local system.
2.  Create the OData service definition file `myservice.xsodata`.
3.  Expose the table as EntitySet in the `xsodata` file:

    > ### Sample Code:  
    > ```
    > service {
    > "mytable" as "MyEntitySet";
    > }
    > ```

4.  Deploy your application with the client deployment tool.
5.  Call your service from the client UI, for example, a Web browser:

    You can call your OData service with: the following URI

    <code>http://<i class="varname">&lt;myServer&gt;</i>:<i class="varname">&lt;port&gt;</i>/odata/services/<i class="varname">&lt;myService&gt;</i>.xsodata</code>

    You can requests the metadata of the OData service using the following URI

    <code>http://<i class="varname">&lt;myServer&gt;</i>:<i class="varname">&lt;port&gt;</i>/odata/services/<i class="varname">&lt;myService&gt;</i>.xsodata/$metadata</code>


> ### Restriction:  
> OData supports both the ATOM and JSON formats in request and response payloads. However, the Node.js module only support JSON. To specify JSON as the payload format, you can either add the following system-query option to the request “`$format=json`” or add the following request header “`Accept:json`”.

**Related Information**  


[Define the Data an OData Service Exposes](define-the-data-an-odata-service-exposes-aa09986.md "An OData service exposes data stored in database tables or views as OData collections for analysis and display by client applications. However, first of all, you need to ensure that the tables and views to expose as an OData collection actually exist.")

[Create an OData Service Definition](create-an-odata-service-definition-46c19fe.md "The OData service definition is a configuration file you use to specify which data (for example, views or tables) is exposed as an OData collection for analysis and display by client applications.")

[Working with the SAP Cloud Application Programming Model](../020-HANA-Cloud-DB-Dev-Get-Started/working-with-the-sap-cloud-application-programming-model-166f4fb.md "Create a business application using the SAP Cloud Application Programming model.")

[SAP Note 3013788](https://me.sap.com/notes/3013788 "XSODATA not supported in SAP HANA Cloud Service")

