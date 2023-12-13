<!-- loio6694cbdaef16415bb2a35effe5dc5cd1 -->

# Create the Underlying Data Artifacts for a Procedure

Create the data objects that you plan to use and modify with your functions and procedures.



## Prerequisites

-   You have access to a running SAP HANA Cloud system where the Cloud Foundry run time is installed and configured

-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development space and a multitarget application \(MTA\) project.

> ### Caution:  
> The code examples included in this document are sometimes either syntactically incomplete or include additional definitions that you might not always need. As a general rule, code examples are intended for illustration purposes only.



## Context

Database procedures and functions are used to automate actions that need to be regularly performed on underlying data objects, such as tables or views. In this task, we show you how to create some tables, views, and data types that can then be used by the database procedures and functions you create in subsequent tasks. You also create a sequence to enable you to add items to a table in the correct order, and upload some initial data into the new tables you create.



## Procedure

1.  Start SAP Business Application Studio.

2.  Display the application project to which you want to add a database procedure.

    An application is created within a context of a project. If you do not already have a project, there are a number of ways to create one, for example: by importing it, cloning it, or creating a new one from scratch.

    1.  Start the *Create Project from Template* Wizard.

        -   Open the command palette:

            Choose *View* \> *Command Palette...*

        -   In the command palette, type `Project` and choose *Create Project from Template*.

        > ### Tip:  
        > Alternatively, in the *Welcome* tab, choose *Start from Template* \> *Create a new project*.

    2.  In the *New Project from Template* Wizard, choose *SAP HANA Database Project* and then choose *Start*.

    3.  In the *Add Basic Information* pane, type the name of the new project \(`myapp` \) and choose *Next*.

    4.  In the *Set Basic Properties* pane, accept the default settings and choose *Next*.

    5.  In the *Set Database Information* pane, use the default settings and choose *Next*.

        You can use the following default settings:

        -   *Namespace* \(empty\)

        -   *Schema Name* \(empty\)

        -   *SAP HANA Database Version \** \(HANA Cloud\)

        -   *Bind the database module to a Cloud Foundry service instance?* \(Yes\)


    6.  In the *Bind to HDI Container Service* pane, provide the requested information.

        It is necessary to provide the credentials required to log on to the Cloud Foundry end point that provides the service instance to which you want to bind the database module of your new application project. After you log on to Cloud Foundry, you can choose the target organization, space, and service instance.

        -   *Enter e-mail address* \(Type the e-mail address of a registered Cloud Foundry user\)
        -   *Enter Password* \(Type the Cloud Foundry user's password\)

            Press [Enter\] or click *Login -\>* to connect to Cloud Foundry.

            > ### Note:  
            > If two-factor authentication \(2FA\) is configured in your landscape, you might need to provide an additional single-use token.


        After you log in to Cloud Foundry, use the following options to specify the target Cloud Foundry space where the service instance is running:

        -   *Choose Cloud Foundry Org \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Space \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Service \** \(Create a new service instance\)
        -   *Please enter a unique and non-existing service-instance name\** \(default is "*<ProjectName\>*-hdidb-ws-*<WorkspaceName\>*"\)

            > ### Note:  
            > It is recommended to accept the default service-instance name displayed, but you can also choose an existing service instance from the drop-down list provided. However, binding to an existing service can lead to problems caused by the undeployment \(removal\) of existing files from a previous deployment.


        Choose *Finish* to generate the new project called *FlightReservation* in the chosen Cloud Foundry organization and space.


3.  Create a new application folder for your data artifacts.

    In the `db/` module of your application project, create a folder named `data` in the `src/` folder, for example, `myapp/db/src/data`. You use this folder to store your tables, types, views, sequences, and so on.

4.  Add some simple database tables to the database module.

    Use the following code samples to add the tables “Header” and “Item” to your application's database module:

    1.  Create a new table artifact called `Header.hdbtable` and add the following code to it:

        > ### Sample Code:  
        > `myapp/db/src/data/PurchaseOrderHeader.hdbtable`
        > 
        > ```
        > COLUMN TABLE "PurchaseOrderHeader" (
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
        >       WITH ASSOCIATIONS( JOIN "PurchaseOrderItem" AS "ITEMS" ON "PURCHASEORDERID" = "PURCHASEORDERID") 
        >       UNLOAD PRIORITY 5 AUTO MERGE
        > 
        > ```

    2.  Create a new table artifact called `Item.hdbtable` and add the following code to it:

        > ### Sample Code:  
        > `myapp/db/src/data/PurchaseOrderItem.hdbtable`
        > 
        > ```
        > COLUMN TABLE "PurchaseOrderItem" (
        >       "PURCHASEORDERID" INTEGER NOT NULL COMMENT 'Purchase Order ID',
        >       "PURCHASEORDERITEM" INTEGER NOT NULL COMMENT 'Purchase Order Item',
        >       "PRODUCT" NVARCHAR(10) NOT NULL COMMENT 'Product ID',
        >       "NOTEID" NVARCHAR(10) COMMENT 'Notes',
        >       "CURRENCY" NVARCHAR(5) COMMENT 'Currency',
        >       "GROSSAMOUNT" DECIMAL(15,2) COMMENT 'Gross Amount',
        >       "NETAMOUNT" DECIMAL(15,2) COMMENT 'Net Amount',
        >       "TAXAMOUNT" DECIMAL(15,2) COMMENT 'Tax Amount',
        >       "QUANTITY" DECIMAL(13,3) COMMENT 'Quantity',
        >       "QUANTITYUNIT" NVARCHAR(3) COMMENT 'Quantity Unit',
        >       "DELIVERYDATE" DATE COMMENT 'Delivery Date',
        >       PRIMARY KEY ("PURCHASEORDERID","PURCHASEORDERITEM")) 
        >       COMMENT 'Purchase Order Item'	 
        >       WITH ASSOCIATIONS( JOIN "PurchaseOrderHeader" AS "POHeader" ON "POHeader"."PURCHASEORDERID" = "PURCHASEORDERID") 
        >       UNLOAD PRIORITY 5 AUTO MERGE 
        > ```


5.  Add an SQL view to the database model.

    Enter the SQL DDL code for the simple view “ItemView”, as illustrated in the following example:

    > ### Sample Code:  
    > `myapp/db/src/data/PurchaseOrderItemView.hdbview`
    > 
    > ```
    > VIEW "PurchaseOrderItemView" COMMENT 'Purchase Order Item View' ( 
    >      "PurchaseOrderItemId",
    >      "ItemPos",
    >      "ProductID",
    >      "CurrencyCode",
    >      "Amount",
    >      "NetAmount",
    >      "TaxAmount",
    >      "Quantity",
    >      "QuantityUnit",
    >      "DeliveryDate1"
    >      ) AS SELECT
    >      "Item_$0"."PURCHASEORDERID" AS "PurchaseOrderItemId",
    >      "Item_$0"."PURCHASEORDERITEM" AS "ItemPos",
    >      "Item_$0"."PRODUCT" AS "ProductID",
    >      "Item_$0"."CURRENCY" AS "CurrencyCode",
    >      "Item_$0"."GROSSAMOUNT" AS "Amount",
    >      "Item_$0"."NETAMOUNT" AS "NetAmount",
    >      "Item_$0"."TAXAMOUNT" AS "TaxAmount",
    >      "Item_$0"."QUANTITY" AS "Quantity",
    >      "Item_$0"."QUANTITYUNIT" AS "QuantityUnit",
    >      "Item_$0"."DELIVERYDATE" AS "DeliveryDate1"
    > FROM "PurchaseOrderItem" AS "Item_$0" 
    > WITH READ ONLY STRUCTURED PRIVILEGE CHECK
    > ```

6.  Create a new database sequence.

    The tables “Header” and “Item” use a unique order id number as the primary key. As a result, you need a sequence to have an auto incrementing unique id generated for each time new data is inserted into the tables.

    1.  Right-click the folder `myapp/db/src/data` and choose *New* \> *File* in the context menu.

    2.  Name the new file artifact `orderId.hdbsequence`.

        Enter the following code to create a non-cycling sequence within your schema starting from 200000000 and ending with 299999999. Make the sequence dependent upon the header table with the full package id on the front of the header table name.

        > ### Sample Code:  
        > `myapp/db/src/data/orderId.hdbsequence`
        > 
        > ```
        > SEQUENCE "orderId" 
        > INCREMENT BY 1 
        > START WITH 200000000 
        > MINVALUE 1 
        > MAXVALUE 2999999999 
        > NO CYCLE 
        > RESET BY SELECT IFNULL(MAX(PURCHASEORDERID), 0)+1 
        > FROM "PurchaseOrderHeader" 
        > ```

    3.  Save the sequence file.


7.  Load some initial data into the new tables `Header` and `Item`.

    In HDI, you can import data from a comma-separated-value file \(CSV\) into a database table; you need the following design-time artifacts:

    -   CSV file \(`myData.csv`\)

        Holds the data you want to load into the database table.

    -   Table definition file \(`myTargetTable.hdbtabledata`\)

        Specifies the target table for the data in the source `.csv` file to be uploaded.


    1.  Create the `.hdbtabledata` file.

        In the database module's `data/` folder, create a file called `Purchase.hdbtabledata` and add the following code:

        > ### Sample Code:  
        > `db/src/data/Purchase.hdbtabledata`
        > 
        > ```
        > {
        >     "format_version" : 1,
        >     "imports" : [
        >         {
        >     "target_table" : "PurchaseOrderHeader",
        >     "source_data" : {
        >         "data_type" : "CSV",
        >         "file_name" : "header.csv",
        >         "has_header" : false,
        >         "dialect" : "HANA",
        >         "type_config" : {
        >         "delimiter" : ","
        >         }
        >     },
        >     "import_settings" : {
        >     "import_columns" : [
        >         "PURCHASEORDERID",
        >         "NOTEID",
        >         "PARTNER",
        >         "CURRENCY",
        >         "GROSSAMOUNT",
        >         "NETAMOUNT",
        >         "TAXAMOUNT",
        >         "LIFECYCLESTATUS",
        >         "APPROVALSTATUS",
        >         "CONFIRMSTATUS",
        >         "ORDERINGSTATUS",
        >         "INVOICINGSTATUS"]
        >     },
        >     "column_mappings" : {
        >         "PURCHASEORDERID" : 1,
        >         "NOTEID" : 6,
        >         "PARTNER" : 7,
        >         "CURRENCY" : 8,
        >         "GROSSAMOUNT" : 9,
        >         "NETAMOUNT" : 10,
        >         "TAXAMOUNT" : 11,
        >         "LIFECYCLESTATUS" : 12,
        >         "APPROVALSTATUS" : 13,
        >         "CONFIRMSTATUS" : 14,
        >         "ORDERINGSTATUS" : 15,
        >         "INVOICINGSTATUS" : 16
        >         }
        >     },
        >     {
        >     "target_table" : "PurchaseOrderItem",
        >     "source_data" : {
        >         "data_type" : "CSV",
        >         "file_name" : "item.csv",
        >         "has_header" : false,
        >         "dialect" : "HANA",
        >         "type_config" : {
        >         "delimiter" : ","
        >         }
        >     },
        >     "import_settings" : {
        >     "import_columns" : [
        >         "PURCHASEORDERID",
        >         "PURCHASEORDERITEM",
        >         "PRODUCT",
        >         "NOTEID",
        >         "CURRENCY",
        >         "GROSSAMOUNT",
        >         "NETAMOUNT",
        >         "TAXAMOUNT",
        >         "QUANTITY",
        >         "QUANTITYUNIT" ]
        >         },
        >     "column_mappings" : {
        >         "PURCHASEORDERID" : 1,
        >         "PURCHASEORDERITEM" : 2,
        >         "PRODUCT" : 3,
        >         "NOTEID" : 4,
        >         "CURRENCY" : 5,
        >         "GROSSAMOUNT" : 6,
        >         "NETAMOUNT" : 7,
        >         "TAXAMOUNT" : 8,
        >         "QUANTITY" : 9,
        >         "QUANTITYUNIT" : 10
        >         }
        >     }]
        > }
        > ```

    2.  Create the `header.csv` file.

        In the database module's `data/` folder, create a file called `header.csv` and add the following content and save the file:

        > ### Sample Code:  
        > `header.csv`
        > 
        > ```
        > 0500000000,0000000033,20120101,0000000033,20120101,9000000001,0100000000,EUR,13224.47,11113,2111.47,N,I,I,I,I
        > 0500000001,0000000033,20120102,0000000033,20120102,9000000001,0100000002,EUR,12493.73,10498.94,1994.79,N,I,I,I,I
        > 
        > ```

    3.  Create the `item.csv` file.

        In the database module's `data/` folder, create a file called `item.csv` and add the following content and save the file:

        > ### Sample Code:  
        > `item.csv`
        > 
        > ```
        > 0500000000,0000000010,HT-1000,,EUR,1137.64,956,181.64,1,EA,20121204
        > 0500000000,0000000020,HT-1091,,EUR,61.88,52,9.88,2,EA,20121204
        > 0500000000,0000000030,HT-6100,,EUR,1116.22,938,178.22,2,EA,20121204
        > 0500000000,0000000040,HT-1000,,EUR,2275.28,1912,363.28,2,EA,20121204
        > 0500000000,0000000050,HT-1091,,EUR,92.82,78,14.82,3,EA,20121204
        > 0500000000,0000000060,HT-6100,,EUR,1116.22,938,178.22,2,EA,20121204
        > 0500000000,0000000070,HT-1000,,EUR,2275.28,1912,363.28,2,EA,20121204
        > 0500000000,0000000080,HT-1091,,EUR,61.88,52,9.88,2,EA,20121204
        > 0500000000,0000000090,HT-6100,,EUR,1674.33,1407,267.33,3,EA,20121204
        > 0500000000,0000000100,HT-1000,,EUR,3412.92,2868,544.92,3,EA,20121204
        > 0500000001,0000000010,HT-1100,,USD,213.96,179.8,34.16,2,EA,20121204
        > 0500000001,0000000020,HT-2026,,USD,35.69,29.99,5.7,1,EA,20121204
        > 0500000001,0000000030,HT-1002,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000040,HT-1100,,USD,213.96,179.8,34.16,2,EA,20121204
        > 0500000001,0000000050,HT-2026,,USD,71.38,59.98,11.4,2,EA,20121204
        > 0500000001,0000000060,HT-1002,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000070,HT-1100,,USD,320.94,269.7,51.24,3,EA,20121204
        > 0500000001,0000000080,HT-2026,,USD,107.06,89.97,17.09,3,EA,20121204
        > 0500000001,0000000090,HT-1002,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000100,HT-1100,,USD,320.94,269.7,51.24,3,EA,20121204
        > 
        > ```


8.  Create a new database synonym.

    A database synonym is required to enable access to any table or view outside of our application's container. In this step, to enable us to access the `DUMMY` view, you create **two** files: an synonym artifact \(`.hdbsynonym`\).

    In the database module's `data/` folder, create a file called `general.hdbsynonym`, add the following content, and save the file:

    > ### Sample Code:  
    > `general.hdbsynonym`
    > 
    > ```
    > { 
    >   "DUMMY" : { 
    >      "target" : { 
    >               "schema" : "SYS", 
    >               "object" : "DUMMY" 
    >      }
    >   } 
    > }
    > ```

9.  Create a new structured privilege.

    The structured privilege is the logical successor to the analytic privilege; it enables us to perform instance filtering for the SQL view `ItemView` that we created earlier.

    1.  In the database module's `data` folder, create a new subfolder named `roles`, for example, `db/src/roles`.


    In the database module's `db/src/roles` folder, create a file called `PurchaseOrder.hdbstructuredprivilege`, add the following content, and save the file:

    > ### Sample Code:  
    > `PurchaseOrder.hdbstructuredprivilege`
    > 
    > ```
    > STRUCTURED PRIVILEGE 
    >   "PO_VIEW_PRIVILEGE" 
    >   FOR SELECT ON 
    >   "PurchaseOrderItemView" 
    > WHERE "CurrencyCode" = 'EUR'
    > ```

10. Create a new role for the structured privilege.

    The technical user bound to the application's HDI container enables access to the HDI database objects from XS advanced. If you want to enable access by other database users \(for example, external reporting tools\) you must create a database role.

    In the database module's `src/roles` folder, create a file called `dev007.hdbrole`, add the following content, and save the file:

    > ### Sample Code:  
    > `dev007.hdbrole`
    > 
    > ```
    > {
    >     "role":{
    >             "name": "dev007", 
    >             "object_privileges":[ 
    >             { 
    >             "name": "PurchaseOrderHeader", 
    >             "type": "TABLE", 
    >             "privileges": [ "SELECT" ] 
    >             }, 
    >             { 
    >             "name": "PurchaseOrderItem", 
    >             "type": "TABLE", 
    >             "privileges": [ "SELECT" ] 
    >             },  
    >             { 
    >             "name": "PurchaseOrderItemView", 
    >             "type": "VIEW", 
    >             "privileges": [ "SELECT" ] 
    >             } 
    >             ], 
    >             "schema_analytic_privileges": [ 
    >             { 
    >             "privileges":[ "PO_VIEW_PRIVILEGE" ] 
    >             } 
    >           ] 
    >      } 
    >   }
    > ```

11. Check that the required plug-ins are available to build and deploy the database objects defined in this task.

    In HDI, a file suffix \(for example, `.hdbtable`\) is linked to a specific plug-in, which is used to generate the corresponding catalog object from a design-time artifact.

    The container-configuration file `db/src/.hdiconfig` must contain \(at least\) the following entries:

    > ### Note:  
    > The version number of the plug-in is optional in SAP HANA Cloud.

    > ### Sample Code:  
    > `db/src/.hdiconfig`
    > 
    > ```
    > "hdbsequence": {
    >      "plugin_name": "com.sap.hana.di.sequence"
    >      },
    > "hdbtable" : { 
    >      "plugin_name" : "com.sap.hana.di.table"
    >      }, 
    > "hdbview" : { 
    >      "plugin_name" : "com.sap.hana.di.view"
    >      }, 
    > "csv" : { 
    >      "plugin_name" : "com.sap.hana.di.tabledata.source"
    >      }, 
    > "hdbtabledata" : { 
    >      "plugin_name" : "com.sap.hana.di.tabledata"
    >      }, 
    > "hdbfunction" : { 
    >      "plugin_name" : "com.sap.hana.di.hdbfunction"
    >      },
    > "hdbstructuredprivilege" : {
    >      "plugin_name" : "com.sap.hana.di.structuredprivilege"
    >      },
    > "hdbsynonym" : { 
    >      "plugin_name" : "com.sap.hana.di.hdbsynonym"
    >      },
    > "hdbrole" : { 
    >      "plugin_name" : "com.sap.hana.di.role"
    >      }, 
    > "hdbroleconfig" : { 
    >      "plugin_name" : "com.sap.hana.di.role.config"
    >      }
    > 
    > ```

    > ### Tip:  
    > By default, the `.hdiconfig` configuration file is hidden. To display it, choose *View* \> *Show Hidden Files*in the menu bar.

12. Build the HDB module `db`.

    Building a database module activates the data model and creates the corresponding objects in the database catalog for each artifact defined in the SQL DDL files. In this case, the build creates two tables named “Header” and “Item”, and an SQL view named “ItemView”.

    1.  In the SAP Business Application Studio, select *myapp/db* in the SAP HANA PROJECTS pane and choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).


    If the builder displays the message ***\(Builder\) Build of /myapp/db completed*** in the SAP Business Application Studio terminal, the data-model was successfully activated in a HANA database container, and can now be used to store and retrieve data.


**Related Information**  


[Create a Database Procedure in SAP HANA Cloud](create-a-database-procedure-in-sap-hana-cloud-81e83fb.md "Create, edit, and deploy procedures.")

[Create a Database Function in SAP HANA Cloud](create-a-database-function-in-sap-hana-cloud-e3093ea.md "Add a database function to your data model.")

