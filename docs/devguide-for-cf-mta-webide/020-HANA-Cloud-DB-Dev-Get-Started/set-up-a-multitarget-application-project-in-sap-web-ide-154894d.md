<!-- loio154894de6bac4e94845ef9f7879852ca -->

# Set up a Multitarget Application Project in SAP Web IDE

Use templates to start an application-development project in SAP Web IDE Full-Stack.



<a name="loio154894de6bac4e94845ef9f7879852ca__prereq_mvv_cp1_vlb"/>

## Prerequisites

Before using SAP Web IDE Full-Stack, bear in mind the following prerequisites:

-   You must have a valid global account.

    A global account in SAP Business Technology Platform is required to enable the SAP Web IDE Full-Stack.

    > ### Tip:  
    > To perform the steps described in this tutorial, you need two subaccounts: a Neo subaccount to enable the SAP Web IDE Full-Stack, and a Cloud Foundry subaccount to maintain your application artifacts. For more information, see *Setup and Prerequisites for SAP Web IDE Full-Stack* in *Related Information*.

-   Set up the SAP Web IDE Full-Stack
    -   The subaccount hosting the SAP Web IDE Full-Stack service must have the trust configuration of the *Local Service Provider* set to *Principal Propagation: enabled*.

    -   You must enable the SAP Web IDE Full-Stack.

        > ### Tip:  
        > SAP Web IDE is a service running in the Neo environment. To enable and configure the SAP Web IDE service, open the cockpit, navigate to the corresponding \(Neo\) subaccount and choose *Neo Environment* \> *Services* \> *SAP Web IDE Full-Stack* to enable the service.

    -   You must grant access to the SAP Web IDE Full-Stack

        Access to the SAP Web IDE Full-Stack is possible only for users who have been assigned the “`DiDeveloper`” role. For more information, see *Setup and Prerequisites for SAP Web IDE Full-Stack* in *Related Information*.

    -   Set up the Cloud Foundry preferences in SAP Web IDE Full-Stack

        -   API Endpoint \(displayed in the Cloud Foundry subaccount overview\)
        -   Organization \(displayed in the drop-down list after you log in\)
        -   Space \(displayed in the drop-down list after you log in\)


-   Enable the *SAP HANA Database Development Tools* extension in SAP Web IDE Full-Stack \(in *Global Preferences*\)
-   You must set up your developer environment in Cloud Foundry:
    -   Enable the *SAP HANA Database Development Tools service*
    -   Create a development space in the Cloud Foundry subaccount organization; the space is used to maintain your application design-time artifacts
    -   Assign members to your Cloud Foundry organizations and spaces

        To use the Cloud Foundry space linked to your SAP Web IDE application project, developers working with the Cloud Foundry environment must be assigned the “space developer” role. For more information, see *Setup and Prerequisites for SAP Web IDE Full-Stack* in *Related Information*.





## Context



## Procedure

1.  Create a new multitarget application project.

    1.  Create a project.

        In the Home \(*Welcome*\) page, choose *New Project from Template*.

    2.  In the *Template Selection* window, choose *Environment* \> *Cloud Foundry*.

    3.  In the list of templates displayed, choose *SAP HANA Database Application*.

        Define mandatory \(\*\) details of the new project according to the requirements of the setup Wizard, for example:

        -   *Basic Information* \> *Project Name\**: `travel`
        -   *Template Customization* \> *Database Details\** \> *HANA Cloud*

    4.  Save the configuration; choose *Finish*.

        The setup Wizard creates a project with the default configuration, files \(`package.json` and `mta.yaml)`, and directories \(`travel/db/src`\).


2.  Create a simple database table.

    1.  Create a new database artifact \(hdbtable\) called `room.hdbtable`.

        Right-click the folder `travel/db/src`, choose *New* \> *Database Artifact* in the context menu, and in the *New Database Artifact* window, enter the following values:

        -   *File Name*: `room`
        -   *File Type*: *hdbtable*

        The new file is displayed in a new tab in the SAP Web IDE code editor.

    2.  Copy the following SAP HANA DDL code into the new `hdbtable` file and save the changes.

        > ### Sample Code:  
        > ```
        > COLUMN TABLE "travel.db::room" ( 
        > 	"hno" INTEGER, 
        > 	"type" VARCHAR(10), 
        > 	"free" INTEGER, 
        > 	"price" DOUBLE, 
        > 	PRIMARY KEY ("hno", "type") 
        > )
        > ```


3.  Build the database module of your multitarget application.

    1.  In the project structure, right-click the *db* module and choose *Build* \> *Build* in the context menu.

        A successful build creates an HDI container and deploys the run-time version of the defined table to this container.

        > ### Tip:  
        > To watch the build progress, display the *Console* pane by clicking the console icon **\[\>\]** in the bottom right-hand corner of the SAP Web IDE window.

    2.  Check the database table has been deployed and activated in the run-time catalog.

        You can display the contents of HDI container to which the database table is deployed by right-clicking the *db* module in the *travel* project and choosing *Open HDI Container* in the context menu. In the Database Explorer choose *Tables* to list the tables available, which at this point includes only one called *room*.


4.  Load some data into your new database table.

    1.  In the Database Explorer, open an SQL Console.

    2.  Copy the following SQL commands into the SQL Console and choose *Run* **\[\>\]**.

        > ### Sample Code:  
        > ```
        > INSERT INTO "travel.db::room" VALUES (10, 'single', 20, 135.00);
        > INSERT INTO "travel.db::room" VALUES (10, 'double', 45, 200.00);
        > INSERT INTO "travel.db::room" VALUES (30, 'single', 12, 45.00);
        > INSERT INTO "travel.db::room" VALUES (30, 'double', 15, 80.00);
        > INSERT INTO "travel.db::room" VALUES (100, 'single', 11, 60.00);
        > INSERT INTO "travel.db::room" VALUES (100, 'double', 24, 100.00);
        > INSERT INTO "travel.db::room" VALUES (110, 'single', 2, 70.00);
        > INSERT INTO "travel.db::room" VALUES (110, 'double', 10, 130.00);
        > INSERT INTO "travel.db::room" VALUES (120, 'single', 34, 80.00);
        > INSERT INTO "travel.db::room" VALUES (120, 'double', 78, 140.00);
        > INSERT INTO "travel.db::room" VALUES (120, 'suite', 55, 350.00);
        > INSERT INTO "travel.db::room" VALUES (130, 'single', 89, 100.00);
        > INSERT INTO "travel.db::room" VALUES (130, 'double', 300, 270.00);
        > INSERT INTO "travel.db::room" VALUES (130, 'suite', 100, 700.00);
        > INSERT INTO "travel.db::room" VALUES (140, 'single', 10, 99.00);
        > INSERT INTO "travel.db::room" VALUES (140, 'double', 9, 149.00);
        > INSERT INTO "travel.db::room" VALUES (140, 'suite', 78, 499.00);
        > ```

    3.  Check the database table has been deployed and activated in the run-time catalog.

        You can display the contents of HDI container to which the database table is deployed by right-clicking the *db* module in the *travel* project and choosing *Open HDI Container* in the context menu. In the Database Explorer choose *Tables* to list the tables available, which at this point includes only one called *room*.

    4.  Check the database table *room* now contains the data you loaded.

        In the Database Explorer right-click *room* and choose *Open data* to display the table with raw data in the details pane.


5.  Create a simple calculation view based on your database table.

    1.  Create a new calculation view called `cv_room.hdbcalculationview`.

        Right-click the folder `travel/db/src`, choose *New* \> *Calculation View* in the context menu, and in the *New Calculation View* window, enter the following values:

        -   *Name*: `cv_room`
        -   *Namespace*: travel.db
        -   *Label*: An optional short description of the view
        -   *Data Category*: `CUBE`

        The new calculation view is displayed in the graphical modeling editor.

    2.  Select a data source for the calculation view.

        Click the *Aggregation* node and the \[+\] icon and in the *Find Data Sources* window, type `room` in the *All Types Selected* search box, and in the *Results* pane, choose *travel.db::room* and choose *Finish*.

    3.  Display details of the calculation view's *Aggregation* node.

        Double-click the *Aggregation* node *travel.db::room* and choose the *Mapping* column in the *Aggregation* details window.

    4.  Define the output columns you want to display in your calculation view.

        In the *Data Sources* pane, select the table columns *type*, *free*, and *price*, drag them over and drop them onto the *Output Columns* pane.

    5.  Check the semantics for the columns displayed in your calculation view.

        Click the *Semantics* node in the calculation view editor and, in the *Semantics* details pane, check that the option *SUM* is displayed in the *Aggregation* column for both the *free* and *price* columns.

    6.  Save the changes.


6.  Build the calculation view.

    1.  In the project structure, right-click the calculation view *cv\_room* and choose *Build* \> *Build selected files* in the context menu.

        A successful incremental build deploys the run-time version of the calculation view *cv\_room* to the HDI container created in the previous database build operation.

    2.  Check the calculation view has been deployed and activated in the run-time catalog.

        In the Database Explorer choose *Column Views* to list the calculation views available, which at this point includes only one called *cv\_room*.

    3.  Display the calculation view's data.

        In the Database Explorer right-click *cv\_room* and choose *Open Data* in the context menu.

    4.  Create a chart using the calculation view's columns and data.

        In the *Analysis* tab of the calculation view's details pane, drag *type* from the list of column *Attributes* and drop it into the *Label Axis\(1\)* pane. Then drag *free* from the list of column *Measures* and drop it into the *Value Axis\(1\)* pane.

        The details pane displays a chart showing the number of rooms available for the different room types: "single", "double", and "suite".

        > ### Tip:  
        > You can chart-type bar at the top of the display pane to change the chart type, for example, from the default "*Vertical Bar*" to "*Horizontal Stacked Bar*" or "*Pie*" chart.



**Related Information**  


[Setup and Prerequisites for SAP Web IDE Full-Stack](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/102a024b1e344c54a0df7d835163b039.html)

[SAP HANA Academy: SAP HANA Cloud](https://www.youtube.com/watch?v=e2Kt2uKnTyM&feature=youtu.be)

