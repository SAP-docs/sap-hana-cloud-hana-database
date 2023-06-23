<!-- loio90de80c89b034ac39731bff8269a9a18 -->

# Create an Index with SQL Data Definition Language

Define a design-time database **index** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio90de80c89b034ac39731bff8269a9a18__prereq_wmq_cdt_sfb"/>

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

An index is a data structure that helps to make searching data for a specific column in a database faster and more efficient by reducing the number of records, columns, or rows to consider in the search operation. The data structure stores values for indexed columns from one table in another table. Although the indexed data is usually structured in a so-called b-tree, which ensures that the structure is sorted, indexes can also be structured using the r-tree or hash table method, each of which has advantages and disadvantages. For more information, see the *SAP HANA SQL Reference* in *Related Information*.

You can use the HDI `.hdbindex` artifact to define constraints on unique keys. The file format used in the `.hdbindex` artifact is similar to the syntax used in the corresponding SQL statement "`CREATE INDEX` ", but without the leading "`CREATE ...`" as illustrated in the example below.

> ### Note:  
> The database index plug-in \(`.hdbindex`\) only supports constraints on unique keys; foreign-key constraints are handled by the database constraint plug-in \(`.hdbconstraint`\).



## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Open the application project to which you want to add your SQL DDL database index artifact.

3.  Create the index-definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL index-definition file and perform the following steps:

    1.  Right-click the folder where you want to save the SQL DDL index-definition file and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    2.  Enter the name of the index-definition file in the *File Name* box, for example, `partnerPO`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL index-definition artifacts have the file extension `.hdbindex`, for example, `partnerPO.hdbindex`.

    3.  Choose *Finish* to save the new SQL DDL index-definition file in the database module of your local project workspace.


4.  Define the SQL DDL database index.

    Locate and double-click the new index-definition file that you created in the previous step, for example, `partnerPO.hdbindex`, and add the following SQL DDL code that defines the scope and target of the index:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > `db/src/partnerPO.hdbindex`
    > 
    > ```sql
    > INDEX "PARTNER_IDX" ON "PurchaseOrder.Header" (PARTNER)
    > ```

    > ### Note:  
    > The database index `partnerPO.hdbindex` references the `"PARTNER"` column in the table `"PurchaseOrder.Header"` defined in `PurchaseOrderHeader.hdbtable`, which is described in another task. For more information, see *Create a Database Table with SQL Data Definition Language* in *Related Information* below.

5.  Save all files and rebuild the database module.

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build* \> *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


6.  Verify that the new index is activated in the catalog.

    You can use the *Database Explorer* to display activated objects in the run-time catalog and verify that the index is present.

    1.  Right-click the database module in your application project and in the context menu choose *Open HDI Container*.

    2.  Select *Indexes* from the list; a list of activated indexes is displayed in the *Catalog* pane.

    3.  Select *PARTNER\_IDX* to display the contents of the index in the details pane.



**Related Information**  


[Database Table Index Syntax (.hdbindex in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/58fdf2d2ffae44b6a3dd0e9a3f5ae8c5.html "Transform a design-time index resource into an index on a database table.") :arrow_upper_right:

[Create a Database Constraint with SQL Data Definition Language](create-a-database-constraint-with-sql-data-definition-language-65b61c4.md "Define a design-time database constraint using the SQL Data Definition Language (DDL) syntax.")

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

