<!-- loio404d6af8e57044e5b20ecdee9e6b3c04 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Structured Privilege Using SQL Data Definition Language

Define a structured privilege using the SQL Data Definition Language \(DDL\) syntax.



<a name="loio404d6af8e57044e5b20ecdee9e6b3c04__prereq_wmq_cdt_sfb"/>

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

Access to the HDI database objects is performed automatically by the HDI container's technical user. If you want to grant additional privileges to the technical user \(for example, in structured privileges that grant access to an SQL view\), you first need to create this structured privilege.

SAP HANA Deployment Infrastructure \(HDI\) enables you to use the SQL DDL syntax to define a structured privilege in a design-time file. Building or deploying the database module that contains the SQL DDL structured privilege creates the corresponding object in the corresponding schema.

During the build process, the `.hdbstructuredprivilege` plug-in is called to transform a design-time structured-privilege resource into an SQL database object. The format or the design-time file requires a DDL-style syntax which is equivalent to the syntax required in the corresponding SQL statement `CREATE STRUCTURED PRIVILEGE`, but without the leading "`CREATE`", as illustrated in the code examples below.

> ### Note:  
> The views to which the structured privileges apply must include the `WITH STRUCTURED PRIVILEGE CHECK` clause.

A dedicated database role, created in another tutorial, can also be used to provide broader access for other database users. For more information about creating a database role in SQL DDL, see *Create a Database Role Using SQL Data Definition Language* in *Related Information* below.

To create a design-time SQL DDL structured-privilege definition file, perform the following steps:



## Procedure

1.  Start SAP Business Application Studio.

2.  Create the structured-privilege definition file.

    Browse to the folder in the database module in your application's project workspace, for example, Open the application project to which you want to add your SQL DDL structured privilege.<code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/</code> where you want to create the new SQL DDL structured-privilege definition file and perform the following steps:

    1.  Create a new folder for your roles and structured-privilege artifacts.

        In the `db` module, right click the `db/src/` folder, create a new folder named "`roles`".

    2.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    3.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    4.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *db/src/roles* folder, and choose *Open*.

    5.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new artifact.

    6.  Select the database artifact type, for example, a structured privilege.

        In the command palette, type `hdbst` and choose *Structured Privilege \(hdbstructuredprivilege\)* in the list that appears.

    7.  Name the file *PurchaseOrder*.

        The appropriate file suffix \(`.hdbstructuredprivilege`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL structured-privilege definition artifacts have the file extension `.hdbstructuredprivilege`, for example, `PurchaseOrder.hdbstructuredprivilege`.

    8.  Save the changes and create the new database structured-privilege artifact; choose *Create*.


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

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

        > ### Note:  
        > A mismatch between the installed SAP HANA version and the version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


5.  Verify that the structured privilege is working and filtering access to the view data.

    You can use the *Database Explorer* to display activated views in the run-time catalog and verify that the view contains the selected data.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \([Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

        You can filter by name the databases displayed in the *DATABASE LIST*. For example, choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and choose *OK* press or [Enter\]. To reset the filter, press [Escape\].

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

        You can filter by name the database objects displayed in the *CATALOG BROWSER*. Choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Escape\].

    3.  Choose *Views*.

    4.  Select *PurchaseOrder.ItemView* to display the view's contents in the details pane.


    Thanks to the new structured privilege required by the view, you should now be able to see data in the view, but only those records with currency of EUR, as specified in the structured-privilege.

    > ### Note:  
    > To enable a database user other than the technical user to access the structured-privilege-based view, a suitable database role must be granted to the additional database user requiring access. This rule also applies for non-technical-user access to any other catalog objects. For more information about creating roles, see *Create a Database Role with SQL Data Definition Language* in *Related Information* below.


**Related Information**  


[Structured Privilege Syntax (.hdbstructuredprivilege in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/c3827df3a9dc4c45b5b4e2f7b1070b08.html "Transforms a design-time DDL-based structured privilege resource into a structured privilege object.") :arrow_upper_right:

[Create a Database View with SQL Data Definition Language](create-a-database-view-with-sql-data-definition-language-4920a3a.md "Define a design-time database view using the SQL Data Definition Language (DDL) syntax.")

[Creating Data Persistence Artifacts with SQL DDL](creating-data-persistence-artifacts-with-sql-ddl-a216fd8.md "You can use SQL DDL to define the underlying database objects that store and provide data for your application, for example, tables and views.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

