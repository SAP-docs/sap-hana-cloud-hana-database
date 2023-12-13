<!-- loio1e5e2c619d214508958a192f2241a2e2 -->

# Creating Procedures and Functions in SAP HANA Cloud

Database procedures and functions can be used to help manage the underlying data model.

As part of the process of defining the database persistence model for your application, you create database design-time artifacts such as tables and views, for example using SAP HANA Cloud DDL. However, you can also create procedures and table or scalar functions, for example, using SQLScript; procedures can be used to insert data into \(and remove data from\) tables or views.

Each design-time database artifact has a distinct file extension, for example, `myProcedure.hdbprocedure`, `mySynonym.hdbsynonym`, `myScalarFunction.hdbfunction`; the file extension determines which HDI plug-in is used to generate the corresponding catalog objects.

> ### Tip:  
> Scalar and table functions have the same file extension `.hdbfunction`. The HDI uses the same plug-in to generate the catalog object.

For easier navigation and maintenance, it is recommended to place your procedures and functions in a separate folder in the application's database \(`db/`\) module, as illustrated in the following example:

> ### Sample Code:  
> ```
> <MyAppName>
> |- db/                              # Database deployment artifacts
> |  |- package.json                  # Database details/dependencies
> |  |- src/                          # Database artifacts: tables, views, etc.
> |     |- .hdiconfig                 # HDI build plug-in configuration
> |     |- .hdinamespace              # HDI run-time name-space configuration
> |     |- data/                      # 
> |     |  |- myTable.hdbtable        # HANA DDL table definition
> |     |  \- myView.hdbview          # HANA DDL view definition
> |     |  
> |     |- procedures                 # Database procedures, functions, ...
> |        |- myProc.hdbprocedure     # Database procedure
> |        \- myFunc.hdbfunction      # Database function                        
> \- mtad.yaml
> 
> ```

**Related Information**  


[Create a Database Procedure in SAP HANA Cloud](create-a-database-procedure-in-sap-hana-cloud-81e83fb.md "Create, edit, and deploy procedures.")

[Create a Database Function in SAP HANA Cloud](create-a-database-function-in-sap-hana-cloud-e3093ea.md "Add a database function to your data model.")

[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

