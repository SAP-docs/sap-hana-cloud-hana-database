<!-- loio90de80c89b034ac39731bff8269a9a18 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create an Index with SQL Data Definition Language

Define a design-time database **index** using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio90de80c89b034ac39731bff8269a9a18__prereq_wmq_cdt_sfb"/>

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

An index is a data structure that helps to make searching data for a specific column in a database faster and more efficient by reducing the number of records, columns, or rows to consider in the search operation. The data structure stores values for indexed columns from one table in another table. Although the indexed data is usually structured in a so-called b-tree, which ensures that the structure is sorted, indexes can also be structured using the r-tree or hash table method, each of which has advantages and disadvantages. For more information, see the *SAP HANA SQL Reference* in *Related Information*.

You can use the HDI `.hdbindex` artifact to define constraints on unique keys. The file format used in the `.hdbindex` artifact is similar to the syntax used in the corresponding SQL statement "`CREATE INDEX` ", but without the leading "`CREATE ...`" as illustrated in the example below.

> ### Note:  
> The database index plug-in \(`.hdbindex`\) only supports constraints on unique keys; foreign-key constraints are handled by the database constraint plug-in \(`.hdbconstraint`\).



## Procedure

1.  Start SAP Business Application Studio.

2.  Open the application project to which you want to add your SQL DDL database index artifact.

3.  Create the index-definition file in SQL DDL.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src</code> where you want to create the new SQL DDL index-definition file and perform the following steps:

    1.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new artifact.

    5.  Select the database artifact type, for example, index.

        In the command palette, type `hdbi` and choose *Index \(hdbindex\)* in the list that appears.

    6.  Name the file *partnerPO*.

        The appropriate file suffix \(`.hdbindex`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL index artifacts have the file extension `.hdbindex`, for example, `partnerPO.hdbindex`.

    7.  Save the changes and create the new database view artifact; choose *Create*.


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

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

        > ### Note:  
        > A mismatch between the installed SAP HANA version and the version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


6.  Verify that the new index is activated in the catalog.

    You can use the *Database Explorer* to display activated objects in the run-time catalog and verify that the index is present.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \([Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

        You can filter by name the databases displayed in the *DATABASE LIST*. For example, choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and choose *OK* press or [Enter\]. To reset the filter, press [Escape\].

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

        You can filter by name the database objects displayed in the *CATALOG BROWSER*. Choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Escape\].

    3.  Choose *Indexes*.

    4.  Select *PARTNER\_IDX* to display the contents of the index in the details pane.



**Related Information**  


[Database Table Index Syntax (.hdbindex in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/58fdf2d2ffae44b6a3dd0e9a3f5ae8c5.html "Transform a design-time index resource into an index on a database table.") :arrow_upper_right:

[Create a Database Constraint with SQL Data Definition Language](create-a-database-constraint-with-sql-data-definition-language-65b61c4.md "Define a design-time database constraint using the SQL Data Definition Language (DDL) syntax.")

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

