<!-- loio4f5add96a6a04d9f81dbaed135bf84ab -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind an Application to a Database Schema Service



<a name="loio4f5add96a6a04d9f81dbaed135bf84ab__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project \(*FlightReservation* in this example\) that you want to bind is available.
-   The application project contains a database module called *db*.

    > ### Tip:  
    > If the database module is not yet bound to any service, you can bind it as part of this tutorial.




## Context

The *SAP HANA PROJECTS* explorer includes tools that enable you to manage the bindings to any database services required by your SAP HANA database application. You can bind an application to an existing schema service, for example, to make use of data provided by another application.

> ### Tip:  
> The list of existing schema services is displayed in *Database Connections* along with the current binding status, for example: ![](images/BAS_icon_dependencyBound_e45e7a9.svg) \(*bound service*\) or ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) \(*unbound service*\). If your application is already bound to a service, the name of the bound service is included \(in brackets\), for example, *cross-container-service-1 \(MySchema\)*.

To bind an application to an alternative schema service, perform the following steps:



## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Add a new database connection. \(*Optional*\)

    If the service to which you want to bind your application is not already included in the list of available services displayed in *Database Connections*, you need to add it, as follows:

    1.  Start the *Add Database Wizard*.

        Use the <span class="SAP-icons-V5"></span> \(Add database connection\) tool in the *Database Connections* node to start the *Add Database Connection* Wizard,

    2.  Select the **type** of database connection to add.

        In the drop-down list of database connection types, choose *Existing schema service instance*.

    3.  Select the schema service to connect to.

        Choose the target schema service from the drop-down list of options, for example *MySchema hana \(schema\)*.


    The new connection is displayed in the list of database connections under the *Database Connections* node in the *SAP HANA PROJECTS* pane, for example, ![](images/BAS_icon_dependencyNotBound_1694e4a.svg)*cross-container-service-1*.

3.  Bind a database application to a schema service.

    Either the schema service instance is part of your application, in which case it is defined in the application's development descriptor \(`mta.yaml`\), or you can bind the database application to another schema service instance, for example, if you want to use data stored in an existing "schema" instance that is not part of your application.

    1.  Select a connection to bind the schema service to.

        In the list of connections displayed in *Database Connections*, select the service to which you want to bind your application \(for example, ![](images/BAS_icon_dependencyNotBound_1694e4a.svg)*cross-container-service-1*\), and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).

    2.  Select the target schema service

        In the list of options displayed, choose *Bind to a schema service* and choose *MySchema hana \(schema\)*.


    The status of the database connection changes to ![](images/BAS_icon_dependencyBound_e45e7a9.svg)*cross-container-service-1 \(MySchema\)*.

4.  Unbind your database application from a schema service.

    Use the *Database Connections* node to display a the list of available schema service instances and their current status.

    1.  In the list of database connections, locate the schema service instance from which you want to unbind your database application and choose ![](images/BAS_icon_unbind_3f54cf3.svg) \(*Unbind*\).

        -   Bound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyBound_e45e7a9.svg)*cross-container-service-1 \(MySchemaService\)* 


    2.  Check the status of the schema service.

        On completion of the unbinding operation, the binding status is displayed in the *Database Connections* node, for example:

        -   Unbound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyNotBound_1694e4a.svg)*cross-container-service-1* 




**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[Bind an Application to an HDI-Container Service](bind-an-application-to-an-hdi-container-service-6db6afa.md "")

[Bind an Application to a User-Provided Service](bind-an-application-to-a-user-provided-service-274e8c1.md "")

[Bind an Application to a Service Managed by the Service Manager](bind-an-application-to-a-service-managed-by-the-service-manager-818a87c.md "You can bind an application's database module to a service managed by SAP Service manager.")

[Permissions for Objects in HDI Containers](../040-HANA-Cloud-DB-Dev-Persistence-Model/permissions-for-objects-in-hdi-containers-79e8664.md "The owner of a container object needs additional privileges to the ones assigned by default.")

