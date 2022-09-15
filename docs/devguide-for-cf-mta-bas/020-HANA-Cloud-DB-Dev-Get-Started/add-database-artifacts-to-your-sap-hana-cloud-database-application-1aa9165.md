<!-- loio1aa916563bea48c8a880efba306fb7f9 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Add Database Artifacts to your SAP HANA Cloud Database Application

Add the underlying design-time database objects to your SAP HANA application.



<a name="loio1aa916563bea48c8a880efba306fb7f9__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged in to SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.



## Context

This tutorial shows how to use SAP Business Application Studio to add database artifacts \(for example, tables, views, etc.\) to an SAP HANA Cloud business application.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. The tool is available on SAP Business Application Studio's *Welcome* screen or in the command palette \(*View* \> *Find Command...* \> *Guided Development*\).



## Procedure

1.  Add a database table to your SAP HANA Cloud database application.

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Find Command...*

    2.  Create a new SAP HANA database artifact.

        Type ***hana*** in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new artifact.

    5.  Select the database artifact type, for example, table.

        In the *Artifact Type* box, type ***hdbt***, and choose *Table \(hdbtable\)* from the list that appears.

    6.  Name the file *PASSENGERS*.

        The appropriate file suffix \(`.hdbtable`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL table-definition artifacts have the file extension `.hdbtable`, for example, `MyTable.hdbtable`

    7.  Save the changes and create the new database artifact; choose *Create*.

        > ### Tip:  
        > When you create a database artifact, the location of the created artifact is saved as a user-specific workspace preference. The saved path is used by default the next time you create a database artifact. You can view and change the saved path or disable the setting in SAP Business Application Studio by choosing :gear:and then *Open Preferences* \> *SAP HANA Database Artifacts* \> *\[Remember\] Last Selected Target Path*.

    8.  Open the new database table artifact for editing.

        > ### Tip:  
        > SAP Business Application Studio provides a wide variety of dedicated editors that correspond to the database artifact types supported by the SAP HANA Deployment Infrastructure \(HDI\). The artifact type, for example, `hdbtable` or `hdbview`, is used by SAP Business Application Studio to determine which editor to open by default to enable editing. Some editors also provide a default template for the artifact type, which you can either adapt, delete, or replace as required.

        Add the following code to the file and save it.

        > ### Sample Code:  
        > `PASSENGERS.hdbtable`
        > 
        > ```
        > COLUMN TABLE
        >   "PASSENGERS" ( 
        >   "PASSENGERID" INTEGER, 
        >   "NAME" NVARCHAR(256), 
        >   "ACTIVE" TINYINT, 
        >   "ADDRESS" NVARCHAR(256), 
        >   "COUNTRY" NVARCHAR(256), 
        >   "PASSPORT" NVARCHAR(256), 
        >   "PASSENGERPRIORITYSTATUS" NVARCHAR(3) NOT NULL, 
        >   PRIMARY KEY ("PASSENGERID") 
        > ) 
        > WITH ASSOCIATIONS( 
        >   JOIN "FLIGHTRESERVATION" AS "FLIGHTRESERVATION" 
        > ON "PASSENGERID" = "PASSENGERID" 
        > )
        > ```


2.  Add another database table to your SAP HANA Cloud database application

    1.  Open the command palette and choose *SAP HANA: Create HANA Database Artifact*.

    2.  Select the project's *src* folder and click *Open*.

    3.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new database role.

    4.  Select the database artifact **type**. In the selection box, type ***.hdbt*** and choose *hdbtable* in the list that appears.

    5.  Name the file `FLIGHTRESERVATION`.

        > ### Tip:  
        > The appropriate file suffix \(`.hdbtable`\) is appended to the name by the Wizard.

    6.  Add the following code to the file and save it.

        > ### Sample Code:  
        >  `FLIGHTRESERVATION.hdbtable`
        > 
        > ```
        > COLUMN TABLE "FLIGHTRESERVATION" ( 
        >   "RESERVATIONID" INTEGER NOT NULL , 
        >   "PASSENGERID" INTEGER NOT NULL , 
        >   "MANDT" NVARCHAR(3) NOT NULL, 
        >   "CARRID" NVARCHAR(3) NOT NULL, 
        >   "CONNID" NVARCHAR(4) NOT NULL, 
        >   "FLDATE" NVARCHAR(8) NOT NULL, 
        >   "SEAT" INTEGER NOT NULL, 
        >   "BOOKINGTIME" NVARCHAR(8) NOT NULL, 
        >   PRIMARY KEY ("RESERVATIONID")) 
        >    WITH ASSOCIATIONS( JOIN "PASSENGERS" ON "PASSENGERS"."PASSENGERID" = "PASSENGERID") 
        >    UNLOAD PRIORITY 5 AUTO MERGE
        > ```


3.  Build and deploy the database module.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose <span class="FPA-icons"></span> \(Deploy\).

    > ### Tip:  
    > Details of each deployment operation are written to a dedicated log file. To ensure that the log file does not retain any information about previous deployments, enable the option *Clear the deployment log before starting a new deployment*, which you can find in :gear:. Choose *Open Settings* \> *SAP HANA Project Explorer* \> *Deploy: Auto clean deployment log*.

    Bear in mind that a mismatch between the installed SAP HANA version and the SAP HANA version specified at the start of the `.hdbconfig` file \(with the optional parameter `"minimum_feature_version"`\) can cause problems with the deployment operation.

    > ### Note:  
    > SAP Business Application Studio needs to connect to the SAP HANA Cloud instance where you want to deploy your application’s database artifacts. By default, SAP HANA Cloud accepts all connections from allowed IP addresses in SAP Business Technology Platform \(SAP BTP\), for example, in the same region and infrastructure where SAP HANA was provisioned.
    > 
    > If you are having problems deploying database artifacts to your SAP HANA Cloud instance, you can use SAP BTP cockpit to check the connection settings and, if necessary, configure SAP HANA Cloud to allow connections from additional IP addresses, for example, the ones hosting SAP Business Application Studio for your Cloud region and the underlying platform. For more details, see *Related Information* below.

4.  Check that the tables have been added to the database catalog.

    An HDI container is created and bound to a database application when the application's database module is built and deployed for the first time during the project-creation process.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  Expand the *FlightReservation...* node in the SAP HANA Database Explorer.

    3.  Choose *Tables*.

    4.  Check the two tables \(`PASSENGERS` and `FLIGHTRESERVATION`\) are listed in the results pane.

    5.  Select each table to display the table's contents in the details pane.



**Related Information**  


[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[SAP Business Application Studio Availability by IP Address](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/8509485251814213876223e332bfdcbb.html)

[Change Allowed Connections in SAP HANA Cloud cockpit](https://help.sap.com/viewer/db19c7071e5f4101837e23f06e576495/2020_04_QRC/en-US/770d34deb86d4eb49dc944ce9921228c.html)

