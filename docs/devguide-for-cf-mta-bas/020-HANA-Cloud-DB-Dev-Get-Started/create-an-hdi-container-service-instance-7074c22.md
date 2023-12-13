<!-- loio7074c22b359244fc840a1a3c99cb4871 -->

# Create an HDI-Container Service Instance

Create a new instance of an HDI container service.



<a name="loio7074c22b359244fc840a1a3c99cb4871__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.



## Context

You can use the *Create an HDI Container Service Instance* Wizard to set up a new instance of a `hana` service with the service plan `hdi-shared`, as follows:



## Procedure

1.  In SAP Business Application Studio, start the command palette.

    -   Press [Crtl\] + [Shift\] + [P\]  or
    -   Press [F1\] or
    -   Choose *View* \> *Command Palette...* in the menu bar.

2.  Start the service-creation Wizard

    In the command palette, type `HANA` and choose *SAP HANA: Create an HDI Container Service Instance* from the drop-down list.

3.  Define details of the new service instance.

    In the *Create an HDI Container Service Instance* Wizard, you need to provide the following information:

    1.  Type the name of the new service instance.

    2.  Specifiy the name of the schema to be used as the default schema for the new HDI service \(**optional**\).

    3.  Choose whether to use the default database to create the new HDI service or an alternative database.

        -   *Yes*

            Create the new HDI service instance in the default database.

        -   *No*

            You must specify the name \(or ID\) of the target SAP HANA database where you want to create the new HDI service.

            > ### Tip:  
            > You can either select a database name from the drop-down list provided or choose *<Enter a database ID\>* and provide a database ID manually. The database specified by the ID will be used to create the new HDI service instance.



4.  Choose *Create* to set up the new HDI service instance.


**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[Deploy Artifacts with SAP HANA Projects Explorer](deploy-artifacts-with-sap-hana-projects-explorer-4bbbaae.md "Use the SAP HANA Projects explorer to deploy and view your application's design- and run-time database artifacts.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

