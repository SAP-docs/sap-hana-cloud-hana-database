<!-- loio0e5ac0b0625b411c8f05346566a3341f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View Database Objects with the Database Explorer

Check the contents of your database with SAP HANA Database Explorer.



<a name="loio0e5ac0b0625b411c8f05346566a3341f__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.
-   The module has been built and bound to the deploy service and the module's assigned HDI container.

> ### Note:  
> For information about developing SAP HANA database applications using the *SAP HANA Native Application* extension in Visual Studio Code, see *SAP HANA Database Explorer Integration for Visual Studio Code \(Visual Studio Marketplace\)* in *Related Information* below.



## Context

The SAP HANA Database Explorer enables you to view the run-time contents of your database module after the corresponding design-time artifacts have been deployed to the HDI container that is created and assigned to the module during deployment.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. The tool is available on SAP Business Application Studio's *Welcome* screen or in the command palette \(*View* \> *Command Palette...* \> *Guided Development*\).



## Procedure

1.  Open SAP Business Application Studio.

    In the *Dev Spaces* manager, choose <span class="SAP-icons-watt"></span> \(Run\)to start a development space in SAP Business Application Studio. You can open the selected development space when the status is *RUNNING*.

2.  Start the SAP HANA Database Explorer.

    The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application. You can start the database explorer in the following ways:

    1.  Start the standalone database explorer from the *Command palette*.

        Open the command palette by choosing *View* \> *Command Palette...* \(or with the keyboard shortcut  [Ctrl\] + [Shift\] + [P\] \), type ***data***, and choose *SAP HANA: Open Database Explorer* in the list of commands displayed.

        > ### Note:  
        > With this method, you need to locate and select the database \(HDI container\) manually.

    2.  Start the standalone database explorer from the *SAP HANA PROJECTS* explorer.

        In the *SAP HANA PROJECTS* explorer, locate the application project containing the database artifacts that you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    3.  Start the embedded database explorer from the *SAP HANA Database Explorer* tool in the views pane of the SAP Business Application Studio.

        In the views pane on the left-hand side of SAP Business Application Studio, choose <span class="FPA-icons"></span> \(SAP HANA Database Explorer\) to display a list of connections to SAP HANA databases and a corresponding catalog browser.

        Since the databases are associated with a Cloud Foundry development space, you must be logged on to Cloud Foundry to see the database list. If you are not already logged on to Cloud Foundry, *SAP HANA Database Explorer* prompts you to provide logon credentials.

        > ### Tip:  
        > To reduce the number of databases displayed, you can filter the list of databases connections by name or part of a name. To highlight the names of all databases that contain a particular string of characters, start typing any part of the database name, for example ***Flight*** or ***12345***. Press [Enter\] to display the contents of the database whose name contains the string you typed.


    The selected database is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Tables*, *Views*, *Column Views*, etc.

3.  Browse the different categories of objects in the database catalog.

    You can filter the objects displayed by choosing an object category and select individual catalog objects from the list displayed to view the contents in the details pane.

    1.  Expand the selected database in the *DATABASE LIST* pane to display a list of all the different categories of objects the database contains, for example: *Column Views*, *Tables*, *Procedures*, *Views*, etc.

        > ### Tip:  
        > To locate a specific database name more quickly you can filter the list of databases displayed according to a defined string. For example, in the *DATABASE LIST* choose <span class="SAP-icons"></span> \(Select Database\)and type the desired string in the text box. Select one or more databases from the filtered list and choose *OK*. The list of selected databases is displayed, and the filter icon remains "active" to indicate that the list of databases is incomplete. To remove the filter, choose <span class="SAP-icons"></span> \(Select Database\), uncheck the selected databases in the filter list, and choose *OK*.

    2.  Select a category, for example, *Tables* or *Column Views* to display all deployed objects of the selected category in the *CATALOG BROWSER*.

        > ### Tip:  
        > To reduce the number of database objects displayed in the *CATALOG BROWSER* and find the object you are looking for more quickly, you can filter the list of database objects by name or part of a name. For example, in the *CATALOG BROWSER* choose <span class="SAP-icons"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Cancel\].

    3.  Right-click a database object in the *CATALOG BROWSER* to display a context-sensitive menu that you can use to perform the following actions:

        > ### Note:  
        > The context-sensitive menu is only displayed if the selected database object is supported, and the list of menu options displayed changes according to the type of object selected, for example, table, user, procedure, etc.


        <table>
        <tr>
        <th valign="top">

        Menu Option


        
        </th>
        <th valign="top">

        Action


        
        </th>
        <th valign="top">

        Note!


        
        </th>
        </tr>
        <tr>
        <td valign="top">
        
                *Open Data*


        
        </td>
        <td valign="top">
        
                Open the SQL console, and display the results of the data-preview SQL query that is run on the selected database artifact.


        
        </td>
        <td valign="top">
        
                The option is only available with:

        -   Tables
        -   Views
        -   Column views
        -   Synonyms \(except synonyms of procedures\)
        -   Public synonyms \(except synonyms of procedures\)


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Copy Name*


        
        </td>
        <td valign="top">
        
                Copy the object name of the selected database object to the clipboard


        
        </td>
        <td valign="top">
        
                 


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Copy Full Name*


        
        </td>
        <td valign="top">
        
                Copy the schema name and the object name of the selected database object to the clipboard.


        
        </td>
        <td valign="top">
        
                If the object is a global object without a schema, only the object name is copied.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Generate CREATE Statement*


        
        </td>
        <td valign="top">
        
                Display the SQL statement used to **create** the selected database object in a new SQL console.


        
        </td>
        <td valign="top">
        
                This operation is only available on schema-local objects.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Copy CREATE Statement*


        
        </td>
        <td valign="top">
        
                Copy to the clipboard the SQL statement used to create the selected database.


        
        </td>
        <td valign="top">
        
                This operation is only available on schema-local objects.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Generate SELECT Statement*


        
        </td>
        <td valign="top">
        
                Copy the SQL statement used to **select** the database object and display it in a new SQL console, where you can run the `SELECT` statement and view the results.


        
        </td>
        <td valign="top">
        
                The option is only available with:

        -   Tables
        -   Views
        -   Column views
        -   Synonyms \(except synonyms of procedures\)
        -   Public synonyms \(except synonyms of procedures\)
        -   Functions


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Generate CALL Statement*


        
        </td>
        <td valign="top">
        
                Display the SQL statement used to **call** the selected database object in a new SQL console, where you can run the `CALL` statement on the chosen database artifact \(for example, a procedure\) and view the results.


        
        </td>
        <td valign="top">
        
                The option is only available with:

        -   Procedures
        -   Synonyms of procedures


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
                *Generate CALL Statement with UI*


        
        </td>
        <td valign="top">
        
                Display the SQL statement used to **call** the selected database object in the graphical user interface \(GUI\), where you can run the `CALL` statement on the chosen database object \(for example, a procedure\) and view the results.


        
        </td>
        <td valign="top">
        
                The option is available with:

        -   Procedures
        -   Synonyms of procedures

        > ### Tip:  
        > Some types of procedure cannot be called with the GUI, for example, procedures with parameters that reference user-defined types \(`TABLE_TYPE`\). You must run the procedure without the GUI.


        
        </td>
        </tr>
        </table>
        

4.  View the details of a selected database object.

    You can use the standalone SAP HANA Database Explorer to view the structure, content, and \(where appropriate\) the raw data contained in the objects deployed to the SAP HANA database, as follows:

    > ### Tip:  
    > To view the content of a deployed database object, use the standalone SAP HANA Database Explorer, which you can start with the <span class="SAP-icons-watt"></span> \(Open Database in Database Explorer\) icon, as described in the next step.

    1.  Open the standalone SAP HANA database explorer.

        In the *DATABASE LIST* pane, expand *SAP HANA Database Explorer Connections*, locate the database containing the database objects whose contents you want to view, for example, *FlightReservation-hdidb-ws-12345*, and choose <span class="SAP-icons-watt"></span> \(Open Database in Database Explorer\).

    2.  Check the tables that you deployed.

        Choose the database object category *Tables* and, in the list of tables displayed in the *Catalog*, choose *FLIGHTRESERVATION* or *PASSENGERS* to display the contents of the selected table in the details pane. Choose *Open Data* to display the *Raw Data* tab, which shows the data you added to the table with the `hdbtabledata` and `CSV` artifacts.

    3.  Check the calculation view that you deployed.

        Choose *Column Views* and, in the list of calculation views displayed, choose *FlightReservation* to display the contents of the selected calculation view in the details pane. Choose *Open Data* to display the *Analysis* and *Raw Data* tabs.

    4.  Check the procedure that you deployed to the HDI container.

        Choose *Procedures* and, in the list of procedures displayed, choose *BookingCount* to display the contents of the selected procedure in the details pane. Choose *Generate CALL Statement with UI*, and in the *Parameters* tab, type ***1*** in the *PASSENGER\_ID \(INTEGER\)* box, and choose <span class="SAP-icons-watt"></span> \(Run\) to run the procedure.

        The value for *BOOKING COUNT* displayed in the *Results* pane should be *2*.


5.  Manage database connections. \(**optional**\)

    You can use the *SAP HANA PROJECTS* explorer to add a database connection or an HDI container, as described below:

    1.  Open the *SAP HANA PROJECTS* explorer.

    2.  Expand the *FlightReservation/db* and *Database Connections* nodes.

        An SAP HANA application project is bound to an HDI container in the SAP HANA database. The name of the bound container is displayed in *Database Connections* along with the current binding status, for example: bound \(green\), and unbound \(grey\).

    3.  Add an HDI container to the SAP HANA Database Explorer \(optional\).

        In the *Database Connections* node, choose <span class="SAP-icons"></span> \(Add database connection\) to display the *Add Database Connection* Wizard.

        > ### Note:  
        > To test the connection details \(for example, the host name, port number, user name and password\), check the option *Validate the database information*. The *Add database Connection* Wizard tries to connect to the specified database using the credentials provided and notifies you immediately if the connection attempt is successful or not.

        Select the connection type, for example, *Existing HDI Container* and type ***Flight*** into the *Select SAP HANA HDI service instance name* box. In the list of HDI containers displayed choose the HDI container you want to add, for example, *FlightReservation-hdidb-workspaces-ws-12345*, and choose *Add*.

        The selected HDI container is displayed in the SAP HANA Database Explorer.

    4.  Bind a database module to an HDI container \(service\).

        When you create a new database application project, the application's database module is bound by default to a new HDI container by means of a Cloud Foundry service. However, you can change this behavior, for example, by choosing to bind the database module to an **existing** container \(service\), which you select from a list displayed by the database-connections Wizard.

        > ### Caution:  
        > Binding an application's database module to an existing HDI container \(service\) can lead to problems caused by the automatic removal of existing artifacts from a previous deployment.

        If the content of the new application's database module does not match the content deployed by the application that was originally bound to the service, then by default all unmatched files are automatically undeployed when you deploy the new application.

        > ### Tip:  
        > To help prevent the undeployment of unmatched files during deployment, you can set the project preferences in SAP Business Application Studio to display warning messages, as described below.

        -   Display a confirmation message that warns about the consequences of binding to an existing container service:

            *Preferences* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm existing service*.

            -   *Continue*

                Bind the current database application to the selected service and proceed to the next option. Before the bind operation finishes, the bind-service Wizard displays a warning about auto-undeployment, and requires you to choose one of the provided options.

            -   *Cancel*

                Do not bind the current database application to the selected service, cancel the bind-service operation, and close the message window.


        -   Display a prompt confirming the disabling of the auto-undeployment of unmatched artifacts:

            *Preferences* \> *Workspace* \> *SAP HANA Project Explorer* \> *Bind: confirm automatic undeployment*.

            -   *Enable* 

                Allow the automatic undeployment of all unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

            -   *Disable* \(automatic undeployment\)

                Do **not** allow the automatic undeployment of all unmatched \(missing or deleted\) files from the corresponding HDI container when redeploying a database application that is bound to an existing service.

                > ### Tip:  
                > Even if you **disable** automatic undeployment, you can still ensure that individual files are undeployed during the redeployment of the database application by adding the files to an allow list defined in the file `db/undeploy.json`. For more details about setting up the `undeploy.json` file, see *HDI Delta Deployment and Undeploy Allow List* in *Related Information*.





**Related Information**  


[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

[Deploy Artifacts with SAP HANA Projects Explorer](deploy-artifacts-with-sap-hana-projects-explorer-4bbbaae.md "Use the SAP HANA Projects explorer to deploy and view your application's design- and run-time database artifacts.")

[User Preferences for SAP HANA Native Application Development Tools](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md "Customize the SAP HANA Native Application project workspace by setting or modifying user preferences.")

[SAP HANA Client 2.0 \(SAP Development Tools\)](https://tools.hana.ondemand.com/#hanatools)

[SAP HANA User Store \(SAP HANA Client Interface Programming Reference\)](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/latest/en-US/708e5fe0e44a4764a1b6b5ea549b88f4.html)

[SAP HANA Database Explorer Integration for Visual Studio Code \(Visual Studio Marketplace\)](https://marketplace.visualstudio.com/items?itemName=SAPSE.hana-database-explorer)

