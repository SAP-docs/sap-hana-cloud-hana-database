<!-- loiod74bfe7bb92547d7861e302ee9c062b5 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Calculation View for your Application in Business Application Studio

Use the tools provided with Business Application Studio to create a calculation view.



<a name="loiod74bfe7bb92547d7861e302ee9c062b5__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*
-   The tables you created in the *db* module in the previous tutorial \(`passengers` and `flightreservation`\) are available.
-   The tables contain the data you loaded in the previous tutorial.



## Context

In this tutorial, you create a calculation view to combine information from the `PASSENGERS` and `FLIGHTRESERVATION` tables into a single view and then extend the view with a calculated column.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



## Procedure

1.  Create a folder named "`models`" under the `src/` folder.

2.  Create a new calculation view.

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...* or


    1.  Create a new SAP HANA database artifact.

        Type ***hana*** in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    2.  Select the database artifact type, for example, calculation view.

        In the *Artifact Type* box, type ***hdbca***, and choose *Calculation View \(hdbcalculationview\)* from the list that appears.

    3.  Choose the file location where you want to add the new calculation view.

        Choose *Browse for Folder*, select the project's *src/models* folder, and choose *Open*.

    4.  Choose the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new database artifact.

    5.  Name the file ***FlightReservation***.

        The appropriate file suffix \(`.hdbcalculationview`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL calculation view artifacts have the file extension `.hdbcalculationview`, for example, `MyCalcView.hdbcalculationview`

        In the selection menus, choose *DIMENSION* as the data category and *STANDARD* as the data type.

    6.  Save the changes and create the new database calculation-view artifact; choose *Create*.


3.  Open the new calculation-view artifact for editing.

    > ### Tip:  
    > SAP Business Application Studio provides a wide variety of dedicated editors that correspond to the database artifact types supported by the SAP HANA Deployment Infrastructure \(HDI\). The artifact type, for example, `hdbcalculationview`, is used by SAP Business Application Studio to determine which editor to open by default to enable editing. Some editors also provide a default template for the artifact type, which you can either adapt, delete, or replace as required.

    In the *Project Explorer*, double-click the calculation view to display it in the graphical *Calculation View Editor*. If you prefer to view and work with the artifact source code, right-click the calculation-view artifact and choose *Open with* \> *Code Editor*.

    1.  Create a new join node for the calculation view.

        In the tools palette, choose *Join*.

    2.  Name the join node.

        Right-click the join node, choose *Rename*, and type the name ***Reservations***.

    3.  Add a data source for the join node.

        Click *\[+\]*, search for the *PASSENGERS* table in the add data source window, select the table, and click *Finish*.

    4.  Add another data source for the join node.

        Click *\[+\]*, search for the *FLIGHTRESERVATION* table in the add data source window, select the table, and click *Finish*.

    5.  Configure the join node.

        To create a join between the two tables *PASSENGERS* and *FLIGHTRESERVATION*, in the *Join Definition* tab select the *PASSENGERID* column in the *PASSENGERS* table and drag it over and drop it onto the *PASSENGERID* column in the *FLIGHTRESERVATION* table.

    6.  Select and map the output columns.

        Switch to the *Mapping* tab and select the columns to map. Select the *CARRID* \(Carrier ID: it will be used later in the calculated columns\) and then choose *Add To Output*.

    7.  Switch to the *Calculated Columns* tab and click the *Add* button.

    8.  Select the calculated column *CC\_1* and configure it as follows:

        -   Rename it to ***Airline*** 
        -   Change the column length to ***20***
        -   Add the following SQL expression:

            `CASE "CARRID" WHEN 'LH' THEN 'Lufthansa' WHEN 'SQ' THEN 'Singapore Airlines' END`


    9.  In the calculation view editor, connect the *Reservations* node to the *Projection* node.

    10. In the *Projection* node’s details panel, in the *Mapping* tab, choose *Auto Map by Name*.

        > ### Tip:  
        > If the *Auto Map by Name* is hidden, scroll right to display it.

    11. Save your changes.


4.  Deploy the calculation view.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose <span class="FPA-icons"></span> \(Deploy\).

    > ### Note:  
    > A mismatch between the installed SAP HANA version and the SAP HANA version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.

5.  Check that the calculation view now contains your configuration.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  Expand the *FlightReservation...* node in the SAP HANA Database Explorer.

    3.  Choose *Column Views* in the list of object types.

    4.  Check the new calculation view is listed in the results pane.

    5.  Select the calculation view `FlightReservation` to display the contents in the details pane.



**Related Information**  


[Load Data into your SAP HANA Cloud Application's Database Tables](load-data-into-your-sap-hana-cloud-application-s-database-tables-75679ce.md "Use the tools provided with SAP Business Application Studio to populate the new database tables with data stored in CSV (comma separated values) files.")

[Create a Database Procedure for your Application in SAP Business Application Studio](create-a-database-procedure-for-your-application-in-sap-business-application-st-d13c960.md "Use the tools provided with SAP Business Application Studio to create a database procedure.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[Create Analytic Privileges for Your Calculation View](create-analytic-privileges-for-your-calculation-view-8ff23ca.md "Use analytic privileges to restrict access to your calculation view's data.")

