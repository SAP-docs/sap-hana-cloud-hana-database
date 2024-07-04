<!-- loio879ce231b09240d493304e0a591456fc -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Table with SQL Data Definition Language

Define a design-time database **table** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio879ce231b09240d493304e0a591456fc__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a dev space and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multi-target application \(or just the database module\) is deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



## Context

In the SAP HANA database, as in other relational databases, a table contains a set of data elements that are organized using columns and rows. SAP HANA Deployment Infrastructure \(HDI\) enables you to use the SQL DDL syntax to create a database table as a design-time file. Building or deploying the database module that contains the SQL DDL table creates the corresponding table in the corresponding schema.

During the build process, the `.hdbtable` plug-in is called to transform a design-time table resource into an SQL table database object. The file formats use a DDL-style syntax which is equivalent to the syntax required in the corresponding SAP HANA SQL statement `CREATE TABLE`, but without the leading “`CREATE`”, as illustrated in the examples below. Specifying the table type is mandatory, and the type of table you can define is limited to ROW and COLUMN.

A table must be self-contained and cannot reference another table. As result, it is not possible to define a table by using another table \(for example, `TABLE A LIKE B`\), and you cannot define a table based on a query, for example, `TABLE A AS SELECT [...] FROM B`.

> ### Note:  
> The `.hdbtable` plug-in used to create the catalog table object does not provide any data migration. An already deployed version of the table will be dropped on deployment.

To create a design-time SQL DDL table-definition file, perform the following steps:



## Procedure

1.  Start SAP Business Application Studio.

2.  Open the application project to which you want to add your SQL DDL table.

3.  Create the table-definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL table-definition file and perform the following steps:

    1.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

            > ### Tip:  
            > By default, SAP Business Application Studio only provides "compact" menus and options, which are initially hidden and displayed when you choose <span class="SAP-icons-V5"></span> \(Menus\)in the Views pane. If you want to display the traditional, horizontal *Menu* bar at the top of the work space, choose :gear:and then *Settings*, search for "*Menu*", and change the value of *Window: Menu Bar Visibility* from *compact* to *classic* in the drop-down list provided.


    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new artifact.

    5.  Select the database artifact type, for example, table.

        In the *Artifact Type* box, type `hdbt`, and choose *Table \(hdbtable\)* from the list that appears.

    6.  Name the file *PurchaseOrderHeader*.

        The appropriate file suffix \(`.hdbtable`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL table-definition artifacts have the file extension `.hdbtable`, for example, `PurchaseOrderHeader.hdbtable`

    7.  Save the changes and create the new database artifact; choose *Create*.


4.  Define the structure of the SQL DDL table \(`PurchaseOrderHeader`\).

    If the new table-definition file is not automatically displayed by the file-creation wizard, double-click the table-definition file you created in the previous step, for example, `PurchaseOrderItem.hdbtable`, and add the SQL DDL code that defines the table to the file:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Code Syntax:  
    > `db/src/PurchaseOrderHeader.hdbtable`
    > 
    > ```
    > COLUMN TABLE "PurchaseOrder.Header" (
    >       "PURCHASEORDERID" INTEGER GENERATED BY DEFAULT AS IDENTITY (NO CYCLE NO CACHE NO MINVALUE START WITH 200000000 INCREMENT BY 1 MAXVALUE 2999999999) NOT NULL COMMENT 'Purchase Order ID',
    >       "HISTORY.CREATEDBY" NVARCHAR(10) COMMENT 'Created By',
    >       "HISTORY.CREATEDAT" DATE COMMENT 'Created Date',
    >       "HISTORY.CHANGEDBY" NVARCHAR(10) COMMENT 'Changed By',
    >       "HISTORY.CHANGEDAT" DATE COMMENT 'Change Date',
    >       "NOTEID" NVARCHAR(10) COMMENT 'Notes',
    >       "PARTNER" NVARCHAR(10) COMMENT 'Supplier',
    >       "CURRENCY" NVARCHAR(5) COMMENT 'Currency',
    >       "GROSSAMOUNT" DECIMAL(15,2) COMMENT 'Gross Amount',
    >       "NETAMOUNT" DECIMAL(15,2) COMMENT 'Net Amount',
    >       "TAXAMOUNT" DECIMAL(15,2) COMMENT 'Tax Amount',
    >       "LIFECYCLESTATUS" NVARCHAR(1) COMMENT 'Lifecycle Status',
    >       "APPROVALSTATUS" NVARCHAR(1) COMMENT 'Approval Status',
    >       "CONFIRMSTATUS" NVARCHAR(1) COMMENT 'Confirmation Status',
    >       "ORDERINGSTATUS" NVARCHAR(1) COMMENT 'Ordering Status',
    >       "INVOICINGSTATUS" NVARCHAR(1) COMMENT 'Invoicing Status',
    >       PRIMARY KEY ("PURCHASEORDERID")) 
    >       COMMENT 'Purchase Order Header'
    >       WITH ASSOCIATIONS( JOIN "PurchaseOrder.Item" AS "ITEMS" ON "PURCHASEORDERID" = "PURCHASEORDERID") 
    >       UNLOAD PRIORITY 5 AUTO MERGE
    > ```

    > ### Note:  
    > `"PurchaseOrder.Item"` defined in `PurchaseOrderItem.hdbtable`, which we create in the next step.

5.  Save the SQL DDL table-definition file.

    Saving the definition persists the file in your local workspace; it does not create any objects in the database catalog.

6.  Create and define a second design-time table `PurchaseOrderItem.hdbtable` using SQL DDL.

    The purchase-order **items** table is associated with the purchase-order **header** table to provide a basis for an SQL view that you can define in subsequent task.

    1.  Open the command palette and choose *SAP HANA: Create SAP HANA Database Artifact*.

    2.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    3.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new artifact.

    4.  Select the database artifact **type**. In the selection box, type `hdbt` and choose *hdbtable* in the list that appears.

    5.  Name the file *PurchaseOrderItem*.

        > ### Tip:  
        > The appropriate file suffix \(`.hdbtable`\) is appended to the name by the Wizard.

        The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL table-definition artifacts have the file extension `.hdbtable`, for example, `PurchaseOrderItem.hdbtable`.

    6.  Define the structure of the SQL DDL table `PurchaseOrderItem`.

        If the new table-definition file is not automatically displayed by the file-creation wizard, double-click the table-definition file you created in the previous step and add the SQL DDL code that defines the table to the file:

        > ### Note:  
        > The following code example is provided for illustration purposes only.

        `db/src/PurchaseOrderItem.hdbtable`

        ```sql
        COLUMN TABLE "PurchaseOrder.Item" (
              "POHeader.PURCHASEORDERID" INTEGER NOT NULL COMMENT 'Purchase Order ID',
              "PRODUCT" NVARCHAR(10) NOT NULL COMMENT 'Product ID',
              "NOTEID" NVARCHAR(10) COMMENT 'Notes',
              "CURRENCY" NVARCHAR(5) COMMENT 'Currency',
              "GROSSAMOUNT" DECIMAL(15,2) COMMENT 'Gross Amount',
              "NETAMOUNT" DECIMAL(15,2) COMMENT 'Net Amount',
              "TAXAMOUNT" DECIMAL(15,2) COMMENT 'Tax Amount',
              "QUANTITY" DECIMAL(13,3) COMMENT 'Quantity',
              "QUANTITYUNIT" NVARCHAR(3) COMMENT 'Quantity Unit',
              "DELIVERYDATE" DATE COMMENT 'Delivery Date',
              PRIMARY KEY ("POHeader.PURCHASEORDERID","PRODUCT")) 
              COMMENT 'Purchase Order Item'	 
              WITH ASSOCIATIONS( JOIN "PurchaseOrder.Header" AS "POHeader" ON "POHeader"."PURCHASEORDERID" = "POHeader.PURCHASEORDERID") 
              UNLOAD PRIORITY 5 AUTO MERGE 
        ```

        > ### Note:  
        > This code example defines an association with a second table, `"PurchaseOrder.Header"` defined in `PurchaseOrderHeader.hdbtable`, which we created in the previous step. These two tables are the basis for an SQL view that you can create in a subsequent task.


7.  Build and deploy the database module.

    To activate the new entity definition and generate a corresponding table in the catalog, use the *Build* or *Deploy* feature.

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

        Bear in mind that a mismatch between the installed SAP HANA version and the SAP HANA version specified in the `.hdbconfig` file \(for example, with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.

        > ### Tip:  
        > Details of each deployment operation are written to a dedicated log file. To ensure that the log file does not retain any information about previous deployments, enable the option *Clear the deployment log before starting a new deployment*, which you can find in :gear:. Choose *Settings* \> *SAP HANA Project Explorer* \> *Deploy: Auto clean deployment log*.


8.  Check that the new tables have been successfully created in the catalog.

    You can use the *Database Explorer* to view the activated objects in the run-time catalog.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \([Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

        You can filter by name the databases displayed in the *DATABASE LIST*. For example, choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and choose *OK* press or [Enter\]. To reset the filter, press [Escape\].

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

        You can filter by name the database objects displayed in the *CATALOG BROWSER*. Choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Escape\].

    3.  Choose *Tables*.

    4.  Check the two tables are listed in the results pane.

    5.  Select each table to display the contents in the details pane.



**Related Information**  


[Table Syntax (.hdbtable in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_3_QRC/en-US/453d48e28f6747799546236b4b432e58.html "Transforms a design-time table resource into a table database object.") :arrow_upper_right:

[Creating Data Persistence Artifacts with SQL DDL](creating-data-persistence-artifacts-with-sql-ddl-a216fd8.md "You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.")

[Load Data into a Database Table with the "hdbtabledata" Artifact](load-data-into-a-database-table-with-the-hdbtabledata-artifact-91b08cc.md "Use an hdbtabledata artifact to load data external data into an existing database table.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

