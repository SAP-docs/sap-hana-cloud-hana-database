<!-- loiod13c960b96ed47439cdc4c4812593ad8 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Create a Database Procedure for your Application in SAP Business Application Studio

Use the tools provided with SAP Business Application Studio to create a database procedure.



<a name="loiod13c960b96ed47439cdc4c4812593ad8__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*
-   The tables you created in the *db* module in the previous tutorial \(`passengers` and `flightreservation`\) are available and contain data.
-   The calculation view created in a previous step is available.



## Context

This tutorial shows you how to create a procedure that you can use to display the bookings made by a passenger, based on the passenger's ID, for example: ID = 1.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



## Procedure

1.  Create a new database procedure.

    1.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type ***hana****SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Select the file location where you want to add the new database procedure.

        Choose *Browse for Folder*, select *db/src/*, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new database procedure.

    5.  Select the database artifact type, for example, procedure.

        In the *Artifact Type* box, type ***hdbp***, and choose *Procedure \(hdbprocedure\)* from the list that appears.

    6.  Name the file ***BookingCount***.

        The appropriate file suffix \(`.hdbprocedure`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL procedure-definition artifacts have the file extension `.hdbprocedure`, for example, `MyProcedure.hdbprocedure`

    7.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    8.  Save the changes and create the new database procedure artifact; choose *Create*.


2.  Edit the new database procedure.

    > ### Tip:  
    > SAP Business Application Studio provides a wide variety of dedicated editors that correspond to the database artifact types supported by the SAP HANA Deployment Infrastructure \(HDI\). The artifact type, for example, `hdbprocedure`, is used by SAP Business Application Studio to determine which editor to open by default to enable editing. Some editors also provide a default template for the artifact type, which you can either adapt, delete, or replace as required.

    Add the following code to the new database procedure file:

    > ### Sample Code:  
    > `BookingCount.hdbprocedure` 
    > 
    > ```
    > PROCEDURE "BookingCount"( 
    >  OUT BOOKING_COUNT INTEGER, 
    >  IN PASSENGER_ID INTEGER 
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
    >     COUNT(*) INTO BOOKING_COUNT 
    >   FROM 
    >     "FLIGHTRESERVATION" 
    >   WHERE 
    >     "PASSENGERID" = PASSENGER_ID; 
    > END 
    > ```

3.  Save your changes.

4.  Deploy the new procedure.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose <span class="FPA-icons"></span> \(Deploy\) \(*Deploy*\).

    > ### Note:  
    > A mismatch between the installed SAP HANA version and the SAP HANA version specified in the in the command palette and choose `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.

5.  Check that the procedure has been deployed.

    1.  in the command palette and chooseDisplay the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  Expand the *FlightReservation...* node in the SAP HANA Database Explorer.

    3.  Choose *Procedures* in the list of object types.

    4.  Check the new procedure is listed in the results pane.

    5.  Select the procedure `BookingCount` to display the contents in the details pane.



**Related Information**  


[Create a Calculation View for your Application in Business Application Studio](create-a-calculation-view-for-your-application-in-business-application-studio-d74bfe7.md "Use the tools provided with Business Application Studio to create a calculation view.")

[View Database Objects with the Database Explorer](view-database-objects-with-the-database-explorer-0e5ac0b.md "Check the contents of your database with SAP HANA Database Explorer.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

