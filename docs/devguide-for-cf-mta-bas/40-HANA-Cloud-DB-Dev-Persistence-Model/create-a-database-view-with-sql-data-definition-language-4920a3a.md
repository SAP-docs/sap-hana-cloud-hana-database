<!-- loio4920a3af75874cc3a1318c84f8738331 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database View with SQL Data Definition Language

Define a design-time database **view** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio4920a3af75874cc3a1318c84f8738331__prereq_wmq_cdt_sfb"/>

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



<a name="loio4920a3af75874cc3a1318c84f8738331__context_jk3_skt_sfb"/>

## Context

In the SAP HANA database, as in other relational databases, a view contains a set of data elements that are organized using columns and rows. SAP HANA Deployment Infrastructure \(HDI\) enables you to use the SQL DDL syntax to create a database view as a design-time file. Building or deploying the database module that contains the SQL DDL view creates the corresponding view in the corresponding schema.

During the build process, the `.hdbview` plug-in is called to transform a design-time view resource into an SQL view database object. The file format uses a DDL-style syntax which is equivalent to the syntax required in the corresponding SQL statement `CREATE VIEW`, but without the leading "`CREATE`". If the view selects from a synonym which points to an object inside another schema or a different container or to an object inside the same container which is owned by a different user, then the container’s object owner \(“`<container>#OO`”\) needs to have the required privileges on this target object, for example, `SELECT`, `UPDATE`, or `INSERT`. If the views are exposed to other users, the object owner usually needs privileges `WITH GRANT OPTION`. If access to the view needs to be filtered by means of analytic \(or structured\) privileges, then the view defined must contain the `WITH STRUCTURED PRIVILEGE CHECK` clause, as illustrated in the examples below.

To create a design-time SQL DDL view-definition file, perform the following steps:



<a name="loio4920a3af75874cc3a1318c84f8738331__steps_kk3_skt_sfb"/>

## Procedure

1.  Start SAP Business Application Studio.

2.  Open the application project to which you want to add your SQL DDL view.

3.  Create the view-definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL view-definition file and perform the following steps:

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Find Command...*

    2.  Create a new SAP HANA database artifact.

        Type ***hana*** in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new artifact.

    5.  Select the database artifact type, for example, SQL view.

        In the command palette, type ***hdbv*** and choose *SQL View \(hdbview\)* in the list that appears.

    6.  Name the file *PurchaseOrderItemView*.

        The appropriate file suffix \(`.hdbview`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL view-definition artifacts have the file extension `.hdbview`, for example, `PurchaseOrderItemView.hdbview`.

    7.  Save the changes and create the new database view artifact; choose *Create*.


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

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose <span class="FPA-icons"></span> \(Deploy\).

        > ### Note:  
        > A mismatch between the installed SAP HANA version and the version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


7.  Check that the new view has been successfully created in the catalog.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

    3.  Choose *Views*.

    4.  Check the new view is listed in the results pane.

    5.  Select the view to display the contents in the details pane.



**Related Information**  


[SQL View Syntax (.hdbview in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_2_QRC/en-US/2bf9a6f2db824fbd84315196a9c318d5.html "Transforms a design-time view resource into an SQL view database object.") :arrow_upper_right:

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

