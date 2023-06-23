<!-- loio6db6afae316847b99c5a78b6eb2e292e -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind an Application to an HDI-Container Service



<a name="loio6db6afae316847b99c5a78b6eb2e292e__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project \(FlightReservation\) you created in the previous tutorial is available.
-   The application project contains a database module called *db*.
-   The database module has been built and bound to the deploy service and the module's assigned HDI container.

    > ### Tip:  
    > If the database module is not yet bound to any service, you can bind it as part of this tutorial.




## Context

If you are developing native SAP HANA applications in SAP Business Application Studio, you can use the *SAP HANA PROJECTS* explorer to deploy the application's artifacts to the SAP HANA database and display an overview of the deployment status, for example, to see which objects are pending deployment. You can also manage the application's connections to the SAP HANA database, for example, to create a new connection that enables you to bind an application to the **default HDI container** or a non-default service such as a user-provided service, a schema service, or a service managed by the Service Manager.

When you create a new database application project, the application's database module is bound by default to its own, new HDI container in the SAP HANA database by means of a Cloud Foundry service. However, you can change this behavior, for example, by choosing not to create a default service or binding the application's database module to another service, which you select from a list displayed by the database-connections Wizard.

> ### Tip:  
> In the *SAP HANA PROJECTS* explorer, the name of the bound service is displayed \(in brackets\) for each item in the list of *Database Connections*, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*, along with the current binding status, for example: ![](images/BAS_icon_targetContainerBound_5c18d02.svg) \(*bound container*\) or ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) \(*unbound container*\).

Services bound to a database module are local to a Cloud Foundry space. More specifically, the services are taken from the space that you are logged to on at the time of the bind operation. If you subsequently change to another Cloud Foundry space, the bound services still reference the old Cloud Foundry space, which can cause problems for the application. To ensure that the original services are automatically unbound if the underlying Cloud Foundry space changes, you can set the following user preferences:

:gear:: *Settings* \> *Workspace* \> *SAP HANA Project Explorer* \> ****Unbind: Unbind all services if the Cloud Foundry space changes**.

You can use the *SAP HANA PROJECTS* explorer to set up a database connection, as described below:

To bind an application to an HDI container service, perform the following steps:



## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Expand the *FlightReservation/db* and *Database Connections* nodes.

3.  Add a connection to an existing HDI container service to SAP HANA Database Explorer \(*Optional*\).

    If the target container to which you want to bind your application is not already included in the list displayed in *Database Connections*, you need to add it, as follows:

    1.  Open the *Add Database Connection* Wizard.

        In the *Database Connections* node, choose <span class="SAP-icons"></span> \(Add database connection\) to display the *Add Database Connection* Wizard.

        > ### Note:  
        > To test the connection details \(for example, the host name, port number, user name and password\), check the option *Validate the database information*. The *Add database Connection* Wizard tries to connect to the specified database using the credentials provided and notifies you immediately if the connection attempt is successful or not.

    2.  Select the connection type.

        Specify which type of connection you want to add, for example, *Existing HDI Container* and type ***Flight*** in the *Select SAP HANA HDI service instance name* box.

    3.  Choose the HDI container that you want to connect to.

        In the list of HDI containers displayed choose the HDI container that you want to add as a target for the new database connection, for example, *FlightReservation-hdidb-ws-12345*, and choose *Add*.


    The SAP HANA Database Explorer displays the bound HDI-container service in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*.

    > ### Caution:  
    > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container.

    If the contents of the new application's database module do not match the contents deployed by the application that was originally bound to the container service, then by default all unmatched files are automatically undeployed when you deploy the new application.

    > ### Tip:  
    > To help prevent the undeployment of unmatched files during deployment, you can set the project preferences in SAP Business Application Studio to display warning messages, as described in the next steps.

4.  Bind an application to an HDI-container service.

    You can choose between the following target services:

    -   Bind a database module to the **default** \(HDI-container\) service.
    -   Bind a database module to an existing, non-default \(HDI-container\) service.
    -   Bind a database module to a **new** \(HDI-container\) service.

    > ### Tip:  
    > Each of these options is described in detail in the following steps.

    1.  Bind a database module to the **default** \(HDI-container\) service.

        Typically, an application's database module is bound to the \(HDI-container\) service that is created by default for the application during the creation of the application project. If your application is not already bound to the default service \(or the default service does not yet exist\), you can bind it manually, as follows:

        > ### Caution:  
        > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container, as described in the previous steps.

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *Bind to the default service \(MyApp-hdidb-ws-12345\)*.

            The name of the default service is displayed in brackets \(*MyApp-hdidb-ws-12345* in the example above\) based on the following information: "*<ProjectName\>*-hdidb-ws-*<WorkspaceName\>*". If the indicated service does not exist, it is created automatically as part of the binding process.

            > ### Note:  
            > If the database ID of the specified service does not match the database ID of the SAP HANA application's database module as specified in the application project's `mta.yaml` file, SAP Business Application Studio requires you to confirm or cancel the requested binding action.

        3.  The module is bound to the selected service, and the new binding status is displayed alongside the connection in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(MyApp-hdidb-ws-12345\)*.

    2.  Bind a database module to an existing, non-default \(HDI-container\) service.

        You can bind an application's database module to an HDI-container service that is not the one selected by default during the creation of the application project. It is important to note, however, that changing the default behavior can lead to unintended and undesired consequences. It is also possible to use the *Bind all* option in the *Database Connections* pane to bind to **all** the services specified in the application's `mta.yaml` file. If your application is not already bound to an HDI container service, you can bind it manually, as follows:

        > ### Caution:  
        > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container, as described in the previous steps.

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *MyApp-hdidb-ws-54321\(hdi-shared\)* from the list of existing services displayed.

            > ### Tip:  
            > To search for an existing service name, type part of the name into the *Select an SAP HANA Service* box, for example, "***MyApp***" or "***54321***".

        3.  The module is bound to the selected service and the new binding status is displayed alongside the service name \(in brackets\) in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(MyApp-hdidb-ws-54321\)*.

    3.  Bind a database module to a **new** \(HDI-container\) service.

        If you chose not to bind an application's database module to the HDI-container service that is created by default during the creation of the application project, or you chose not to create a default HDI-container service for your application project, you can perform these tasks manually, as follows:

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *\+ Create a new service* in the service-creation Wizard.

            The service-creation Wizard suggests a name for the new service, using the following format: **<AppName\>*-hdidb-ws-*<WorkspaceID\>**

        3.  The module is bound to the new service, and the new binding status is displayed alongside the service name \(in brackets\) in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*.


5.  Unbind an application from an HDI-container service.

    Use the *Database Connections* node to display a the list of available HDI container service instances and their current status.

    1.  In the list of database connections, locate the HDI-container service instance from which you want to unbind your database application and choose ![](images/BAS_icon_unbind_3f54cf3.svg) \(*Unbind*\).

        -   Bound "target" HDI container services:

            ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_db \(MyApp-hdidb-ws-123\)*


    2.  Check the status of the HDI container service.

        On completion of the unbinding operation, the binding status is displayed in the *Database Connections* node, for example:

        -   Unbound "target" HDI container services:

            ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdb\_db* 




**Related Information**  


[Bind an Application to a User-Provided Service](bind-an-application-to-a-user-provided-service-274e8c1.md "")

[Bind an Application to a Database Schema Service](bind-an-application-to-a-database-schema-service-4f5add9.md "")

[Bind an Application to a Service Managed by the Service Manager](bind-an-application-to-a-service-managed-by-the-service-manager-818a87c.md "You can bind an application's database module to a service managed by SAP Service manager.")

[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

