<!-- loioe3093ea4fd394be288d97090f193fa89 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Function in SAP HANA Cloud

Add a database function to your data model.



## Prerequisites

-   You have access to a running SAP HANA Cloud system where the Cloud Foundry \(CF\) run-time environment is installed and configured.

-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development space and a multitarget application \(MTA\) project.

> ### Caution:  
> The code examples included in this document are sometimes syntactically incomplete; as a general rule, code examples are intended for illustration purposes only.



## Context

In SQL, a user-defined function \(UDF\) enables you to build complex logic into a single database object. A scalar UDF is a custom function that can be called in the `SELECT` and `WHERE` clauses of an SQL statement. In SAP HANA Cloud, a database function \(scalar or table\) has the file extension `.hdbfunction`, for example, `myScalarFunction.hdbfunction`.

To create and deploy a procedure using the SAP Business Application Studio, perform the following steps:



<a name="loioe3093ea4fd394be288d97090f193fa89__steps_ag1_ccc_3v"/>

## Procedure

1.  Start SAP Business Application Studio.

2.  Display the application project to which you want to add a database function.

    An application is created within a context of a project. If you do not already have a project, there are a number of ways to create one, for example: by importing it, cloning it, or creating a new one from scratch.

    1.  In SAP Business Application Studio, start the *Create Project from Template* Wizard.

        -   Open the command palette:

            Choose *View* \> *Command Palette...*

        -   In the command palette, type `Project` and choose *Create Project from Template*.

        > ### Tip:  
        > Alternatively, in the *Welcome* tab, choose *Start from Template* \> *Create a new project*.

    2.  In the *New Project from Template* Wizard, choose *SAP HANA Database Project* and then choose *Start*.

    3.  In the *Add Basic Information* pane, type the name of the new project \(`MyApp` \) and choose *Next*.

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


3.  Create a database function.

    Database functions must be created in the application project's database module, for example, `db/src`. A scalar user-defined function \(UDF\) has a list of input parameters and returns the scalar values specified in the <code>RETURNS <i class="varname">&lt;return parameter list&gt;</i></code> option defined in the SQL function, for example, `decimal(15,2)`. The scalar UDF named “`apply_discount`” that you create in this tutorial performs the following actions:

    -   Applies a discount to the stored product price

    -   Calculates the sale price of a product including the suggested discount


    1.  Create a new folder for your functions.

        If it does not already exist, create a folder named `functions` in the `src/` folder of your application project's `db/` module, for example, `myapp/db/src/functions`.

    2.  Create a new `.hdbfunction` file for your scalar user-defined function.

        Right-click the application's database-module folder `db/src/functions`, choose *New* \> *File* from the context menu, and name the new stored scalar function `apply_discount.hdbfunction`.

        > ### Note:  
        > To use the *Create SAP HANA Database Artifact* Wizard to guide you through the artifact-creation process, choose *View* \> *Command Palette*, type `create`, and choose *SAP HANA: Create SAP HANA Database Artifact*. Choose *Function \(hdbfunction\)* as the artifact type, provide a name for the new function and save it in the folder `db/src/functions`.

        The new scalar function opens in SAP Business Application Studio.

    3.  Add the following SQLScript code to the function-definition file `apply_discount.hdbfunction`

        > ### Sample Code:  
        > `db/src/functions/apply_discount.hdbfunction`
        > 
        > ```sql
        > FUNCTION "apply_discount" (im_price decimal(15,2), im_discount decimal(15,2) )
        > 	RETURNS result decimal(15,2) 
        > 	LANGUAGE SQLSCRIPT 
        > 	SQL SECURITY INVOKER AS 
        > BEGIN 
        > 
        > result := :im_price - ( :im_price * :im_discount );
        > END;
        > ```

    4.  Build the application database module `db`.

        In SAP Business Application Studio, right-click the application module *MyApp/db*, select the *db/* folder, choose ![](../020-HANA-Cloud-DB-Dev-Get-Started/images/BAS_icon_deploy_4423157.svg) \(*Deploy*\), and follow the deployment progress in the output displayed in the console pane.

        ***Deployment to container A7976B2D158949D193DB4843390C4BE5 done \[Deployment ID: none\].******Deployment ended at 2023-05-24 13:02:13***


4.  Check that the required plug-in is available deploy the function.

    In SAP HANA Cloud, a file suffix \(for example, `.hdbfunction`\) is linked to a specific HDI plug-in, which is used to generate the corresponding catalog object from a design-time artifact.

    The container-configuration file `.hdiconfig` must contain the following entry:

    > ### Sample Code:  
    > ```json
    > "hdbfunction": {
    >             "plugin_name": "com.sap.hana.di.function"
    >         },
    > ```

    > ### Tip:  
    > By default, the `.hdiconfig` configuration file is hidden. To display it, choose *View* \> *Show Hidden Files*in the menu bar.

5.  Check that the new database function has been deployed.

    1.  Open the SAP HANA Database Explorer.

        In the views pane on the left-hand side of SAP Business Application Studio, choose <span class="FPA-icons"></span> \(SAP HANA Database Explorer\) to display a list of connections to SAP HANA databases and a corresponding catalog browser.

        > ### Note:  
        > To use the standalone Database Explorer, open the *SAP HANA PROJECTS* explorer, locate the application project containing the database artifacts that you want to explore, for example, *MyApp/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    2.  Select and expand the database service instance assigned to your application.

        The HDI container assigned to your database application is named **<AppName\>*-hdbdb-ws-*<ID\>** 

        > ### Tip:  
        > If your HDI container is not listed in the SAP HANA Database Explorer, choose <span class="SAP-icons"></span> \(Refresh Explorer\)to refresh the list.

    3.  Select the *Functions* node.

    4.  Confirm that the *CATALOG* pane displays the function named *apply\_discount*.


6.  Test the new scalar function `apply_discount.hdbfunction`.

    Use the SAP HANA Database Explorer to test the `apply_discount.hdbfunction` function.

    1.  In the SAP HANA Database Explorer, select and expand the database assigned to your application.

        In the list of database object types displayed, select *Functions*, and in the *CATALOG BROWSER*, choose the function `apply_discount.hdbfunction` to display the configuration in the details tab.

    2.  Choose a test option.

        You can run one of the following options:

        -   *Generate SELECT Statement*

            Displays the corresponding SQL `SELECT` statement for the database function.

            > ### Tip:  
            > The *CREATE Statement* tab displays the SQL code used to create the selected function.

        -   *Analyze SQLScript Code*

            Runs an analysis of the SQLScript used in the selected database function. The report generated by the code analysis includes the name of the object that is causing problems and name of the schema where the object is located, the rule that tiggered the report, a short description of the problem, and the corresponding code snippet where the problem was found.

            > ### Tip:  
            > Choose <span class="SAP-icons"></span> \(Download\) to save the findings of the SQLScript analysis to a comma-separated-values \(CSV\) file, for example, `SQLScript_Code_Analysis_Results.csv`, in your local file system.




**Related Information**  


[Create a Database Procedure in SAP HANA Cloud](create-a-database-procedure-in-sap-hana-cloud-81e83fb.md "Create, edit, and deploy procedures.")

[Creating Procedures and Functions in SAP HANA Cloud](creating-procedures-and-functions-in-sap-hana-cloud-1e5e2c6.md "Database procedures and functions can be used to help manage the underlying data model.")

