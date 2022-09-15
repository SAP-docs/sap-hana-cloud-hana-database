<!-- loio00340d4ede0a43ceb0a67f36bbc46a3a -->

# Create Virtual Tables

Virtual tables enable you to access objects in other databases without having to replicate in SAP HANA.



<a name="loio00340d4ede0a43ceb0a67f36bbc46a3a__prereq_qrw_sym_bhb"/>

## Prerequisites

You must already have created a remote source.



## Context

SAP Business Application Studio supports the creation of virtual tables using either a code editor or a built-in Wizard. The Wizard is designed to help those users who are not sure of the syntax required to create virtual tables in the code editor. After creating the virtual tables, you can use them as a data source.



## Procedure

1.  Start SAP Business Application Studio.

2.  Select the *SAP HANA Database Module* in which you want to create the virtual table.

3.  Start the database-artifact creation Wizard.

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Choose *View* \> *Find Command...*

    2.  Start the database-artifact creation Wizard.

        In the command palette, type ***database*** and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.


4.  Create a new virtual table.

    Specify the following mandatory details:

    -   Artifact location: `~/myapp/db/src`
    -   Database version: *HANA Cloud* 
    -   Artifact type: *Virtual Table \(hdbvirtualtable\)*

        > ### Tip:  
        > In the *Choose the artifact type* box, type ***table*** to display only those artifacts with the name "table" and select *Virtual Table \(hdbvirtualtable\)* from the list.

    -   Artifact Name: Use the following naming format: ****<namespace\>*::virtual\_table\_name***.

        > ### Tip:  
        > You do not need to include the file suffix in the artifact name; the file suffix is added automatically according to the selection in the *Artifact type* box.


    Choose *Create*.

    The creation Wizard starts the *Virtual Table Editor*.

5.  Define the virtual table.

    Use the *Virtual Table Editor* to configure the new virtual table.

    > ### Tip:  
    > The object owner and the application \(run-time\) user require the global object privilege `CREATE VIRTUAL TABLE` on the remote source to be able to use the *Virtual Table Editor* to locate and select objects in the remote databases. You can use an `hdbgrants` file to grant privileges, for example, with the `"global_object_privileges": [...]` key in the `"object_owner"` and `"application_user"` sections \(`"type": "REMOTE SOURCE"` and `"privileges": [ "CREATE VIRTUAL TABLE" ]`\). For more information about syntax requirements in the `hdbgrants` file, see *Related Information* below.

    The following details are mandatory:

    -   *Virtual table name \**

        The editor displays the name that you specified when creating the new virtual table in the previous step.

    -   *Remote source name \**

        Choose *\[…\]* to display a list of known remote sources and select the one that contains the database object \(for example, a table\) that you want to use. You can then choose the database and schema where the object is located.

    -   *Object name \**

        Choose *\[…\]* to display a list of known objects in the database schema on the specified remote source and choose the object you want to use.


6.  Choose *Save* in the menu bar or  [CTRL\] + [S\]  to save your file \(virtual table\).

7.  Buildand deploy the SAP HANA database module.

    The build process uses the design-time database artifacts to generate the corresponding actual objects \(run-time objects\) in the HDI container.

    In the *SAP HANA PROJECTS* explorer, select the application project whose database artifacts you want to deploy, and choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).


**Related Information**  


[Syntax Options in the hdbgrants File](syntax-options-in-the-hdbgrants-file-f49c1f5.md "Assign the privileges required by users to access objects in the target schema.")

