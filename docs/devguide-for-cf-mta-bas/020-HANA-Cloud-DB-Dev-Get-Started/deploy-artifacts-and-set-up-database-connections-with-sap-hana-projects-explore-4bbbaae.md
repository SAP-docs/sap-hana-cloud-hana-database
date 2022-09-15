<!-- loio4bbbaae1d8694005adcfe1ec06a5cd46 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Deploy Artifacts and Set up Database Connections with SAP HANA Projects Explorer

Use the SAP HANA Projects explorer to deploy and manage your application's database artifacts and connections.



<a name="loio4bbbaae1d8694005adcfe1ec06a5cd46__prereq_tql_yyh_qmb"/>

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

-   Any new or existing user-defined services that are required.




## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Choose how to display the contents of the application's database module.

    By default, the *SAP HANA PROJECTS* explorer uses the ![](images/BAS_icon_listTree_c55a137.svg) \(*tree*\) view to display all the artifacts and folders in the database module of the application that you are working on, regardless of whether the artifacts are deployed or not.

    If you want to see only those database objects that are pending deployment, hover the mouse cursor over the *SAP HANA PROJECTS* explorer pane's title and choose <span class="FPA-icons"></span> \(Pending Deployment\) . The ![](images/BAS_icon_pendingDeploymentFolder_eefbce6.svg) *Pending Deployment \(\#\)* view displays a single folder that contains any database artifacts awaiting deployment, where "\#" is the number of artifacts currently in the folder.

3.  Deploy an application's database artifacts to the SAP HANA database.

    You can choose to deploy **all** an application's database artifacts or any individual artifacts. To maintain dependencies between artifacts, it is recommended to deploy all artifacts.

    In the *SAP HANA PROJECTS* explorer, select either the application's database module \(for example, *FlightReservation/db*\) or one or more individual database artifact \(for example, *PASSENGERS.hdbtable*\) and choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

    > ### Tip:  
    > If you want to deploy multiple individual artifacts from your database module, select the artifacts that you want to deploy using the [Ctrl\] key, then choose ![](images/BAS_icon_deploy_multiple_6fd14bf.svg) \(*Deploy all selected files*\).

    The *SAP HANA PROJECTS* explorer displays the flag *\(pending deployment\)* alongside any database artifact that has not yet been deployed to its target HDI container in the SAP HANA database. If you want to compare and synchronize the artifacts that are pending deployment with the version of the artifacts already deployed to the database, hover the mouse cursor over the name of the database module that contains the artifacts that are pending deployment, for example, *FlightReservation/db \(pending deployment\)* and choose :arrows_clockwise:.

    > ### Note:  
    > If the selected database module \(for example, *FlightReservation/db*\) is not bound to an HDI container, it is not possible to synchronize the deployment status. You will have to bind the database module's target container to its HDI container service and try again. In larger application projects, the synchronization can take some time.

    After synchronization completes, the *\(pending deployment\)* flag is only displayed alongside those artifacts whose design-time version in your application's database module is newer than the run-time version currently deployed to the database. Choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\) to deploy the newer version.

4.  Display the run-time contents deployed to the HDI container that is bound to a database application.

    The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application.

    In the *SAP HANA PROJECTS* explorer, locate the application that contains the database artifacts you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    The selected HDI container is displayed in the *SAP HANA Database Explorer*, which enables you to browse through the different categories of database artifacts in the catalog, for example, *Tables*, *Views*, *Column Views*, etc.

5.  Bind an application to an HDI-container service. \(**optional**\)

    When you create a new database application project, the application's database module is bound by default to its own, new HDI container in the SAP HANA database by means of a Cloud Foundry service. However, you can change this behavior, for example, by choosing not to create a default service or binding the application's database module to another service, which you select from a list displayed by the database-connections Wizard.

    > ### Tip:  
    > The name of the bound service is displayed \(in brackets\) for each item in the list of *Database Connections*, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*, along with the current binding status, for example: ![](images/BAS_icon_targetContainerBound_5c18d02.svg) \(*bound container*\) or ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) \(*unbound container*\).

    Services bound to a database module are local to a Cloud Foundry space. More specifically, the services are taken from the space that you are logged to on at the time of the bind operation. If you subsequently change to another Cloud Foundry space, the bound services still reference the old Cloud Foundry space, which can cause problems for the application. To ensure that the original services are automatically unbound if the underlying Cloud Foundry space changes, you can set the following user preference in *Settings*:

    :gear:: *Preferences* \> *Workspace* \> *SAP HANA Project Explorer* \> ****Unbind: Unbind all services if the Cloud Foundry space changes**.

    You can use the *SAP HANA PROJECTS* explorer to set up a database connection, as described below:

    1.  Expand the *FlightReservation/db* and *Database Connections* nodes.

    2.  Add a connection to an existing HDI container service to SAP HANA Database Explorer \(optional\).

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

    3.  Bind a database module to the **default** \(HDI-container\) service.

        Typically, an application's database module is bound to the \(HDI-container\) service that is created by default for the application during the creation of the application project. If your application is not already bound to the default service \(or the default service does not yet exist\), you can bind it manually, as follows:

        > ### Caution:  
        > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container, as described in the previous steps.

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *Bind to the default service \(MyApp-hdidb-ws-12345\)*.

            The name of the default service is displayed in brackets \(*MyApp-hdidb-ws-12345*\) based on the following information: "*<ProjectName\>*-hdidb-ws-*<WorkspaceName\>*". If the indicated service does not exist, it is created automatically as part of the binding process.

            > ### Note:  
            > If the database ID of the specified service does not match the database ID of the SAP HANA application's database module as specified in the application project's `mta.yaml` file, SAP Business Application Studio requires you to confirm or cancel the requested binding action.

        3.  The module is bound to the selected service, and the new binding status is displayed alongside the connection in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(MyApp-hdidb-ws-12345\)*.

    4.  Bind a database module to an existing, non-default \(HDI-container\) service.

        You can bind an application's database module to an HDI-container service that is not the one selected by default during the creation of the application project. It is important to note, however, that changing the default behavior can lead to unintended and undesired consequences. It is also possible to use the *Bind all* option in the *Database Connections* pane to bind to **all** the services specified in the application's `mta.yaml` file. If your application is not already bound to an HDI container service, you can bind it manually, as follows:

        > ### Caution:  
        > Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of artifacts from a previous deployment to the target container, as described in the previous steps.

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *MyApp-hdidb-ws-54321\(hdi-shared\)* from the list of existing services displayed.

            > ### Tip:  
            > To search for an existing service name, type part of the name into the *Select an SAP HANA Service* box, for example, "***MyApp***" or "***54321***".

        3.  The module is bound to the selected service and the new binding status is displayed alongside the service name \(in brackets\) in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(MyApp-hdidb-ws-54321\)*.

    5.  Bind a database module to a **new** \(HDI-container\) service.

        If you chose not to bind an application's database module to the HDI-container service that is created by default during the creation of the application project, or you chose not to create a default HDI-container service for your application project, you can perform these tasks manually, as follows:

        1.  In the *Database Connections* node, select the database module that you want to bind \(![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) *hdi\_db*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).
        2.  Choose *\+ Create a new service* in the service-creation Wizard.

            The service-creation Wizard suggests a name for the new service, using the following format: **<AppName\>*-hdidb-ws-*<WorkspaceID\>**

        3.  The module is bound to the new service, and the new binding status is displayed alongside the service name \(in brackets\) in the *Database Connections* node, for example, ![](images/BAS_icon_targetContainerBound_5c18d02.svg) *hdb\_di \(FlightReservation-hdidb-ws-12345\)*.

    6.  Display a confirmation message to warn users about the consequences of binding to an existing container service.

        Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of unmatched artifacts from a previous deployment. To help prevent the deletion of already deployed artifacts, you can configure the *SAP HANA Projects* explorer to display a warning message when a user binds an application's database module to an existing service, as follows:

        :gear:: *Preferences* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm existing service*.

        The notification displays the following options:

        -   *Continue*

            Bind the current database application to the selected service and proceed to the next option. Before the bind operation finishes, the bind-service Wizard displays a warning about auto-undeployment, and requires you to choose one of the provided options.

        -   *Cancel*

            Do not bind the current database application to the selected service, cancel the bind-service operation, and close the message window.


    7.  Display a prompt to confirm the disabling of the auto-undeployment of unmatched artifacts.

        Binding an application's database module to an existing \(HDI-container\) service can lead to problems caused by the automatic removal of unmatched artifacts that were created during a previous deployment. To help prevent the deletion of unmatched deployed artifacts, you can configure the *SAP HANA Projects* explorer to display a warning message and prompt regarding auto-undeployment when they try to bind an application's database module to an existing service, as follows:

        :gear:: *Preferences* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm automatic undeployment*.

        -   *Enable* 

            Allow the automatic undeployment of unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

        -   *Disable* \(automatic undeployment\)

            Do **not** allow the automatic undeployment of unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

            > ### Tip:  
            > Even if you **disable** automatic undeployment, you can still ensure that individual files are undeployed during the redeployment of the database application by adding the files to an *allow list* defined in the file `db/undeploy.json`. For more details about setting up the `undeploy.json` file, see *HDI Delta Deployment and Undeploy Allow List* in *Related Information*.



6.  Bind \(or unbind\) your database application to \(or from\) a user-provided service.

    The *SAP HANA PROJECTS* explorer includes tools that enable you to manage the bindings to any user-provided services required by your SAP HANA database application. You can bind an application either to a new user-provided service that you create using the <span class="SAP-icons"></span> \(Add database connection\) tool in the *Database Connections* node or to a user-provided service that already exists.

    > ### Tip:  
    > The list of user-provided services is displayed in *Database Connections* along with the current binding status, for example: ![](images/BAS_icon_dependencyBound_e45e7a9.svg) \(*bound service*\) or ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) \(*unbound service*\). If a service is already bound to your application, the name of the bound service is included \(in brackets\), for example, *cross-container-service-1 \(UPS\)*.

    1.  Add a new database connection.

        Use the <span class="SAP-icons"></span> \(Add database connection\) tool in the *Database Connections* node to start the *Add Database Connection* Wizard and choose the connection type *Create user-provided service instance* and the option *Use deployment target container database*.

        You will need to provide the credentials of the user who manages the user-provided service, and you have the option of using a procedure grantor and \(or\) an hdbgrants file to assign the privileges required for access to the user-provided service and the objects it reveals.

        -   *Procedure grantor*

            This is required if you are using a procedure rather than a database user to grant the privileges required to use a new user-provided service. You will need to provide the name of the procedure that assigns the privileges and the name of the schema where the procedure is located.

        -   *Generate hdbgrants file*

            Select this option if you want to create a grants file that can be used to assign privileges to the owner and consumer of database objects in the HDI container assigned to this database connection. The hdbgrants file is created with a basic template that you can use to suit your requirements.


    2.  Bind a user-provided service to your database application.

        In the list of services displayed in *Database Connections*, select the user-provided service to which you want to bind your application \(for example, ![](images/BAS_icon_dependencyNotBound_1694e4a.svg) *cross-container-service-2*\) and choose ![](images/BAS_icon_bind_074ce84.svg) \(*Bind*\).

    3.  Unbind a user-provided service from your database application.

        In the list of services displayed in *Database Connections* select the user-provided service from which you want to unbind your application \(for example, ![](images/BAS_icon_dependencyBound_e45e7a9.svg) *cross-container-service-1 \(UPS\)*\) and choose ![](images/BAS_icon_unbind_3f54cf3.svg) \(*Unbind*\).



**Related Information**  


[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

