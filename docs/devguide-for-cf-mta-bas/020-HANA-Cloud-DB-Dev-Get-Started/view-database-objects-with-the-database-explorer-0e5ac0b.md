<!-- loio0e5ac0b0625b411c8f05346566a3341f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# View Database Objects with the Database Explorer

Check the contents of your database with SAP HANA Database Explorer.



<a name="loio0e5ac0b0625b411c8f05346566a3341f__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*.

> ### Note:  
> For information about developing SAP HANA database applications using the *SAP HANA Native Application* extension in Visual Studio Code, see *SAP HANA Database Explorer Integration for Visual Studio Code \(Visual Studio Marketplace\)* in *Related Information* below.



## Context

The SAP HANA Database Explorer enables you to view the run-time contents of your database module after the corresponding design-time artifacts have been deployed to the HDI container that is created and assigned to the module during deployment.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



## Procedure

1.  Open SAP Business Application Studio.

    In the *Dev Spaces* manager, choose <span class="SAP-icons-watt"></span> \(Run\)to start a development space in SAP Business Application Studio. You can open the selected development space when the status is *RUNNING*.

2.  Start the SAP HANA Database Explorer.

    The database explorer enables you to view the run-time objects deployed to the SAP HDI container that is assigned to your SAP HANA database application. You can start the database explorer in the following ways:

    1.  Start the standalone database explorer from the *Command palette*.

        Open the command palette by choosing *View* \> *Command Palette...* \(or with the keyboard shortcut [Ctrl\] + [Shift\] + [P\] \), type `data`, and choose *SAP HANA: Open Database Explorer* in the list of commands displayed.

        > ### Note:  
        > With this method, you need to locate and select the database \(HDI container\) manually.

    2.  Start the standalone database explorer from the *SAP HANA PROJECTS* explorer.

        In the *SAP HANA PROJECTS* explorer, locate the application project containing the database artifacts that you want to explore, for example, *FlightReservation/db*, and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

    3.  Start the embedded database explorer from the *SAP HANA Database Explorer* tool in the views pane of the SAP Business Application Studio.

        In the views pane on the left-hand side of SAP Business Application Studio, choose <span class="FPA-icons-V3"></span> \(SAP HANA Database Explorer\) to display a list of connections to SAP HANA databases and a corresponding catalog browser.

        Since the databases are associated with a Cloud Foundry development space, you must be logged on to Cloud Foundry to see the database list. If you are not already logged on to Cloud Foundry, *SAP HANA Database Explorer* prompts you to provide logon credentials.

        > ### Tip:  
        > To reduce the number of databases displayed, you can filter the list of databases connections by name or part of a name. To highlight the names of all databases that contain a particular string of characters, start typing any part of the database name, for example `Flight` or `12345`. Press [Enter\] to display the contents of the database whose name contains the string you typed.


    The selected database is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Tables*, *Views*, *Column Views*, etc.

3.  Browse the different categories of objects in the database catalog.

    You can filter the objects displayed by choosing an object category and select individual catalog objects from the list displayed to view the contents in the details pane.

    1.  Expand the selected database in the *DATABASE LIST* pane to display a list of all the different categories of objects the database contains, for example: *Column Views*, *Tables*, *Procedures*, *Views*, etc.

        > ### Tip:  
        > To locate a specific database name more quickly you can filter the list of databases displayed according to a defined string. For example, in the *DATABASE LIST* choose <span class="SAP-icons-V5"></span> \(Select Database\)and type the desired string in the text box. Select one or more databases from the filtered list and choose *OK*. The list of selected databases is displayed, and the filter icon remains "active" to indicate that the list of databases is incomplete. To remove the filter, choose <span class="SAP-icons-V5"></span> \(Select Database\), uncheck the selected databases in the filter list, and choose *OK*.

    2.  Select a category, for example, *Tables* or *Column Views* to display all deployed objects of the selected category in the *CATALOG BROWSER*.

        > ### Tip:  
        > To reduce the number of database objects displayed in the *CATALOG BROWSER* and find the object you are looking for more quickly, you can filter the list of database objects by name or part of a name. For example, in the *CATALOG BROWSER* choose <span class="SAP-icons-V5"></span> \(Apply filter\), type the desired name or part of a name in the text box provided, and press [Enter\]. To reset the filter, press [Cancel\].

    3.  Click a database object in the *CATALOG BROWSER* to display the object's metadata in the details pane.

        > ### Note:  
        > This feature is currently available for selected objects only, for example, functions, procedures, and views. You can also view the metadata of supported database object types from a link in the dependency viewer, as described below.

        The information displayed can include the name of the selected object, the schema the selected object is located in, any parameters defined for the object, and the SQL statement used to create the object.

    4.  Right-click a database object in the *CATALOG BROWSER* to display a context-sensitive menu that you can use to perform the following actions:

        > ### Note:  
        > The context-sensitive menu is only displayed if the selected database object is supported, and the list of menu options displayed changes according to the type of object selected, for example, table, view, procedure, etc. For more detailed information about the scope of each individual action, see *Context-sensitive Actions on Database Objects in Database Explorer* in *Related Information* below.

        -   *Open Data*: Preview the data returned by the SQL query run on the selected database object.
        -   *Copy \[Name | Full Name\]*: Copy \(to the clipboard\) the name of the selected database object along with \(*Full Name*\) the name of the schema where the object is located.\)
        -   *Generate \[CREATE | INSERT | SELECT | CALL \] Statement*: Generate the SQL statement used to `CREATE`, `INSERT`, `SELECT`, or `CALL` the selected database object, where available in a new graphical user interface \(*with UI*\).
        -   *Copy CREATE Statement*: Copy \(to the clipboard\) the SQL statement used to `CREATE` the selected database object..
        -   *Open Dependency Viewer*: Display a graphical view of the dependencies between the selected database objects and any other objects.


4.  View the details of a selected database object.

    You can use the standalone SAP HANA Database Explorer to view the structure, content, and \(where appropriate\) the raw data contained in the objects deployed to the SAP HANA database, as follows:

    > ### Tip:  
    > To view the content of a deployed database object, use the standalone SAP HANA Database Explorer, which you can start with the <span class="SAP-icons-watt"></span> \(Open Database in Database Explorer\) icon, as described in the next step.

    1.  Open the standalone SAP HANA database explorer.

        In the *DATABASE LIST* pane, expand *SAP HANA Database Explorer Connections*, locate the database containing the database objects whose contents you want to view, for example, *FlightReservation-hdidb-ws-12345*, and choose <span class="SAP-icons-watt"></span> \(Open Database in Database Explorer\).

    2.  Check the tables that you deployed.

        Choose the database object category *Tables* and, in the list of tables displayed in the *CATALOG BROWSER*, choose *FLIGHTRESERVATION* or *PASSENGERS* to display the contents of the selected table in the details pane. Choose *Open Data* to display the *Raw Data* tab, which shows the data you added to the table with the `hdbtabledata` and `CSV` artifacts.

    3.  Check the calculation view that you deployed.

        Choose *Column Views* and, in the list of calculation views displayed, choose *FlightReservation* to display the contents of the selected calculation view in the details pane. Choose *Open Data* to display the *Analysis* and *Raw Data* tabs.

    4.  Check the procedure that you deployed to the HDI container.

        Choose *Procedures* and, in the list of procedures displayed in the *CATALOG BROWSER* pane, right-click *BookingCount* and choose *Generate CALL Statement with UI*.

        In the *Parameters* tab, type `1` in the *PASSENGER\_ID \(INTEGER\)* box, and choose <span class="SAP-icons-watt"></span> \(Run\) to run the procedure.

        The value for *BOOKING COUNT* displayed in the *Results* pane should be *2*.


5.  Display a graphical representation of the dependencies between the procedure and any underlying objects, for example, tables and views.

    Choose *Procedures* and, in the list of procedures displayed in the *CATALOG BROWSER* pane, right-click *BookingCount* and choose *Open Dependency Viewer*.

    > ### Tip:  
    > You can use the *Dependency Viewer* to display the dependencies between other database objects, too.

    1.  Select and view details of any of the individual objects displayed in the dependency graph, including recently viewed objects.

        > ### Note:  
        > Dependency graphs are cached in storage. When you display an object in the dependency viewer, the dependency data is fetched from the database and saved. The next time you choose the same object, the cached data is retrieved for quicker performance. The *Refresh* button, on the other hand, fetches the latest version of the dependencies from the database.

    2.  Zoom in to an individual object in a schema and back out again to view all objects in the schema.

        To zoom in and out of the dependency view, use the scroll-wheel on your mouse or the resize buttons <span class="FPA-icons-V3"></span> and <span class="FPA-icons-V3"></span>.

        > ### Tip:  
        > To collapse or expand an entire schema, double-click it.

    3.  Show or hide the minimap view.

        The minimap view \(![](images/BAS_FluentUI_contract_down_right_16_regular_2ffad45.svg) \(*Toggle Minimap*\)\) is a subpane that shows where the currently displayed objects are located in the context of a larger and more complicated dependency tree.

        > ### Tip:  
        > To locate and highlight an object in the minimap view, click the object in the main schema view.

    4.  Hide or show selected object types in the dependency viewer.

        Choose :gear: and use the list provided in the *Hide Nodes of Selected Types* box to select the object types that you want to hide in the currently displayed dependency graph.

        To remove the object type from the list of hidden object types and show them in the depencency view again, choose <span class="FPA-icons-V3"></span>.

        > ### Tip:  
        > If a graph seems to be small or incomplete, choose :gear: to display information about the current show/hide settings. Objects can be hidden because the schema to which they belong is collapsed, the graph-depth setting is too low, or specific object types have been excluded from the graph.

    5.  Set the maximum depth \(scope\) of the dependency viewer.

        To help navigation and reduce complexity, you can set the maximum number of links that can be displayed along a single dependency path between the root node \(the run-time database object selected when the dependency viewer is opened\) and other nodes in a dependency graph, as follows:

        -   Locally, for the currently displayed dependency graph \(default: 3\):

            Enter a value in the *Graph Depth \(Maximum\)* box in the dependency viewer's *Settings* dialog and choose *Apply Change*.

        -   Globally, for all dependency graphs \(default: 3\):

            In the tools pane, choose :gear:, then *Settings*, search for *Dependency Viewer: Default Graph Depth*, and enter a new \(non-default\) value, for example, 5.


        > ### Note:  
        > If the specified graph depth \(3, in this example\) is lower than the number of nodes in a long dependency path, then some nodes will not be shown. To ensure that all nodes in a long dependency path are displayed, you need to increase the graph-depth setting accordingly.

    6.  Save the currently displayed dependency view to a local file.

        Choose <span class="FPA-icons-V3"></span> \(Save as...\), and choose the output format to use, for example:

        -   *DOT*

            The DOT format is used for describing hierarchical or layered "directed" graphs, for example, flowcharts or dependency trees.

        -   *SVG*

            The XML-based SVG format is used for defining simple two-dimensional scalable vector graphics.


    7.  Restore the default layout used in the dependency viewer.

        Use <span class="SAP-icons-V5"></span> \(Run layout\) to restore the items displayed in the dependency viewer to the layout used at the start of the current session, for example, after modifying the initial or default layout.

    8.  Lock \(or unlock\) the current layout of the items displayed in the dependency viewer.

        Choose <span class="BusinessSuiteInAppSymbols-V2"></span> \(Toggle graph lock\) to lock \(save\) any modifications made to the layout in the current session or unlock the current layout in order to enable changes.

    9.  Display the metadata of a selected object.

        The metadata includes the definition of the object in SQL, for example, the name of the object, the name of the schema where the object is located, any parameter names as well as the SQL statement used to create the selected object.

        > ### Note:  
        > In the dependency viewer, this feature is currently only available for the database object types "function" \(`hdbfunction`\), "procedure" \(`hdbprocedure`\), and "views" \(`hdbview` or `hdbcalculationview`\).

        To view the metadata of a database object in the dependency viewer, select the object in the displayed schema and choose *Open metadata view* in the object description pane.



**Related Information**  


[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

[HDI Delta Deployment and Undeploy Allow List](../040-HANA-Cloud-DB-Dev-Persistence-Model/hdi-delta-deployment-and-undeploy-allow-list-ebb0a1d.md "The HDI Deployer implements a delta-based deployment strategy including an optional allow list.")

[Deploy Artifacts with SAP HANA Projects Explorer](deploy-artifacts-with-sap-hana-projects-explorer-4bbbaae.md "Use the SAP HANA Projects explorer to deploy and view your application's design- and run-time database artifacts.")

[User Preferences for SAP HANA Native Application Development Tools](user-preferences-for-sap-hana-native-application-development-tools-57e2fe6.md "Customize the SAP HANA Native Application project workspace by setting or modifying user preferences.")

[Context-sensitive Actions on Database Objects in Database Explorer](context-sensitive-actions-on-database-objects-in-database-explorer-777b762.md "A list of available context-sensitive actions that can be performed on SAP HANA database objects in the database explorer.")

[SAP HANA Client 2.0 \(SAP Development Tools\)](https://tools.hana.ondemand.com/#hanatools)

[SAP HANA User Store \(SAP HANA Client Interface Programming Reference\)](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/latest/en-US/708e5fe0e44a4764a1b6b5ea549b88f4.html)

[SAP HANA Database Explorer Integration for Visual Studio Code \(Visual Studio Marketplace\)](https://marketplace.visualstudio.com/items?itemName=SAPSE.hana-database-explorer)

