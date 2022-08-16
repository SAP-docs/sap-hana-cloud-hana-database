<!-- loioeaa4e37394ea4efba8148d595d025261 -->

# Defining the Data Model in SAP HANA Cloud

The application data model comprises all the database artifacts used to store and provision data for your application's back end and user interface.

As part of the process of defining the database persistence model for your application, you create database design-time artifacts such as tables and views, for example using SQL Data Definition Language \(DLL\). However, you can also create procedures and functions, for example, using SQLScript, which can be used to insert data into \(and remove data from\) tables or views. For database applications, the structure of the design-time resources should look something like the `db/` module illustrated in the following example:

> ### Sample Code:  
> ```
> <MyAppName>
> |- db/                              # Database deployment artifacts
> |  |- package.json                  # Database details/dependencies
> |  \- src/                          # Database artifacts
> |     |- .hdiconfig                 # HDI build plug-in configuration
> |     |- .hdinamespace              # HDI run-time name-space configuration
> |     |- data/                      # Database artifacts
> |     |  |- myTable.hdbtable        # SQL DDL table definition
> |     |  |- myView.hdbview          # SQL DDL view definition
> |     |  \- mySynonym.hdbsynonym    # SQL DDL synonym definition
> |     \- procedures                 # Database procedures, functions, ...
> |        |- myProc.hdbprocedure     # SQL DDL procedure
> |        \- myFunc.hdbfunction      # SQL DDL function
> |- web/                         
> |  |- xs-app.json               
> |  \- resources/                
> |- js/
> |  |- start.js              
> |  |- package.json           
> |  \- src/                    
> |- security/                  
> |  \- xs-security.json        
> \- mtad.yaml
> 
> ```

The following steps describe the high-level steps you perform when defining, deploying, and consuming the database persistence model for an application deployed to the SAP HANA Cloud run time.

1.  Define the data model.

    Set up the folder structure for the design-time representations of your database objects; this could include tables, data types, views, and so on. But it could also include other database artifacts, too, for example: your stored procedures, synonyms, sequences, scalar \(or table\) functions, and so on.

    In addition, you can also define the analytic model, for example, the calculation views and analytic privileges that are to be used to analyze the underlying data model and specify who \(or what\) is allowed access.

2.  Set up the SAP HANA Cloud HDI deployment infrastructure.

    This includes the following components:

    -   The HDI configuration

        Map the design-time database artifact type to the corresponding HDI build plug-in in the HDI configuration file \(`.hdiconfig`\). The mapping is determined by the file extension, for example, artifacts with the `.hdbtable` extension must be mapped to the HDI build plug-in `com.sap.hana.di.table`; artifacts with the `.hdbview` extension must be mapped to the `com.sap.hana.di.view`.

    -   Run-time name space configuration

        Define rules that determine how the run-time name space of the deployed database object is formed. For example, you can specify a base prefix for the run-time name space and, if desired, specify if the name of the folder containing the design-time artifact is reflected in the run-time name space that the deployed object uses.

        Alternatively, you can specify the use of freestyle names, for example, names that do not adhere to any name-space rules.


3.  Deploy the data model.

    Use the design-time representations of your database artifacts to generate the corresponding active objects in the database catalog.

4.  Consume the data model.

    Reference the deployed database objects from your application, for example, using OData services bound to UI elements.


**Related Information**  


[Design-Time Database Resources in SAP HANA Cloud](design-time-database-resources-in-sap-hana-cloud-72b60de.md "Design-time database resources reside in the database module of your multi-target application.")

[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

