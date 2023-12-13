<!-- loio8ff23cac99754f8faaeb1d6c1f050250 -->

# Create Analytic Privileges for Your Calculation View

Use analytic privileges to restrict access to your calculation view's data.



<a name="loio8ff23cac99754f8faaeb1d6c1f050250__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*
-   The tables you created in the *db* module in the previous tutorial \(`passengers` and `flightreservation`\) are available.
-   The tables contain the data you loaded in the previous tutorial
-   The application project contains a calculation view called *FlightReservation*.



## Context

In this tutorial, you create two analytic privileges for a calculation view called *FlightReservation*. The analytic privileges are used to restrict access to the calculation view's data based on the `CARRID` attribute, which defines the identity of the airline, for example, *LH* \(Lufthansa\) or *SG* \(Singapore Airlines\).

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



## Procedure

1.  Create a new analytic privilege.

    1.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Select the file location where you want to add the new analytic privilege.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the analytic privilege.

    5.  Select the database artifact type, for example, analytic privilege.

        In the *Artifact Type* box, type `hdba`, and choose *Analytic Privilege \(hdbanalyticprivilege\)* from the list that appears.

    6.  Name the file `AP1`.

        The Wizard appends the appropriate file suffix \(`.hdbanalyticprivilege`\) to the name.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL analytic-privilege artifacts have the file extension `.hdbanalyticprivilege`, for example, `MyAnPriv.hdbanalyticprivilege`

    7.  Save the changes and create the new database analytic-privilege artifact; choose *Create*.


2.  Define the details of the analytic privilege *AP1*.

    1.  Open the new analytic privilege *AP1* for editing in the graphical *Analytic Privilege Editor*.

    2.  Check that the calculation view *FlightReservation* appears in the list of *Secured Models*. If it does not, press *\[+\]* to display the *Find Data Sources* Wizard, which you can use to locate and add the required data model.

    3.  Specify the SQL expression that defines the analytic privilege.

        Add the following SQL code to the *SQL Expression* pane.

        > ### Sample Code:  
        > ```
        > "PASSENGERID" in (select "PASSENGERID" from "PASSENGERS" where "NAME"=session_user)
        > ```


3.  Create a new analytic privilege.

    1.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Select the file location where you want to add the new analytic privilege.

        Choose *Browse for Folder*, select the project's *src* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the analytic privilege.

    5.  Select the database artifact type, for example, analytic privilege.

        In the *Artifact Type* box, type `hdba`, and choose *Analytic Privilege \(hdbanalyticprivilege\)* from the list that appears.

    6.  Name the file `APX`.

        The appropriate file suffix \(`.hdbanalyticprivilege`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL analytic-privilege artifacts have the file extension `.hdbanalyticprivilege`, for example, `MyAnPriv.hdbanalyticprivilege`

    7.  Save the changes and create the new database analytic-privilege artifact; choose *Create*.


4.  Define the details of the analytic privilege *APX*.

    1.  Open the new analytic privilege *APX* for editing in the graphical *Analytic Privilege Editor*.

    2.  Add the calculation view *FlightReservation* to the list of *Secured Models*.

        In the *Secured Models* pane, choose *\[+\]* to display the *Find Data Sources* Wizard, which you can use to search for `FlightReservation`. In the *Results* pane, check *FlightReservation* and choose *Finish* to add it to the list of secured models.

    3.  Define the privilege restrictions for the calculation view's `CARRID` attribute.

        In the *Attribute* pane, you need to add *ASSOCIATED ATTRIBUTE RESTRICTIONS* to the attribute `CARRID` for either “LH” \(Lufthansa\) or “SG” \(Singapore Airlines\), as follows:

        1.  Choose *\[+\]*, select `CARRID` from the list of attributes, and choose *OK*.

        2.  In the *Restriction Type* column, choose *\[+\] Restriction* and select either *LH* or *SG* from the list of values displayed, then choose *OK*.

    4.  Save the configuration changes.


5.  Build and deploy the new analytic privileges.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

    > ### Note:  
    > A mismatch between the installed SAP HANA version and the SAP HANA version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


**Related Information**  


[Create a Calculation View for your Application in Business Application Studio](create-a-calculation-view-for-your-application-in-business-application-studio-d74bfe7.md "Use the tools provided with Business Application Studio to create a calculation view.")

[Create a Database Role for the Analytic Privilege](create-a-database-role-for-the-analytic-privilege-e570e10.md "Create the role &quot;development_debug_role&quot; required for your analytic privileges.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

