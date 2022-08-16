<!-- loio492729c3918c4cb7a645f69a6bdfbc56 -->

# Create a Database Role

Define a design-time database role using the JavaScript Object Notation \(JSON\) syntax.



<a name="loio492729c3918c4cb7a645f69a6bdfbc56__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Web IDE Full-Stack. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development workspace and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts.

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multi-target application \(or just the database module\) is built or deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



<a name="loio492729c3918c4cb7a645f69a6bdfbc56__context_rln_cr5_sfb"/>

## Context

Access to the HDI database objects is performed automatically by the HDI container's technical user. If you want to provide additional users \(other than the default technical user assigned to the HDI container\) with access to catalog objects, you need to create a dedicated database role and grant this role to the users requiring access to the database objects.

The role plug-in transforms a design-time role resource, a file with the `.hdbrole` extension, into a run-time role, which can be assigned to database users. The format of the design-time role file is based on JSON, and enables you to specify a list of privileges \(for example, system, schema, object, and analytic privileges\) and, as an additional option, include other roles, too.

> ### Tip:  
> The additional roles can be either global or local. `"global_roles"` are created without a schema; `"schema_roles"` are created with a schema. For more information about the design-time role artifact, for example, file-name restrictions and the use of "`_with_grant_option`" privileges, see *HDI Design-Time Resources* in *Related Information* below.

To create and activate a database role, perform the following steps:



<a name="loio492729c3918c4cb7a645f69a6bdfbc56__steps_sln_cr5_sfb"/>

## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Open the application project to which you want to add your SQL DDL role.

3.  Create the role-definition file `admin.hdbrole`.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/roles</code> where you want to create the new SQL DDL role-definition file and perform the following steps:

    1.  If it does not already exist, add a folder called `roles` to the database module of your application.

        Right-click the folder `src/` in the database module of your application project and choose *New* \> *Folder* in the context-sensitive pop-up menu.

    2.  Right-click the `roles` folder and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    3.  Enter the name of the role-definition file in the *File Name* box, for example, "***admin***".

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL role-definition artifacts have the file extension `.hdbrole`, for example, `admin.hdbrole`.

    4.  Choose *Finish* to save the new SQL DDL role-definition file in the `roles` folder of the database module of your local project workspace.


4.  Define the contents of the SQL DDL role `admin.hdbrole`.

    Locate and right-click the role-definition file that you created in the previous step, for example, `admin.hdbrole`, choose *Open with* \> *Code Editor*, and add the following SQL DDL code that defines the role scope:

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application extension provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > `db/src/roles/admin.hdbrole`
    > 
    > ```json
    > 
    > {
    >   "role":{
    >      "name": "admin",
    >      "schema_privileges": [{
    >         "privileges": ["SELECT METADATA", 
    >                        "SELECT CDS METADATA", 
    >                        "SELECT", 
    >                        "INSERT", 
    >                        "EXECUTE", 
    >                        "DELETE", 
    >                        "UPDATE",
    >                        "CREATE TEMPORARY TABLE"
    >          ]
    >      }],
    >      "schema_analytic_privileges": [
    >         {
    >           "privileges":[ "PO_VIEW_PRIVILEGE" ]
    >         }
    >         ]
    >       }
    > }
    > 
    > ```

    > ### Tip:  
    > By default, *SAP Web IDE Full-stack* opens a role-definition artifact in the *Role Editor*, which displays a graphical representation of the role. To switch between the *Role Editor* and the text-based *Code Editor*, right-click the role-definition artifact that you want to open, and choose *Open with* \> *\[Code Editor | Role Editor\]*. Changes to the open artifact are synchronized between both editors. Note that the *Role Editor* is not able to open an incorrectly formatted file.

5.  Create the role-definition file `adminOwner.hdbrole`.

    Browse to the folder in the database module in your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/roles</code> where you want to create the new SQL DDL role-definition file and perform the following steps:

    1.  Right-click the `roles` folder in the database module and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    2.  Enter the name of the role-definition file in the *File Name* box, for example, `adminOwner`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL role-definition artifacts have the file extension `.hdbrole`, for example, `adminOwner.hdbrole`.

    3.  Choose *Finish* to save the new SQL DDL role-definition file in the `roles` folder of the database module of your local project workspace.


6.  Define the contents of the SQL DDL role `adminOwner.hdbrole`.

    Locate and right-click the role-definition file that you created in the previous step, for example, `adminOwner.hdbrole`, choose *Open with* \> *Code editor*, and add the following SQL DDL code that defines the role scope:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > `db/src/roles/adminOwner.hdbrole`
    > 
    > ```json
    > {
    >   "role":{
    >     "name": "admin#",
    >     "schema_roles": [{
    >     "names": ["admin"]
    >     }] 
    >   }
    > }
    > ```

    > ### Tip:  
    > A role name that ends with the hash character \(\#\), for example, `"admin#"` can include "`with-grant-option`" privileges as well as references to other roles whose names also end with \#. However, a role whose name ends with \# can only be granted to an HDI container’s object owner \(`<container>#OO`\).

7.  Assign the `admin` role to the technical user of the application container.

    To ensure the automatic assignment of the `admin` role to the technical user of the application container, you need to create a role with a special name `default_access_role` as described in the following steps:

    1.  If it does not already exist, add a folder called `defaults` to the database module of your application.

        Right-click the folder `src/` in the database module of your application project and choose *New* \> *Folder* in the context-sensitive pop-up menu. Enter the name `defaults`.

    2.  Right-click the `defaults` folder and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    3.  Enter the name of the new role-definition file in the *File Name* box, for example, `default_access_role`.

        You can specify the corresponding file extension from the drop-down list in the *File Type* text box.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL role-definition artifacts have the file extension `.hdbrole`, for example, `default_access_role.hdbrole`.

    4.  Define the contents of the new SQL DDL role `default_access_role.hdbrole`.

        Locate and double-click the role-definition file that you created in the previous step, for example, `default_access_role.hdbrole`, and add the following SQL DDL code that defines the role scope:

        > ### Note:  
        > The following code example is provided for illustration purposes only.

        > ### Sample Code:  
        > `db/src/defaults/default_access_role.hdbrole`
        > 
        > ```json
        > {
        >   "role":{
        >     "name": "default_access_role",
        >     "schema_roles": [{
        >       "names": ["admin"]
        >     }] 
        >   }
        > }
        > ```

    5.  Choose *Finish* to save the new SQL DDL role-definition file in the `defaults` folder of the database module of your local project workspace.


8.  Save all files and rebuild \(or redeploy\) the database module.

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build* \> *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


9.  Verify that the new roles are working and enabling access to the view data.

    You can use the *Database Explorer* to display activated views in the run-time catalog and verify that the view contains the selected data. The SQL view `PurchaseOrder.ItemView` should now be accessible to database users other than the HDI container's technical database user.

    1.  Right-click the database module in your application project and in the context menu choose *Open HDI Container*.

    2.  Select *Views* from the list; a list of activated views is displayed in the *Catalog* pane.

    3.  Select and right-click view `PurchaseOrder.ItemView` and in the context menu choose *Open Data*.



**Related Information**  


[Database Role Syntax (.hdbrole in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_2_QRC/en-US/625d7733c30b4666b4a522d7fa68a550.html "Transform a design-time role resource (.hdbrole) into a run-time role object.") :arrow_upper_right:

[Create a Database View with SQL Data Definition Language](create-a-database-view-with-sql-data-definition-language-4920a3a.md "Define a design-time database view using the SQL Data Definition Language (DDL) syntax.")

[Create a Structured Privilege Using SQL Data Definition Language](create-a-structured-privilege-using-sql-data-definition-language-404d6af.md "Define a structured privilege using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

[HDI Design-Time Resources and Build Plug-ins](hdi-design-time-resources-and-build-plug-ins-7ce8ca4.md "Database design-time resources must be mapped to a build plug-in for deployment purposes.")

