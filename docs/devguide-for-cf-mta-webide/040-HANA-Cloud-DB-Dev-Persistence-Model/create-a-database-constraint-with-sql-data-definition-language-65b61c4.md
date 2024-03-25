<!-- loio65b61c47c39a44c7909095de902dc22f -->

# Create a Database Constraint with SQL Data Definition Language

Define a design-time database **constraint** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio65b61c47c39a44c7909095de902dc22f__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Web IDE Full-Stack. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development workspace and a multitarget application \(MTA\) project.
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

1.  Start SAP Web IDE Full-Stack.

2.  Open the application project to which you want to add your SQL DDL database constraint artifact.

3.  Create the database-constraint definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL constraint-definition file and perform the following steps:

    1.  Right-click the folder where you want to save the SQL DDL constraint-definition file and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    2.  Enter the name of the constraint-definition file in the *File Name* box, for example, `PurchaseOrderConstraint`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL constraint-definition artifacts have the file extension `.hdbconstraint`, for example, `PurchaseOrderConstraint.hdbconstraint`.

    3.  Choose *Finish* to save the new SQL DDL constraint-definition file in the database module of your local project workspace.


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

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build* \> *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


6.  Verify that the new constraint is activated in the catalog.

    You can use the *Database Explorer* to display activated objects in the run-time catalog and verify that the constraint is present.

    1.  Right-click the database module in your application project and in the context menu choose *Open HDI Container*.

    2.  Select *Tables* from the list; a list of activated tables is displayed in the *Catalog* pane.

    3.  Right-click *PurchaseOrder.Item* and choose *Generate CREATE Statement* in the context menu to display the generated SQL statement in the *SQL Console*.

    4.  Scroll down to the end of the generated SQL statement and check that `ADD CONSTRAINT` is present in the `ALTER TABLE` statement, as illustrated in the following example:

        > ### Output Code:  
        > ```
        > ALTER TABLE "4AABE78A0BA249B185CBBCA1CC89900D"."PurchaseOrder.Item" ADD CONSTRAINT "PO_CONST" FOREIGN KEY ( "POHeader.PURCHASEORDERID" ) REFERENCES "4AABE78A0BA249B185CBBCA1CC89900D"."PurchaseOrder.Header" ("PURCHASEORDERID") ON UPDATE RESTRICT ON DELETE CASCADE ENFORCED VALIDATED INITIALLY IMMEDIATE;
        > 
        > ```



**Related Information**  


[Database Constraint Syntax (.hdbconstraint in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/bda54706fbda4910908871743b675ad1.html "Transform a design-time constraint into a constraint on database tables.") :arrow_upper_right:

[Create an Index with SQL Data Definition Language](create-an-index-with-sql-data-definition-language-90de80c.md "Define a design-time database index using the SQL Data Definition Language (DDL) syntax.")

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

