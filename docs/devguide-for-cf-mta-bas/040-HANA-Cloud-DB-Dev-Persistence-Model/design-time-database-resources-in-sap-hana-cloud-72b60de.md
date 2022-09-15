<!-- loio72b60de8cd1945818259c7d978331a23 -->

# Design-Time Database Resources in SAP HANA Cloud

Design-time database resources reside in the database module of your multi-target application.

The design-time representations of you database resources must be collected in the database module of your multi-target application; the database module is a folder structure that you create, for example `/db/` that includes sub folder called `src/` in you place all the source files. For database applications, the structure of the design-time resources should look something like the following example:

> ### Sample Code:  
> Database module in a Multitarget Application
> 
> ```
> <MyAppName>
> 
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
> |- db/                                    # Database deployment artifacts
> |  |- package.json                        # Database details/dependencies
> |  \- src/                                # Database artifacts...
> |     |- .hdiconfig                       # HDI build plug-in configuration
> |     |- .hdinamespace                    # HDI run-time name-space configuration
> |     |- myTable.hdbtable                 # SDL DDL design-time view definition
> |     |- myView.hdbview                   # SQL DDL design-time table definition 
> |     |- myIndex.hdbindex                 # SDL DDL design-time index definition 
> |     |- data/                            # Data source files
> |        \- myData.csv                    # Table-data import sources (CSV)
> |     |- roles                            #
> |        |- myPriv.hdbstructuredprivilege # SQL DDL privilege definition
> |        \- myRole.hdbrole                # Role definition (JSON)
> ```

As illustrated in the example above, the `/db/` folder contains all your design-time database artifacts, for example: tables, views, procedures, sequences, calculation views. In addition to the design-time database artifacts, the database content must also include the following components:

-   `package.json`

    A file containing details of dependencies

-   `.hdiconfig`

    The HDI container configuration

-   `.hdinamespace`

    The run-time name-space configuration for the deployed objects


The HDI deployment tools deploy all database artifacts located in the `db/` folder to an HDI design-time container. At the same time, the HDI tools create the corresponding run-time container and populate the container with the specified catalog objects. The deployed objects can be referenced and consumed by your business applications.

> ### Caution:  
> If the deployment tools establish that a database run-time artifact has no corresponding design-time definition, the run-time artifact \(for example, a table\) is dropped from the catalog.



## Deployment Configuration Artifacts

The following files are mandatory for the database component of your deployment. One instance of each configuration artifact is required in the `db/src/` folder, and this instance applies to all sub-folders unless another instance exists in a sub folder:

-   `/db/src/.hdiconfig` 

    Used to bind the database artifacts you want to deploy \(determined by a file suffix, for example, `.hdbtable`\) with the appropriate build plug-in. For example, to deploy a table or view to an HDI container, you must ensure that the corresponding build plug-in is configured and, in addition, any other plug-ins required.

    ```json
    
    "hdbprocedure" : {
      "plugin_name"   : "com.sap.hana.di.procedure",
      "plugin_version": "4.0.0.0" },
    "hdbtable" : {
      "plugin_name"   : "com.sap.hana.di.table",
      "plugin_version": "4.0.0.0" }
    "hdbview" : { 
      "plugin_name" : "com.sap.hana.di.view", 
      "plugin_version": "4.0.0.0" }
    ```

-   `/db/src/.hdinamespace`

    Defines naming rules for the run-time objects which are created in the catalog when the application is deployed

    ```json
    {
      "name"      : "com.sap.hana.db.cds", 
      "subfolder" : "append"
    }
    
    ```


> ### Note:  
> For a name-space and build-plugin configuration to take effect, the name-space and build-plugin configuration file must be deployed - in the same way as any other design-time file.

**Related Information**  


[Creating Data Persistence Artifacts with SQL DDL](creating-data-persistence-artifacts-with-sql-ddl-a216fd8.md "You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.")

[Defining the Data Model in SAP HANA Cloud](defining-the-data-model-in-sap-hana-cloud-eaa4e37.md "The application data model comprises all the database artifacts used to store and provision data for your application's back end and user interface.")

[HDI Artifact and Build Plug-in Configuration](../110-HANA-Cloud-DB-Dev-HDI-Plugins/hdi-artifact-and-build-plug-in-configuration-a86453d.md "In SAP HANA Cloud HDI, design-time artifacts are distinguished by means of a unique file suffix that must be mapped to an HDI build plug-in.")

