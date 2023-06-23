<!-- loio818a87c6299a43488f80f92fa8453d4b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind an Application to a Service Managed by the Service Manager

You can bind an application's database module to a service managed by SAP Service manager.



<a name="loio818a87c6299a43488f80f92fa8453d4b__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project \(*FlightReservation* in this example\) that you want to bind is available.
-   The application project contains a database module called *db*.

    > ### Tip:  
    > If the database module is not yet bound to any service, you can bind it as part of this tutorial.




## Context

The *SAP HANA PROJECTS* explorer includes tools that enable you to manage the bindings to any database services required by your SAP HANA database application. You can bind an application to a service instance in the current Cloud Foundry space or a service instance that is managed by SAP Service Manager: a so-called *application-managed service instance*. The application-managed service instance can be bound to a default **target** \(HDI\) container or a "non-target" container in the form of another HDI container or a schema service \(a "`hana`" service with a "`schema`" service plan\).

> ### Tip:  
> SAP Service Manager is the central registry for service brokers and platforms in SAP BTP and enables the management of platforms, service brokers, service instances, and service bindings. SAP BTP cockpit provides access to SAP Service Manager, but you can also use the command-line interface or a REST API. For more information, see *Related Information* below.

To use the *SAP HANA PROJECTS* explorer in SAP Business Application Studio to bind an application to an application-managed service instance, perform the following steps:



## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Add a new database connection. \(*Optional*\)

    The list of existing services is displayed in *Database Connections* along with the current binding status, for example: ![](images/BAS_icon_dependencyBound_e45e7a9.svg) \(*bound service*\) or ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) \(*unbound service*\). If your application is already bound to a service, the name of the bound service is included \(in brackets\), for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_db \(MyApp-hdidb-ws-123\)* for "target" HDI container services or ![](images/BAS_icon_dependencyBound_e45e7a9.svg) *cross-container-service-1 \(MySchemaService\)* for "non-target" container services, for example, a schema service.

    If the service to which you want to bind your application is not included in the list of available services displayed in *Database Connections*, you need to add it, as follows:

    1.  Add a connection to a target HDI container.

        Use the <span class="SAP-icons"></span> \(Add database connection\) tool in the *Database Connections* node to start the *Add Database Connection* Wizard, choose the connection type *Existing HDI Container*, and select the managed service instance listed in the drop-down list of options, for example, *hdb\_db \(MyApp-hdidb-ws-ab123c\)*.

    2.  Add a connection to a non-target HDI container.

        Use the <span class="SAP-icons"></span> \(Add database connection\) tool in the *Database Connections* node to start the *Add Database Connection* Wizard, choose the connection type *Existing schema service instance*, and select the managed service instance listed in the drop-down list of options, for example, *MySchema managed-hana \(schema\)*.


    The new connection is displayed in the list of database connections under the *Database Connections* node in the *SAP HANA PROJECTS* pane, for example, ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db* or ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) *cross-container-service-1*.

3.  Bind a database application to an application-managed service instance.

    Use the *Database Connections* node to display a the list of available application-managed service instances and their current status. You can bind your application to an application-managed HDI container or schema service.

    1.  In the list of database connections, locate the managed service instance to which you want to bind your database application and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).

        -   Unbound "target" HDI container services:

            ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdb\_db* 

        -   Unbound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) *cross-container-service-1* 


    2.  Select a binding option.

        You can choose either of the following options:

        -   *Bind to an HDI container*
        -   *Bind to an application-managed HDI container* \(target containers\)
        -   *Bind to an application-managed service instance* \(non-target containers\)

    3.  Specify a service-manager instance.

        In the list of service-manager instances displayed by the binding Wizard, choose the service manager which manages the service instance to which you want to bind your application's database module, for example:

        -   *ServiceManager01*
        -   *ServiceManager02*

        The bind Wizard displays a list of the service instances managed by the service manager you choose.

    4.  Choose the HDI container or service to which you want to bind your application.

        In the list of SAP HANA services displayed, select a target HDI container or service instance, for example:

        -   HDI container: *MyApp-hdi\_db hana \(hdi-shared\)*
        -   Schema service: *SMS1 hana \(schema\)*

    5.  Check the status of the application-managed HDI container or schema service.

        On completion of the binding operation, the binding status is displayed in the *Database Connections* node, for example:

        -   Bound "target" HDI container services:

            ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_db \(MyApp-hdidb-ws-123\)*

        -   Bound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyBound_e45e7a9.svg) *cross-container-service-1 \(MySchemaService\)* 



4.  Unbind a database application from an application-managed service instance.

    Use the *Database Connections* node to display a the list of available managed service instances and their current status. You can unbind your database application from an application-managed HDI container or schema service.

    1.  In the list of database connections, locate the application-managed service instance from which you want to unbind your database application and choose ![](images/BAS_icon_unbind_3f54cf3.svg) \(*Unbind*\).

        -   Bound "target" HDI container services:

            ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_db \(MyApp-hdidb-ws-123\)*

        -   Bound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyBound_e45e7a9.svg) *cross-container-service-1 \(MySchemaService\)* 


    2.  Check the status of the application-managed HDI container or schema service.

        On completion of the unbinding operation, the binding status is displayed in the *Database Connections* node, for example:

        -   Unbound "target" HDI container services:

            ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdb\_db* 

        -   Unbound "non-target" container services, for example, a schema service:

            ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) *cross-container-service-1* 




**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[Bind an Application to an HDI-Container Service](bind-an-application-to-an-hdi-container-service-6db6afa.md "")

[Bind an Application to a User-Provided Service](bind-an-application-to-a-user-provided-service-274e8c1.md "")

[Bind an Application to a Database Schema Service](bind-an-application-to-a-database-schema-service-4f5add9.md "")

[SAP Service Manager](https://help.sap.com/docs/service-manager/sap-service-manager/sap-service-manager?version=Cloud)

