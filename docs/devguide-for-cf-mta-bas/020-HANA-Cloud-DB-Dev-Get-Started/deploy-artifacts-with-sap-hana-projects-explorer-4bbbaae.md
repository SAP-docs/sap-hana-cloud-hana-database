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

    If you want to see only those database objects that are pending deployment, hover the mouse cursor over the *SAP HANA PROJECTS* explorer pane's title and choose <span class="FPA-icons"></span> \(Pending Deployment\) . The ![](images/BAS_icon_pendingDeploymentFolder_eefbce6.svg) *Pending Deployment \(\#\)* view displays a single folder that contains any database artifacts awaiting deployment, where "\#" is the number of artifacts currently in the folder.

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

4.  Display the run-time contents deployed to the HDI container that is bound to a database application.

    The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application.

    In the *SAP HANA PROJECTS* explorer, locate the application that contains the database artifacts you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    The selected HDI container is displayed in the *SAP HANA Database Explorer*, which enables you to browse through the different categories of database artifacts in the catalog, for example, *Tables*, *Views*, *Column Views*, etc.


**Related Information**  


[Bind Applications to Database Services with SAP HANA Projects Explorer](bind-applications-to-database-services-with-sap-hana-projects-explorer-a3865b1.md "Use the SAP HANA Projects explorer to bind applications to database services and manage database connections.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

