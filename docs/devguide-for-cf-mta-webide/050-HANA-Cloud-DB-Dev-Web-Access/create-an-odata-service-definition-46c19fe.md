<!-- loio46c19fe41ab84cc4b66f84f76beb3402 -->

# Create an OData Service Definition

The OData service definition is a configuration file you use to specify which data \(for example, views or tables\) is exposed as an OData collection for analysis and display by client applications.



## Context

An OData service for your multitarget application is defined in a text file with the file extension `.xsodata`, for example, `OdataSrvDef.xsodata`. It must contain at least the entry service \{\}, which would generate an operational OData service with an empty service catalog and an empty metadata file.



## Procedure

1.  Create the file that will contain your OData service definition.

    An OData service definition is described in an `xsodata` artifact, for example, `myOdataService.xsodata`; the service definition should be placed in the `services/` folder of your multitarget application's OData project structure.

2.  Define the OData service.

    The OData service definition uses the OData Service Definition Language \(OSDL\), which includes a list of keywords that you specify in the OData service-definition file to enable important features.

    The following example shows a simple OData service definition exposing a simple table:

    ```
    service {
             "sample.odata::table" as "MyTable";
    }
    ```

    This service definition exposes a table defined in the file `sample.odata:table.hdbtable` and creates an EntitySet for this entity named `MyTable`. The specification of an alias is optional. If omitted, the default name of the EntitySet is the name of the repository object file, in this example, `table`.

3.  Save the OData service definition.


**Related Information**  


[Define the Data an OData Service Exposes](define-the-data-an-odata-service-exposes-aa09986.md "An OData service exposes data stored in database tables or views as OData collections for analysis and display by client applications. However, first of all, you need to ensure that the tables and views to expose as an OData collection actually exist.")

