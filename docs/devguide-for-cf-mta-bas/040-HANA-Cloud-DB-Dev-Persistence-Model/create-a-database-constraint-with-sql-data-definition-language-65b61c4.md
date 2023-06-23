<!-- loio65b61c47c39a44c7909095de902dc22f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Constraint with SQL Data Definition Language

Define a design-time database **constraint** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio65b61c47c39a44c7909095de902dc22f__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a dev space and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multitarget application \(or just the database module\) is deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



## Context

An SQL constraint specifies rules for the data stored in a database table; the rules can apply to a column, a table, multiple tables, or an entire schema. Constraints limit the type of data that can be loaded into a table based on the specified rules. A constraint is typically used to define the properties that data in a database must comply with in order to ensure the consistency, accuracy, and reliability of the data in the database.

You can use the HDI `.hdbconstraint` artifact to define constraints on foreign keys. The file format used in the `.hdbconstraint` artifact is similar to the syntax used in the corresponding SQL statement "`ALTER TABLE ADD CONSTRAINT` ", but phrased as "`CONSTRAINT constraint ON table` …" as illustrated in the example below.

> ### Note:  
> The database constraint plug-in \(`.hdbconstraint`\) only supports `FOREIGN KEY` constraints; unique constraints are handled by the table index plug-in \(`.hdbindex`\).



## Procedure

1.  Start SAP Business Application Studio.

2.  Open the application project to which you want to add your SQL DDL database constraint artifact.

3.  Create the database-constraint definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL constraint-definition file and perform the following steps:

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type ***hana*** in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new artifact.

    5.  Select the database artifact type, for example, database constraint.

        In the command palette, type ***hdbc*** and choose *Constraint \(hdbconstraint\)* in the list that appears.

    6.  Name the file *PurchaseOrderConstraint*.

        The appropriate file suffix \(`.hdbconstraint`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL constraint artifacts \(for foreign keys\) have the file extension `.hdbconstraint`, for example, `PurchaseOrderConstraint.hdbconstraint`.

    7.  Save the changes and create the new database view artifact; choose *Create*.


4.  Define the structure of the SQL DDL database constraint.

    Locate and double-click the new constraint-definition file that you created in the previous step, for example, `PurchaseOrderConstraint.hdbconstraint`, and add the following SQL DDL code that defines the rules of the constraint:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > `db/src/PurchaseOrderConstraint.hdbconstraint`
    > 
    > ```sql
    > CONSTRAINT PO_CONST 
    > ON "PurchaseOrder.Item" FOREIGN KEY ("POHeader.PURCHASEORDERID") 
    > REFERENCES "PurchaseOrder.Header" ("PURCHASEORDERID") ON DELETE CASCADE 
    > ```

    > ### Note:  
    > The database constraint `PurchaseOrderConstraint.hdbconstraint` references the table `"PurchaseOrder.Header""` defined in `PurchaseOrderHeader.hdbtable`, which is created in another task. For more information, see *Create a Database Table with SQL Data Definition Language* in *Related Information* below.

5.  Save all changes and rebuild \(or redeploy\) the database module.

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose <span class="FPA-icons"></span> \(Deploy\).

        > ### Note:  
        > A mismatch between the installed SAP HANA version and the version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


6.  Verify that the new constraint is activated in the catalog.

    You can use the *Database Explorer* to display activated objects in the run-time catalog and verify that the constraint is present.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

        You can filter by name the databases displayed in the *DATABASE LIST*. For example, choose <span class="SAP-icons"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and choose *OK* press or [Enter\]. To reset the filter, press [Escape\].

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

        You can filter by name the database objects displayed in the *CATALOG BROWSER*. Choose <span class="SAP-icons"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Escape\].

    3.  Choose *Tables* from the list; a list of activated tables is displayed in the *Catalog* pane.

    4.  Right-click *PurchaseOrder.Item* and choose *Generate CREATE Statement* in the context menu to display the generated SQL statement in the *SQL Console*.

    5.  Scroll down to the end of the generated SQL statement and check that `ADD CONSTRAINT` is present in the `ALTER TABLE` statement, as illustrated in the following example:

        > ### Output Code:  
        > ```
        > ALTER TABLE "4AABE78A0BA249B185CBBCA1CC89900D"."PurchaseOrder.Item" ADD CONSTRAINT "PO_CONST" FOREIGN KEY ( "POHeader.PURCHASEORDERID" ) REFERENCES "4AABE78A0BA249B185CBBCA1CC89900D"."PurchaseOrder.Header" ("PURCHASEORDERID") ON UPDATE RESTRICT ON DELETE CASCADE ENFORCED VALIDATED INITIALLY IMMEDIATE;
        > 
        > ```



**Related Information**  


[Database Constraint Syntax (.hdbconstraint in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/bda54706fbda4910908871743b675ad1.html "Transform a design-time constraint into a constraint on database tables.") :arrow_upper_right:

[Create an Index with SQL Data Definition Language](create-an-index-with-sql-data-definition-language-90de80c.md "Define a design-time database index using the SQL Data Definition Language (DDL) syntax.")

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

