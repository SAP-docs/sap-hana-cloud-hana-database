<!-- loio4920a3af75874cc3a1318c84f8738331 -->

# Create a Database View with SQL Data Definition Language

Define a design-time database **view** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio4920a3af75874cc3a1318c84f8738331__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Web IDE Full-Stack. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development workspace and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multi-target application \(or just the database module\) is deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



<a name="loio4920a3af75874cc3a1318c84f8738331__context_jk3_skt_sfb"/>

## Context

In the SAP HANA database, as in other relational databases, a view contains a set of data elements that are organized using columns and rows. SAP HANA Deployment Infrastructure \(HDI\) enables you to use the SQL DDL syntax to create a database view as a design-time file. Building or deploying the database module that contains the SQL DDL view creates the corresponding view in the corresponding schema.

During the build process, the `.hdbview` plug-in is called to transform a design-time view resource into an SQL view database object. The file format uses a DDL-style syntax which is equivalent to the syntax required in the corresponding SQL statement `CREATE VIEW`, but without the leading "`CREATE`". If the view selects from a synonym which points to an object inside another schema or a different container or to an object inside the same container which is owned by a different user, then the container’s object owner \(“`<container>#OO`”\) needs to have the required privileges on this target object, for example, `SELECT`, `UPDATE`, or `INSERT`. If the views are exposed to other users, the object owner usually needs privileges `WITH GRANT OPTION`. If access to the view needs to be filtered by means of analytic \(or structured\) privileges, then the view defined must contain the `WITH STRUCTURED PRIVILEGE CHECK` clause, as illustrated in the examples below.

To create a design-time SQL DDL view-definition file, perform the following steps:



<a name="loio4920a3af75874cc3a1318c84f8738331__steps_kk3_skt_sfb"/>

## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Open the application project to which you want to add your SQL DDL view.

3.  Create the view-definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL view-definition file and perform the following steps:

    1.  Right-click the folder where you want to save the SQL DDL view-definition file and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    2.  Enter the name of the view-definition file in the *File Name* box, for example, `PurchaseOrderItemView`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL view-definition artifacts have the file extension `.hdbview`, for example, `PurchaseOrderItemView.hdbview`.
        > 
        > .

    3.  Choose *Finish* to save the new SQL DDL view-definition file in the database module of your local project workspace.


4.  Define the structure of the SQL DDL view.

    Locate and double-click the new view-definition file that you created in the previous step, for example, `PurchaseOrderItem.hdbview`, and add the following SQL DDL code that defines the view:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    `db/src/PurchaseOrderItem.hdbview`

    ```sql
    
    VIEW "PurchaseOrder.ItemView" COMMENT 'Purchase Order Item View' ( 
         "PurchaseOrderItemId",
         "PartnerId",
         "ProductID",
         "CurrencyCode",
         "Amount",
         "NetAmount",
         "TaxAmount",
         "Quantity",
         "QuantityUnit",
         "DeliveryDate1"
         ) AS SELECT
         "Item_$0"."POHeader"."PURCHASEORDERID" AS "PurchaseOrderItemId" ,
         "Item_$0"."POHeader"."PARTNER" AS "PartnerId" ,
         "Item_$0"."PRODUCT" AS "ProductID" ,
         "Item_$0"."CURRENCY" AS "CurrencyCode" ,
         "Item_$0"."GROSSAMOUNT" AS "Amount" ,
         "Item_$0"."NETAMOUNT" AS "NetAmount" ,
         "Item_$0"."TAXAMOUNT" AS "TaxAmount" ,
         "Item_$0"."QUANTITY" AS "Quantity" ,
         "Item_$0"."QUANTITYUNIT" AS "QuantityUnit" ,
         "Item_$0"."DELIVERYDATE" AS "DeliveryDate1"
    FROM "PurchaseOrder.Item" AS "Item_$0" 
    WITH READ ONLY STRUCTURED PRIVILEGE CHECK 
    ```

    > ### Note:  
    > The view `PurchaseOrder.ItemView` specifies an association with the table `"PurchaseOrder.Item"` defined in `PurchaseOrderItem.hdbtable`, which we created in the previous tutorial. Access to the view is also restricted by a `STRUCTURED PRIVILEGE CHECK`, which is described in another tutorial. For more information about either tutorial, see *Create a Database Table with SQL Data Definition Language* and *Create a Structured Privilege with SQL Data Definition Language*, respectively, in *Related Information* below.

5.  Save the SQL DDL view-definition file.

    Saving the view definition persists the file in your local workspace; it does not create any objects in the database catalog.

6.  Build and deploy the database module.

    To activate the new view definition and generate a corresponding object in the catalog, use the *Build* or *Deploy* feature.

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


7.  Check that the new view has been successfully created in the catalog.

    > ### Tip:  
    > A selection of run-time tools is available in the *Database Explorer* perspective of SAP Web IDE Full-Stack at the following location:
    > 
    > *Tools* \> *Database Explorer*

    Your database run-time objects are located in the HDI container created for your multitarget application's database module; you need to locate and bind to this application-specific container to view its contents. The container name contains the name of the user logged into the SAP Web IDE Full-Stack, the name of the database module containing the CDS design-time entities, and the string *\-hdi-container*, for example:

    **<XS\_UserName\>*-ctetig24\[...\]-*<DB\_Module\>*-hdi-container*

    To view the contents of the HDI container that is bound to your development project, open the SAP HANA run-time *Development* perspective, open the project containing the new tables, right-click the database module where the design-time tables are stored, and in the context menu select *Open HDI Container*.

    > ### Tip:  
    > The new views are listed in the *Views* node. However, the view we created in this task is protected by a "read-only" structured privilege which still needs to be defined. In addition, until the underlying tables used by the view contain some data, the *Open Data* tool will not display the view contents.


**Related Information**  


[SQL View Syntax (.hdbview in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/2bf9a6f2db824fbd84315196a9c318d5.html "Transforms a design-time view resource into an SQL view database object.") :arrow_upper_right:

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

