<!-- loioa3865b12c0354c9fa312f88aa4572b7b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Bind Applications to Database Services with SAP HANA Projects Explorer

Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.



<a name="loioa3865b12c0354c9fa312f88aa4572b7b__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.
-   The database module has been built and bound to the deploy service and the module's assigned HDI container.

    > ### Tip:  
    > If the database module is not yet bound to any service, you can bind it as part of this tutorial.




## Context

If you are developing native SAP HANA applications in SAP Business Application Studio, you can use the *SAP HANA PROJECTS* explorer to deploy the application's artifacts to the SAP HANA database and display an overview of the deployment status, for example, to see which objects are pending deployment. You can also manage the application's connections to the SAP HANA database, for example:

-   The SAP HDI container where the application's database artifacts are deployed

-   Any new or existing user-defined or managed services that are required




## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Display the run-time contents deployed to the HDI container that is bound to a database application.

    An SAP HANA native database application is bound by default to its own HDI container by means of a service instance created when setting up the application project in SAP Business Application Studio. You can change this behaviour during the setup process, for example, by choosing to bind to an alternative service instance. The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application.

    In the *SAP HANA PROJECTS* explorer, locate the application that contains the database artifacts you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    The selected HDI container is displayed in the *SAP HANA Database Explorer*, which enables you to browse through the different categories of database artifacts in the catalog, for example, *Tables*, *Views*, *Column Views*, etc.

3.  Bind an application to a database service.

    In the *SAP HANA PROJECTS* explorer, you can bind your application's database module to the following type of database service:

    -   The default \(or a non-default\) HDI-container
    -   A user-provided service
    -   A database schema service
    -   A service managed by the service-manager \(HDI container or schema service\)

    > ### Tip:  
    > For instructions that describe how to bind an application to a particular service type, see *Related Information* below.

4.  Add a connection to an existing HDI container service to SAP HANA Database Explorer \(optional\).

    In the *Database Connections* node, choose <span class="SAP-icons"></span> \(Add database connection\) to display the *Add Database Connection* Wizard.

    > ### Note:  
    > To test the connection details \(for example, the host name, port number, user name and password\), check the option *Validate the database information*. The *Add database Connection* Wizard tries to connect to the specified database using the credentials provided and notifies you immediately if the connection attempt is successful or not.

    Select the connection type, for example, *Existing HDI Container* and type ***Flight*** in the *Select SAP HANA HDI service instance name* box. In the list of HDI containers displayed choose the HDI container you want to add, for example, *FlightReservation-hdidb-ws-12345*, and choose *Add*.

    The SAP HANA Database Explorer displays the bound HDI-container service in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*.

    > ### Caution:  
    > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container.

    If the contents of the new application's database module do not match the contents deployed by the application that was originally bound to the container service, then by default all unmatched files are automatically undeployed when you deploy the new application.

    > ### Tip:  
    > To help prevent the undeployment of unmatched files during deployment, you can set the project preferences in SAP Business Application Studio to display warning messages, as described in the next steps.

5.  Manage the user preferences for messages displayed during binding operations. \(Optional\)

    1.  Display a confirmation message to warn users about the consequences of binding to an existing container service. \(Optional\)

        Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of unmatched artifacts from a previous deployment. To help prevent the deletion of already deployed artifacts, you can configure the *SAP HANA Projects* explorer to display a warning message when a user binds an application's database module to an existing service, as follows:

        :gear:: *Settings* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm existing service*.

        The notification displays the following options:

        -   *Continue*

            Bind the current database application to the selected service and proceed to the next option. Before the bind operation finishes, the bind-service Wizard displays a warning about auto-undeployment, and requires you to choose one of the provided options.

        -   *Cancel*

            Do not bind the current database application to the selected service, cancel the bind-service operation, and close the message window.


    2.  Display a prompt to confirm the disabling of the auto-undeployment of unmatched artifacts. \(Optional\)

        Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of unmatched artifacts that were created during a previous deployment. To help prevent the deletion of unmatched deployed artifacts, you can configure the *SAP HANA Projects* explorer to display a warning message and prompt regarding auto-undeployment when they try to bind an application's database module to an existing service, as follows:

        :gear:: *Settings* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm automatic undeployment*.

        -   *Enable* 

            Allow the automatic undeployment of unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

        -   *Disable* \(automatic undeployment\)

            Do **not** allow the automatic undeployment of unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

            > ### Tip:  
            > Even if you **disable** automatic undeployment, you can still ensure that individual files are undeployed during the redeployment of the database application by adding the files to an *allow list* defined in the file `db/undeploy.json`. For more details about setting up the `undeploy.json` file, see *HDI Delta Deployment and Undeploy Allow List* in *Related Information*.




**Related Information**  


[Bind an Application to an HDI-Container Service](bind-an-application-to-an-hdi-container-service-6db6afa.md "")

[Bind an Application to a User-Provided Service](bind-an-application-to-a-user-provided-service-274e8c1.md "")

[Bind an Application to a Database Schema Service](bind-an-application-to-a-database-schema-service-4f5add9.md "")

[Bind an Application to a Service Managed by the Service Manager](bind-an-application-to-a-service-managed-by-the-service-manager-818a87c.md "You can bind an application's database module to a service managed by SAP Service manager.")

[Deploy Artifacts with SAP HANA Projects Explorer](deploy-artifacts-with-sap-hana-projects-explorer-4bbbaae.md "Use the SAP HANA Projects explorer to deploy and view your application's design- and run-time database artifacts.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

