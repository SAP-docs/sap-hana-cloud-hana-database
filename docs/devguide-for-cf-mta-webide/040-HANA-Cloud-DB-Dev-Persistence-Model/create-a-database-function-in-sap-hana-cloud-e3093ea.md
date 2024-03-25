<!-- loioe3093ea4fd394be288d97090f193fa89 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Function in SAP HANA Cloud

Add a database function to your data model.



## Prerequisites

-   You have access to a running SAP HANA Cloud system where the Cloud Foundry \(CF\) run-time environment is installed and configured.

-   For the purposes of this tutorial, you must have access to SAP Web IDE Full-Stack. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development workspace and a multitarget application \(MTA\) project.

> ### Caution:  
> The code examples included in this document are sometimes syntactically incomplete; as a general rule, code examples are intended for illustration purposes only.



## Context

In SQL, a user-defined function \(UDF\) enables you to build complex logic into a single database object. A scalar UDF is a custom function that can be called in the `SELECT` and `WHERE` clauses of an SQL statement. In SAP HANA Cloud, a database function \(scalar or table\) has the file extension `.hdbfunction`, for example, `myScalarFunction.hdbfunction`.

To create and deploy a procedure using the SAP Web IDE Full-Stack, perform the following steps:



<a name="loioe3093ea4fd394be288d97090f193fa89__steps_ag1_ccc_3v"/>

## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Display the application project to which you want to add a database function.

    An application is created within a context of a project. If you do not already have a project, there are a number of ways to create one, for example: by importing it, cloning it, or creating a new one from scratch.

    1.  In SAP Web IDE, choose *File* \> *New* \> *Project from Template*.

    2.  Choose the project template type.

        Currently, there is only one type of project template available, namely: *Multi-Target Application Project*. Select *Multi-Target Application Project* and choose *Next*.

    3.  Type the name `MyApp` for the new MTA project and choose *Next* to confirm.

    4.  Specify details of the new MTA project and choose *Next* to confirm.

    5.  Create the new MTA project; choose *Finish*.


3.  Create a database function.

    Database functions must be created in the application project's database module, for example, `db/src`. A scalar user-defined function \(UDF\) has a list of input parameters and returns the scalar values specified in the <code>RETURNS <i class="varname">&lt;return parameter list&gt;</i></code> option defined in the SQL function, for example, `decimal(15,2)`. The scalar UDF named “`apply_discount`” that you create in this tutorial performs the following actions:

    -   Applies a discount to the stored product price

    -   Calculates the sale price of a product including the suggested discount


    1.  Create a new folder for your functions.

        If it does not already exist, create a folder named `functions` in the `src/` folder of your application project's `db/` module, for example, `myapp/db/src/functions`.

    2.  Create a new `.hdbfunction` file for your scalar user-defined function.

        Right-click the application's database-module folder `db/src/functions`, choose *New* \> *Function* from the context menu, and name the new stored scalar function `apply_discount`.

        The new scalar function opens in SAP Web IDE Full-Stack.

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

        In SAP Web IDE Full-Stack, right-click the application module *MyApp/db*, choose *Build* \> *Build* in the context menu, and follow the build progress in the output displayed in the console pane.


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

        Choose *Tools* \> *Database Explorer*

    2.  Select and expand the database service instance assigned to your application.

        The HDI container assigned to your database application is named **<UserName\>*-*<ID\>*-MyApp-hdi-container* 

        > ### Note:  
        > In SAP Web IDE Full-Stack, you can add a database to the list of databases displayed by choosing *Add Database to Database Explorer* in the SAP HANA Database Explorer toolbar.

        > ### Tip:  
        > If your HDI container is not listed in the SAP HANA Database Explorer, choose <span class="SAP-icons-V5"></span> \(Refresh Explorer\)to refresh the list.

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
            > Choose <span class="SAP-icons-V5"></span> \(Download\) to save the findings of the SQLScript analysis to a comma-separated-values \(CSV\) file, for example, `SQLScript_Code_Analysis_Results.csv`, in your local file system.




**Related Information**  


[Create a Database Procedure in SAP HANA Cloud](create-a-database-procedure-in-sap-hana-cloud-81e83fb.md "Create, edit, and deploy procedures.")

[Creating Procedures and Functions in SAP HANA Cloud](creating-procedures-and-functions-in-sap-hana-cloud-1e5e2c6.md "Database procedures and functions can be used to help manage the underlying data model.")

