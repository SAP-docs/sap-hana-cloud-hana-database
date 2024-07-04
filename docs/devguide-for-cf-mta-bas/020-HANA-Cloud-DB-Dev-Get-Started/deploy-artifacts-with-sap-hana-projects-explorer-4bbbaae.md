<!-- loio4bbbaae1d8694005adcfe1ec06a5cd46 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Deploy Artifacts with SAP HANA Projects Explorer

Use the SAP HANA Projects explorer to deploy and view your application's design- and run-time database artifacts.



<a name="loio4bbbaae1d8694005adcfe1ec06a5cd46__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.
-   The database module has been built and bound to the deploy service and the module's assigned HDI container.

    > ### Tip:  
    > If the database module is not yet bound to any service, the previous tutorial, *Bind Applications and Add Database Connections with SAP HANA Projects Explorer*, provides step-by-step instructions to perform the task. See *Related Information* below.




## Context

If you are developing native SAP HANA applications in SAP Business Application Studio, you can use the *SAP HANA PROJECTS* explorer to deploy the application's artifacts to the SAP HANA database and display an overview of the deployment status, for example, to see which objects are pending deployment.



## Procedure

1.  Open the *SAP HANA PROJECTS* explorer.

2.  Choose how to display the contents of the application's database module.

    By default, the *SAP HANA PROJECTS* explorer uses the ![](images/BAS_icon_listTree_c55a137.svg) \(*tree*\) view to display all the artifacts and folders in the database module of the application that you are working on, regardless of whether the artifacts are deployed or not.

    If you want to see only those database objects that are pending deployment, hover the mouse cursor over the *SAP HANA PROJECTS* explorer pane's title and choose <span class="FPA-icons-V3"></span> \(Pending Deployment\) . The ![](images/BAS_icon_pendingDeploymentFolder_eefbce6.svg)*Pending Deployment \(\#\)* view displays a single folder that contains any database artifacts awaiting deployment, where "\#" is the number of artifacts currently in the folder.

3.  Deploy an application's database artifacts to the SAP HANA database.

    You can choose to deploy **all** an application's database artifacts or any individual artifacts. To maintain dependencies between artifacts, it is recommended to deploy all artifacts.

    > ### Note:  
    > If the HDI deployer version defined in <code><i class="varname">&lt;MyApp&gt;</i>/db/node_modules/@sap/hdi-deploy/package.json</code> is outdated SAP Business Application Studio displays a warning with information that describes how to trigger an upgrade. For example, to force an upgrade of the HDI deployer, you will need to delete the <code><i class="varname">&lt;Myapp&gt;</i>/db/package-lock.json</code> file as well as the folder <code><i class="varname">&lt;MyApp&gt;</i>/db/node_modules</code> and then deploy the application again.

    In the *SAP HANA PROJECTS* explorer, select either the application's database module \(for example, *FlightReservation/db*\) or one or more individual database artifact \(for example, *PASSENGERS.hdbtable*\) and choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

    > ### Tip:  
    > To deploy multiple individual artifacts from your database module, select the artifacts that you want to deploy while pressing the [Ctrl\] key, then choose ![](images/BAS_icon_deploy_multiple_6fd14bf.svg) \(*Deploy all selected files*\).

    If changes are made to an application project after deployment, the *SAP HANA PROJECTS* explorer displays the flag *\(pending deployment\)* alongside any new or modified database artifact that has not yet been deployed to its target HDI container in the SAP HANA database. If you want to compare and synchronize the artifacts that are pending deployment with the version of the artifacts already deployed to the database, hover the mouse cursor over the name of the database module that contains the artifacts that are pending deployment, for example, *FlightReservation/db \(pending deployment\)* and choose :arrows_clockwise:.

    > ### Note:  
    > If the selected database module \(for example, *FlightReservation/db*\) is not bound to an HDI container, it is not possible to synchronize the deployment status. You will have to bind the database module's target container to its HDI container service and try again. In larger application projects, the synchronization can take some time.

    After synchronization completes, the *\(pending deployment\)* flag is only displayed alongside those artifacts whose design-time version in your application's database module is newer than the run-time version currently deployed to the database. Choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\) to deploy the newer version.

    > ### Tip:  
    > In the SAP HANA Native Application dev space for SAP Business Application Studio, the HDI deployer does not stop immediately if it encounters an error during deployment. Instead, it tries to clean up and close gracefully. This is the default behaviour. If multiple artifacts are being deployed in parallel, multiple deployment errors could produce multiple error messages. Setting the `stop_on_error` parameter explicitly in the application's `package.json` file has no effect.

4.  Display the run-time contents deployed to the HDI container that is bound to a database application.

    The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application.

    In the *SAP HANA PROJECTS* explorer, locate the application that contains the database artifacts you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    The selected HDI container is displayed in the *SAP HANA Database Explorer*, which enables you to browse through the different categories of database artifacts in the catalog, for example, *Tables*, *Views*, *Column Views*, etc.

5.  Manage database connections. \(**optional**\)

    The *SAP HANA PROJECTS* explorer displays all currently configured connections to the SAP HANA database in the *Database Connections* node, which you can use to add a new database connection, as described below. You can add any of the connection types listed in the following table:


    <table>
    <tr>
    <th valign="top">

    Database Connection Type
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Existing HDI Container*
    
    </td>
    <td valign="top">
    
    Connect to an HDI container that has already been created and is available.

    > ### Caution:  
    > Binding an application's database module to an existing HDI container \(service\) can lead to problems caused by the automatic removal of existing artifacts from a previous deployment. See below for more information about alternative setups and workarounds.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Existing user-provided service instance*
    
    </td>
    <td valign="top">
    
    Connect to a specific instance of a user-provided service that has already been created.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Create user-provided service instance*
    
    </td>
    <td valign="top">
    
    Connect to a new instance of a user-provided service that you create while setting up the connection.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Existing schema service instance*
    
    </td>
    <td valign="top">
    
    Connect to an existing instance of a "`hana`" service with the "`schema`" service plan.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Existing application-managed service instance*
    
    </td>
    <td valign="top">
    
    Connect to an existing instance of an application-managed service.

    > ### Tip:  
    > You need to know the name of the service-manager instance that is managing the service instance you want to connect to.


    
    </td>
    </tr>
    </table>
    
    The process for setting up the various types of database connection is very similar, but in this step, we set up a connection to an existing HDI container which can then be bound to the database module of your application, as follows::

    1.  Open the *SAP HANA PROJECTS* explorer.

    2.  Expand the *FlightReservation/db* and *Database Connections* nodes.

        An SAP HANA application project is bound to an HDI container in the SAP HANA database. The name of the bound container is displayed in *Database Connections* node along with the current binding status, for example: ![](images/BAS_icon_targetContainerBound_5c18d02.svg) \(*bound container*\) or ![](images/BAS_icon_targetContainerNotBound_193ce0c.svg) \(*unbound container*\).

    3.  Add a database connection to the SAP HANA Database Explorer.

        In the *Database Connections* node, choose <span class="SAP-icons-V5"></span> \(Add database connection\) to display the *Add Database Connection* Wizard.

        > ### Note:  
        > To test the connection details \(for example, the host name, port number, user name and password\), check the option *Validate the database information*. The *Add database Connection* Wizard tries to connect to the specified database using the credentials provided and notifies you immediately if the connection attempt is successful or not.

        Select the connection type, for example, *Existing HDI Container* and type `Flight` into the *Select SAP HANA HDI service instance name* box. In the list of HDI containers displayed choose the HDI container you want to add, for example, *FlightReservation-hdidb-workspaces-ws-12345*, and choose *Add*.

        The selected HDI container is displayed in the SAP HANA Database Explorer.

    4.  Bind a database module to an HDI container \(service\).

        When you create a new database application project, the application's database module is bound by default to a new HDI container by means of a Cloud Foundry service. However, you can change this behavior, for example, by choosing to bind the database module to an **existing** container \(service\), which you select from a list displayed in the *Database Connections* node or while setting up a new database connection in the database-connections Wizard.

        > ### Caution:  
        > Binding an application's database module to an existing HDI container \(service\) can lead to problems caused by the automatic removal of existing artifacts from a previous deployment.

        If the content of the new application's database module does not match the content deployed by the application that was originally bound to the service, then by default all unmatched files are automatically undeployed when you deploy the new application. You can manage the removal of deployed files with an "undeploy allow list" as described in *Related Information* below.

        > ### Tip:  
        > To help prevent the undeployment of unmatched files during deployment, you can set the project preferences in SAP Business Application Studio to display warning messages, as described in *Bind Applications to Database Services with SAP HANA Projects Explorer* in *Related Information* below.

    5.  Manage access to a database connection.

        The SAP HANA Project Explorer provides context-sensitive options that enable you to allow other users and roles to use a selected database connection, for example, as part of development and testing activities. The options *User Management* or *Role Management* open the corresponding tools directly in SAP HANA Cockpit, where you can configure the details required to enable user access, as follows:

        1.  In the SAP HANA Project Explorer, expand the *Database Connections* node to display all available connections.
        2.  Right-click the database connection for which you want to provide additional access.
        3.  Choose one of the following options:
            1.  *Manage Roles*

                Opens the *Role Management* tool in SAP HANA Cockpit.

            2.  *Manage Users*

                Opens the *User Management* tool in SAP HANA Cockpit.


        4.  Configure the user or role that requires access to the selected database connection.



**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

