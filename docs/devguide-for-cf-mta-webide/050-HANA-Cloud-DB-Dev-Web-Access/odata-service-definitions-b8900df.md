<!-- loiob8900dfa26ea48bd9a6596612ac122ad -->

# OData Service Definitions

The OData service definition defines what data to expose with OData, how, and to whom. Data exposed as an OData collection is available for analysis and display by client applications, for example, a browser that uses functions provided by an OData client library running on the client system.

To expose information to applications by means of OData, you must define database views that provide the data with the required granularity. Then you create an OData service definition, which is a file you use to specify which database views or tables are exposed as OData collections.

> ### Note:  
> An XSOdata service supports OData version 2.0, which you can use to send OData queries \(for example, using the HTTP `GET` method\). Language encoding is restricted to UTF-8.

An OData service for your multitarget application is defined in a text file with the file suffix `.xsodata`, for example, `OdataSrvDef.xsodata`. The file must contain at least the entry `service {}`, which would generate a completely operational OData service with an empty service catalog and an empty metadata file. However, usually you use the service definition to expose objects in the database catalog, for example: tables, SQL views, or calculation rules.

In the OData service-definition file, you can use the following ways to name the SAP HANA objects you want to expose by OData:

> ### Note:  
> The syntax to use in the OData service-definition file to reference objects is dictated by the object type, for example, database catalog \(runtime\).

-   **Database objects**

    Expose an object using the object's database catalog \(run-time\) name. The support for database objects is mainly intended for existing or replicated objects that do not have a repository design-time representation. The following example shows how to include a reference to a table in an OData service definition using the table's *runtime* name.

    ```
    service {
        "myTable" as "MyTable";
    }
    ```


By default, all entity sets and associations in an OData service are writeable, that is they can be modified with a CREATE, UPDATE, or DELETE requests. However, you can prevent the execution of a modification request by setting the appropriate keyword \(*create*, *update*, or *delete*\) with the `forbidden` option in the OData service definition. The following example of an OData service definition shows how to prevent any modification to the table `myTable` that is exposed by the OData service. Any attempt to make a modification to the indicated table using a CREATE, UPDATE, or DELETE request results in the HTTP response status ***403 FORBIDDEN***.

```
service {
     “sap.test::myTable”
          create forbidden
          update forbidden
          delete forbidden;
}

```

For CREATE requests, for example, to add a new entry to a table exposed by an OData service, you must specify an explicit key \(not a generated key\); the key must be included in the payload of the CREATE request. For UPDATE and DELETE requests, you do not need to specify the key explicitly \(and if you do, it will be ignored\); the key is already known, since it is essential to specify which entry in the table must be modified with the UPDATE or DELETE request.

> ### Note:  
> Without any support for IN/OUT table parameters in SQLScript, it is not possible to use a sequence to create an entry in a table exposed by an OData service. However, you can use JavaScript exits to update a table with a generated value.

