<!-- loio81e83fbc9b2c42ff8dc69cff2f43bc9f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Procedure in SAP HANA Cloud

Create, edit, and deploy procedures.



## Prerequisites

-   You have access to a running SAP HANA Cloud system where the Cloud Foundry run time is installed and configured

-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development space and a multitarget application \(MTA\) project.
-   You have created the database tables `Header` and `Item` described in *Create the Underlying Data Artifacts for a Procedure*. For more information, see *Related Information* below.


> ### Caution:  
> The code examples included in this document are sometimes syntactically incomplete; as a general rule, code examples are intended for illustration purposes only.



## Context

In SAP HANA Cloud a database procedure has the file extension `.hdbprocedure`, for example, `myProcedure.hdbprocedure`. To create and deploy a procedure using the SAP Business Application Studiok, perform the following steps:



## Procedure

1.  Start SAP Business Application Studio.

2.  Display the application project to which you want to add a database procedure.

    An application is created within a context of a project. If you do not already have a project, there are a number of ways to create one, for example: by importing it, cloning it, or creating a new one from scratch.

    1.  Start the *Create Project from Template* Wizard.

        -   Open the command palette:

            Either press  [Crtl\] + [Shift\] + [P\]  

            Or choose *View* \> *Command Palette...*

            Or just press [F1\]

        -   In the command palette, type ***Project*** and choose *Create Project from Template*.

        > ### Tip:  
        > Alternatively, in the *Welcome* tab, choose *Start from Template* \> *Create a new project*.

    2.  In the *New Project from Template* Wizard, choose *SAP HANA Database Project* and then choose *Start*.

    3.  In the *Add Basic Information* pane, type the name of the new project \(***MyApp*** \) and choose *Next*.

    4.  In the *Set Basic Properties* pane, accept the default settings and choose *Next*.

    5.  In the *Set Database Information* pane, use the default settings and choose *Next*.

        You can use the following default settings:

        -   *Namespace* \(empty\)

        -   *Schema Name* \(empty\)

        -   *SAP HANA Database Version \** \(HANA Cloud\)

        -   *Bind the database module to a Cloud Foundry service instance?* \(Yes\)


    6.  In the *Bind to HDI Container Service* pane, provide the requested information.

        It is necessary to provide the credentials required to log on to the Cloud Foundry end point that provides the service instance to which you want to bind the database module of your new application project. After you log on to Cloud Foundry, you can choose the target organization, space, and service instance.

        -   *Enter e-mail address* \(Type the e-mail address of a registered Cloud Foundry user\)
        -   *Enter Password* \(Type the Cloud Foundry user's password\)

            Press [Enter\] or click *Login -\>* to connect to Cloud Foundry.

            > ### Note:  
            > If two-factor authentication \(2FA\) is configured in your landscape, you might need to provide an additional single-use token.


        After you log in to Cloud Foundry, use the following options to specify the target Cloud Foundry space where the service instance is running:

        -   *Choose Cloud Foundry Org \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Space \** \(Select from the drop-down list\)
        -   *Choose Cloud Foundry Service \** \(Create a new service instance\)
        -   *Please enter a unique and non-existing service-instance name\** \(default is "*<ProjectName\>*-hdidb-ws-*<WorkspaceName\>*"\)

            > ### Note:  
            > It is recommended to accept the default service-instance name displayed, but you can also choose an existing service instance from the drop-down list provided. However, binding to an existing service can lead to problems caused by the undeployment \(removal\) of existing files from a previous deployment.


        Choose *Finish* to generate the new project called *FlightReservation* in the chosen Cloud Foundry organization and space.


3.  Create a stored procedure that enables you to extract content from a database table .

    This tutorial shows you how to create a procedure that you can use to display the purchases made by a customer, based on the customer's ID, for example: ID = 1.

    1.  Create a new folder for your stored procedures.

        In the `db/` module create a folder named `procedures` in the `src/` folder, for example, `MyApp/db/src/procedures`.

    2.  Create a new `.hdbprocedure` file for your stored procedure.

        Right-click the database-module folder `db/src/procedures`, choose *New* \> *File* from the context menu, and name the new stored procedure ***OrderCount.hdbprocedure***.

        > ### Note:  
        > To use the *Create SAP HANA Database Artifact* Wizard to guide you through the artifact-creation process, choose *View* \> *Command Palette*, type ***create***, and choose *SAP HANA: Create SAP HANA Database Artifact*. Choose *Procedure \(hdbprocedure\)* as the artifact type, provide a name for the new procedure and save it in the folder `db/src/procedures`.

        The new stored procedure opens in SAP Business Application Studio.

    3.  Add the following SQLScript code to the procedure file `OrderCount.hdbprocedure` and save the file.

        > ### Sample Code:  
        > `MyApp/db/src/procedures/OrderCount.hdbprocedure`
        > 
        > ```sql
        > PROCEDURE "OrderCount"( 
        >  OUT ORDER_COUNT INTEGER, 
        >  IN PURCHASEORDERITEM_ID INTEGER 
        > ) 
        > LANGUAGE SQLSCRIPT 
        > SQL SECURITY INVOKER 
        > --DEFAULT SCHEMA <default_schema_name> 
        > READS SQL DATA AS 
        > BEGIN 
        >   /************************************* 
        >    Write your procedure logic 
        >   *************************************/ 
        >   SELECT 
        >     COUNT(*) INTO ORDER_COUNT 
        >   FROM 
        >     "PurchaseOrderItem" 
        >   WHERE 
        >     "PURCHASEORDERITEM" = PURCHASEORDERITEM_ID; 
        > END 
        > ```

    4.  Build the multitarget application database module `db/`.

        In SAP Business Application Studio, right-click the application module *MyApp/db*, select the *db/* folder, choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\), and follow the deployment progress in the output displayed in the console pane.

        ***Deployment to container A7976B2D158949D193DB4843390C4BE5 done \[Deployment ID: none\].******Deployment ended at 2023-05-24 13:02:13***


4.  Check that the required plug-in is available to build and deploy the stored procedure.

    In SAP HANA Cloud, a file suffix \(for example, `.hdbprocedure`\) is linked to a specific plug-in, which is used to generate the corresponding catalog object from a design-time artifact.

    The container-configuration file `.hdiconfig` must contain the following entry \(version numbers can differ\):

    > ### Sample Code:  
    > ```json
    > "hdbprocedure": {
    >             "plugin_name": "com.sap.hana.di.procedure",
    >             "plugin_version": "40.0.0"                 //optional
    >         },
    > ```

    > ### Tip:  
    > By default, the `.hdiconfig` file is hidden. To display it, choose *View* \> *Show Hidden Files*in the menu bar.

5.  Check that the procedure has been deployed.

    1.  Open the SAP HANA Database Explorer.

        In the views pane on the left-hand side of SAP Business Application Studio, choose <span class="FPA-icons"></span> \(SAP HANA Database Explorer\) to display a list of connections to SAP HANA databases and a corresponding catalog browser.

        > ### Note:  
        > To use the standalone Database Explorer, open the *SAP HANA PROJECTS* explorer, locate the application project containing the database artifacts that you want to explore, for example, *MyApp/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    2.  Select and expand the database service instance assigned to your application.

        The HDI container assigned to your database application is named **<AppName\>*-hdbdb-ws-*<ID\>** 

        > ### Tip:  
        > If your HDI container is not listed in the SAP HANA Database Explorer, choose <span class="SAP-icons"></span> \(Refresh Explorer\)to refresh the list.

    3.  Select the *Procedures* node.

    4.  Confirm that the *CATALOG* pane displays an entry named *OrderCount*.


6.  Test the stored procedure `OrderCount.hdbprocedure`.

    Use the database explorer to test the stored procedure and view some content from your database tables.

    1.  Display the details of the procedure *OrderCount*.

        In the SAP HANA Database Explorer's *CATALOG* pane, select the procedure *OrderCount* to display its definition in the details pane.

    2.  Choose a test option.

        You can run one of the following options:

        -   *Generate CALL Statement*

            Displays the corresponding SQL `CALL` statement for the database procedure.

            > ### Tip:  
            > The *CREATE Statement* tab displays the SQL code used to create the selected procedure.

        -   *Generate CALL Statement with UI*

            Displays the corresponding SQL `CALL` statement for the database procedure in the graphical user interface \(GUI\) so that you can run the procedure with parameters that you provide interactively.

            > ### Note:  
            > Some types of procedure cannot be called with the GUI, for example, procedures with parameters that reference user-defined types \(`TABLE_TYPE`\). You must run the procedure without the GUI.

        -   *Analyze SQLScript Code*

            Runs an analysis of the SQLScript used in the selected database function. The report generated by the code analysis includes the name of the object that is causing problems and name of the schema where the object is located, the rule that tiggered the report, a short description of the problem, and the corresponding code snippet where the problem was found.

            > ### Tip:  
            > Choose <span class="SAP-icons"></span> \(Download\) to save the findings of the SQLScript analysis to a comma-separated-values \(CSV\) file, for example, `SQLScript_Code_Analysis_Results.csv`, in your local file system.


    3.  Generate a `CALL` statement for the SQL procedure and display it in the UI so that you can run it with parameters.

        Right-click the procedure and choose *Generated CALL Statement with UI* from the context menu.

    4.  Enter a value in the *PURCHASEORDER\_ID* box.

        > ### Tip:  
        > Since the `PURCHASEORDERID` is defined in the first column of the table `PurchaseOrderItem`, you can use the first values in each row of the file `item.csv` to run the tests, for example, ***0500000000*** or ***0500000001***.

    5.  Run the procedure.

        Choose ![](images/BAS_Icon_SQL_RUN_6d5a0d0.png) \(*Run SQL with parameter values from this tab*\).



**Related Information**  


[Create a Database Function in SAP HANA Cloud](create-a-database-function-in-sap-hana-cloud-e3093ea.md "Add a database function to your data model.")

