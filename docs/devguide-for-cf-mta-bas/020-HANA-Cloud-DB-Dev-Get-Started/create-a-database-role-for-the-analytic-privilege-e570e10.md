<!-- loioe570e10dc5d64a6dbfe5da1153a6cb44 -->

# Create a Database Role for the Analytic Privilege

Create the role "development\_debug\_role" required for your analytic privileges.



<a name="loioe570e10dc5d64a6dbfe5da1153a6cb44__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*
-   The tables you created in the *db* module in the previous tutorial \(`passengers` and `flightreservation`\) are available.
-   The tables contain the data you loaded in the previous tutorial
-   The application project contains a calculation view called *FlightReservation*.
-   The application project contains analytic privileges view called *API* and *APX*.



## Context

In this tutorial, you define the `development_debug_role` role required by the two analytic privileges you defined to restrict access to the calculation view called *FlightReservation*.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



## Procedure

1.  Create a folder named "`defaults`" under the `src/` folder.

    In the *FlightReservation* project workspace, locate the database module and right-click the folder `src/`, choose *New Folder* in the context menu, and name the new folder `defaults`.

2.  Create the role-definition file `development_debug_role.hdbrole`.

    Browse to the `defaults/` folder in the database module in the *FlightReservation* application's project workspace, and perform the following steps:

    1.  Open the command palette.

        -   Press either [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Select the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select *db/src/defaults*, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new database role.

    5.  Select the database artifact type, for example, a database role.

        In the command palette, type `hdbro` and choose *Role \(hdbrole\)* in the list that appears.

    6.  Name the file "`development_debug_role`".

        The Wizard appends the appropriate file suffix \(`.hdbrole`\) to the role name.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL role-definition artifacts have the file extension `.hdbrole`, for example, `myRole.hdbrole`.

    7.  Save the changes and create the new database-role artifact; choose *Create*.


3.  Define the contents of the SQL DDL role `development_debug_role.hdbrole`.

    > ### Tip:  
    > If the auto-complete feature is enabled in the text \(code\) editor, the SAP HANA Native Application dev space provides context-sensitive descriptions of tags and properties in JSON-based HDI artifacts, for example: `hdbrole` and `hdbroleconfig`, `hdbgrants`, `hdbsynonym` and `hdbsynonymconfig`. For common scenarios, templates are provided, too.

    Locate and right-click the role-definition file that you created in the previous step, for example, `development_debug_role.hdbrole`, choose *Open with* \> *Code Editor*, and add the following SQL DDL code that defines the role scope:

    `db/src/defaults/development_debug_role.hdbrole`

    ```json
    {
      "role": {
        "name": "development_debug_role",
        "schema_analytic_privileges": [
          {
            "privileges": [
              "AP1",
              "APX"
            ]
          }
        ]
      }
    }
    ```

    By default, *SAP Business Application Studio* opens a role-definition artifact in the *Role Editor*, which displays a graphical representation of the role. In the *Role Editor*, the privileges `AP1` and `APX` are listed in the *Analytic Privileges* tab.

    > ### Tip:  
    > To switch between the *Role Editor* and the text-based *Code Editor*, you can either choose the toggle-editor button in the tool bar next to the help icon or simply right-click the role-definition artifact that you want to open, and choose *Open with* \> *\[Code Editor | Role Editor\]*. Changes made to the open artifact during the editing session are synchronized between both editors. Note that the *Role Editor* is not able to open an incorrectly formatted file.

4.  Save the configuration changes.

5.  Build and deploy the new database role.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

    > ### Note:  
    > A mismatch between the installed SAP HANA version and the SAP HANA version specified in the `.hdiconfig` file \(with the optional parameter `"minimum_feature_version"`\) can cause problems with the deployment operation.

6.  Use the `development_debug_role` to assign analytic privileges to the user that runs a data preview in SAP Business Application Studio.

    Similar to the established `default_access_role`, the new `development_debug_role` can be used to add additional privileges to the application user, for example, to enable access to data preview features in SAP Business Application Studio's calculation-view editor.

    > ### Caution:  
    > This `development_debug_role` is intended for development and debugging only; it is not intended for use in productive scenarios.

    If a role-definition file exists at the path `src/defaults/development_debug_role.hdbrole`, and this file defines a role named `development_debug_role`, and is explicitly included in the deployment using the `--deploy` option, for example, in the application project's `package.json` file, then the HDI Deployer grants the deployed `development_debug_role` role to the service instance’s global `access_role`.

    The following example shows how to use the `--deploy` option with the HDI deployer in the application's `db/package.json` file to enable the `development_debug_role` role:

    > ### Sample Code:  
    > `myapp/db/package.json`
    > 
    > ```
    > {
    >   "name": "deploy",
    >   "dependencies": {
    >     "@sap/hdi-deploy": "^4.*"
    >   },
    >   "scripts": {
    >     "start": "node node_modules/@sap/hdi-deploy/deploy.js --deploy src/defaults/development_debug_role.hdbrole"
    >   }
    > }
    > ```


**Related Information**  


[Create Analytic Privileges for Your Calculation View](create-analytic-privileges-for-your-calculation-view-8ff23ca.md "Use analytic privileges to restrict access to your calculation view's data.")

[Create a Calculation View for your Application in Business Application Studio](create-a-calculation-view-for-your-application-in-business-application-studio-d74bfe7.md "Use the tools provided with Business Application Studio to create a calculation view.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

