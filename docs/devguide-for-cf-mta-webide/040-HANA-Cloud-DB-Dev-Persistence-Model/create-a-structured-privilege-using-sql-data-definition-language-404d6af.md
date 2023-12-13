<!-- loio404d6af8e57044e5b20ecdee9e6b3c04 -->

# Create a Structured Privilege Using SQL Data Definition Language

Define a structured privilege using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio404d6af8e57044e5b20ecdee9e6b3c04__prereq_wmq_cdt_sfb"/>

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



## Context

Access to the HDI database objects is performed automatically by the HDI container's technical user. If you want to grant additional privileges to the technical user \(for example, in structured privileges that grant access to an SQL view\), you first need to create this structured privilege.

SAP HANA Deployment Infrastructure \(HDI\) enables you to use the SQL DDL syntax to define a structured privilege in a design-time file. Building or deploying the database module that contains the SQL DDL structured privilege creates the corresponding object in the corresponding schema.

During the build process, the `.hdbstructuredprivilege` plug-in is called to transform a design-time structured-privilege resource into an SQL database object. The format or the design-time file requires a DDL-style syntax which is equivalent to the syntax required in the corresponding SQL statement `CREATE STRUCTURED PRIVILEGE`, but without the leading "`CREATE`", as illustrated in the code examples below.

> ### Note:  
> The views to which the structured privileges apply must include the `WITH STRUCTURED PRIVILEGE CHECK` clause.

A dedicated database role, created in another tutorial, can also be used to provide broader access for other database users. For more information about creating a database role in SQL DDL, see *Create a Database Role Using SQL Data Definition Language* in *Related Information* below.

To create a design-time SQL DDL structured-privilege definition file, perform the following steps:



## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Create the structured-privilege definition file.

    Browse to the folder in the database module in your application's project workspace, for example, Open the application project to which you want to add your SQL DDL structured privilege.<code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/</code> where you want to create the new SQL DDL structured-privilege definition file and perform the following steps:

    1.  Right-click the folder where you want to add a new folder to store the SQL DDL structured-privilege definition file and choose *New* \> *Folder* in the context-sensitive pop-up menu. Add a folder called `roles`.

    2.  Right-click the new `roles` folder and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    3.  Enter the name of the structured-privilege definition file in the *File Name* box, for example, `PurchaseOrder`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL structured-privilege definition artifacts have the file extension `.hdbstructuredprivilege`Open the application project to w, for example, `PurchaseOrder.hdbstructuredprivilege`.

    4.  Choose *Finish* to save the new SQL DDL structured-privilege definition file in the `roles` folder of the database module of your local project workspace.


3.  Define the structure of the SQL DDL structured privilege.

    Locate and double-click the structured-privilege definition file that you created in the previous step, for example, `PurchaseOrder.hdbstructuredprivilege`, and add the following SQL DDL code that defines the structured-privilege:

    > ### Note:  
    > The following code example is provided for illustration purposes only. For this reason, the filter value `'EUR'` is hard-coded; in a real-life example, the attribute value used in the privilege would typically be resolved from user attributes defined elsewhere.

    > ### Sample Code:  
    > `db/src/roles/PurchaseOrder.hdbstructuredprivilege`
    > 
    > ```sql
    > STRUCTURED PRIVILEGE 
    >     "PO_VIEW_PRIVILEGE"
    >     FOR SELECT ON 
    >     "PurchaseOrder.ItemView"
    >     WHERE "CurrencyCode" = 'EUR'
    > 
    > ```

    > ### Note:  
    > This example of a structured privilege is used in the SQL view `"PurchaseOrder.ItemView"`, which is created and defined in another task. For more information, see *Create a Database View with SQL Data Definition Language* in *Related Information* below.

4.  Save all changes and rebuild \(or redeploy\) the database module.

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build* \> *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


5.  Verify that the structured privilege is working and filtering access to the view data.

    You can use the *Database Explorer* to display activated views in the run-time catalog and verify that the view contains the selected data.

    1.  Right-click the database module in your application project and in the context menu choose *Open HDI Container*.

    2.  Select *Views* from the list; a list of activated views is displayed in the *Catalog* pane.

    3.  Select and right-click view *PurchaseOrder.ItemView* and in the context menu choose *Open Data*.


    Thanks to the new structured privilege required by the view, you should now be able to see data in the view, but only those records with currency of EUR, as specified in the structured-privilege.

    > ### Note:  
    > To enable a database user other than the technical user to access the structured-privilege-based view, a suitable database role must be granted to the additional database user requiring access. This rule also applies for non-technical-user access to any other catalog objects. For more information about creating roles, see *Create a Database Role with SQL Data Definition Language* in *Related Information* below.


**Related Information**  


[Structured Privilege Syntax (.hdbstructuredprivilege in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/c3827df3a9dc4c45b5b4e2f7b1070b08.html "Transforms a design-time DDL-based structured privilege resource into a structured privilege object.") :arrow_upper_right:

[Create a Database View with SQL Data Definition Language](create-a-database-view-with-sql-data-definition-language-4920a3a.md "Define a design-time database view using the SQL Data Definition Language (DDL) syntax.")

[Creating Data Persistence Artifacts with SQL DDL](creating-data-persistence-artifacts-with-sql-ddl-a216fd8.md "You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

