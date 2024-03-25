<!-- loio7ffe3cc490f04ca997e22326e013e73f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Use the SQL Console for SAP HANA to Query the Database

Learn how to use the SQL console for SAP HANA to run queries on SAP HANA databases.



<a name="loio7ffe3cc490f04ca997e22326e013e73f__prereq_lzg_lsp_xrb"/>

## Prerequisites

Bear in mind the following limitations to features and functionality when using the SQL console for SAP HANA that is embedded in SAP Business Application Studio:

-   It is not possible to set preferences or define keyboard shortcuts in the SQL console for SAP HANA.
-   In the SQL console for SAP HANA, you can only execute SQL statements on an SAP HANA instance \(not on an instance of data lake Relational Engine\).
-   It is not possible to use the SQL console for SAP HANA to run a query as a background activity.



## Context

The SQL console for SAP HANA is a lean version of the regular SQL console, which you can use to execute SQL code directly from the integrated development environment \(IDE\) in SAP Business Application Studio.

To learn how to use the SQL console for SAP HANA, perform the following steps:



## Procedure

1.  Open the *SAP HANA Database Explorer* view in SAP Business Application Studio.

    > ### Note:  
    > To be able to see the list of databases that you want to explore, you must be logged on to Cloud Foundry; the databases are associated with a Cloud Foundry development space. If you are not logged into Cloud Foundry, SAP Business Application Studio prompts you to provide the required user credentials.

    In the views pane on the left-hand side of SAP Business Application Studio, choose <span class="FPA-icons-V3"></span> \(SAP HANA Database Explorer\).

2.  Open the SQL console for SAP HANA.

    In the *DATABASE LIST* pane, locate the database that you want to explore, and choose <span class="FPA-icons-V3"></span> \(Open SAP HANA SQL Console\) to connect to the selected database and open the SQL console for SAP HANA. If you want access to the HDI container-administrator API, choose *<span class="FPA-icons-V3"></span> \(Open SAP HANA SQL Console as HDI Admin\)*. If you cannot find your database in the list, hover the mouse cursor over the database list and choose <span class="FPA-icons-V3"></span> \(Refresh Database List\).

    > ### Tip:  
    > You can also open the SQL console from the *Database Connections* node in *SAP HANA Projects* explorer pane, though only as a normal HDI container user, not as the HDI container-administrator user. The SQL console connects to the HDI container service bound to the selected database connection.

    After the SQL Console opens, choose <span class="SAP-icons-V5"></span> \(View connection settings\)and enable *Auto-commit contents of this SQL console* if you want to ensure that any changes to the database required by the SQL code you run in the SQL console are performed immediately, for example, when inserting or updating data in tables. Auto-commit is useful if you are running multiple SQL commands which contain dependencies. If auto-commit is disabled, you will have to `COMMIT` or `ROLLBACK` any changes manually.

3.  Check the details of the connected database.

    The tool bar in the SQL Console for SAP HANA displays the following information and options when connected to an SAP HANA database or an HDI container service instance:

    ```
    Current Schema: FlightReservation_HDI_DB_<#> Instance: FlightReservation-hdidb-ws-ab1cd (GFN)                    
    ```

    The information displayed includes the name of the database instance to which the SQL console for SAP HANA is currently connected along with \(in brackets\) the name of the Cloud Foundry space bound to which the database is bound, for example, *FlightReservation-hdidb-ws-ab1cd \(GFN\)*. Choose <span class="FPA-icons-V3"></span> \(Information\)to reveal additional details of the database connection type, for example, SAP HANA, SAP HANA Cloud, or HDI-container service instance.

    > ### Tip:  
    > Click the current schema or instance name to see a list of all the schemas and database instances for which the currently logged-on user has access permissions. For more information about the options, connection settings, and tools available in the SQL Console for SAP HANA, see *Related Information* below.

4.  Run an SQL statement to perform a database query.

    Paste the following SQL statement into the SQL console for SAP HANA and choose <span style="color:#2B7D2B;"><span class="FPA-icons-V3"></span></span> \(Run\):

    > ### Sample Code:  
    > Sample SQL Command
    > 
    > ```
    > SELECT * FROM EFFECTIVE_PRIVILEGE_GRANTEES WHERE (OBJECT_TYPE = 'SYSTEMPRIVILEGE') 
    > AND (PRIVILEGE = 'EXPORT' OR PRIVILEGE='IMPORT');
    > ```

    To cancel a running SQL statement, choose <span style="color:#BB0000;"><span class="FPA-icons-V3"></span></span> \(Cancel Statement\).

    > ### Tip:  
    > Choose <span class="BusinessSuiteInAppSymbols-V2"></span> \(Show/Hide Statement Help\) to display \(or hide\) a side panel in the SQL console, which displays syntax suggestions for SQL statements and provides access to information about metadata SQL objects. The side panel also displays details of the objects referenced in the current console \(for example, tables, views, procedures, and built-in functions\) and provides links to the corresponding SQL reference documentation. For more details, see *SQL Statement Syntax Help* in *Related Information* below.

    The SQL console for SAP HANA permits the following *Run* options:

    > ### Tip:  
    > For more information about the run options available in the SQL Console for SAP HANA, see *Related Information* below.

    -   *Run*

        Run all SQL statements.

    -   *Run Statement*

        Run individual SQL statements.

    -   *Run Line*

        Run the contents of the currently selected line of SQL code.

    -   *Run with parameters*

        Run the contents of the currently selected line of SQL code with the parameters provided.

        > ### Tip:  
        > The run-with-parameters option is only available in the *Parameters* tab.


    The results returned by the SQL query are displayed in the *Results \#* tab.

    The *Messages* tab displays information about errors that occurred during the SQL query run.

    The *History* tab displays a list of the most recent SQL statements that you have run in the SQL console.

5.  Run SQL stored in a file \(**optional**\).

    The SQL console allows you to run SQL directly from a file stored in a file system. You can also save the code displayed in the SQL console to a file, as described in the following steps:

    1.  Run SQL stored in a file.

        To open an SQL file from a file system, choose :open_file_folder:, locate and select the file in the file explorer, and choose *Open*. The name of the open file is displayed in the tab title, and the contents of the open file are displayed in the SQL console.

    2.  Save changes to the currently open SQL file.

        The SQL console periodically saves the contents of the SQL console to the currently open file, whose name is displayed in the tab title. If you want to manually save any updates or changes, choose :floppy_disk:.

    3.  Save the current contents of the SQL console to a file.

        To save the code that is currently displayed in the SQL console to a file in a local file system, choose ![](images/BAS_icon_SQLsaveToFile_f441257.svg)*\(Save SQL to file\)*, locate and select the target folder in the file explorer, specify a file name, and choose *Save*. The name of the specified file is displayed in the tab title of the SQL console.


6.  Run an SQL query that uses parameters.

    The SQL console displays the *Parameters* tab to enable you to provide a value for each parameter included in an SQL query. Use the text boxes provided to define a value for each parameter and run the SQL query by choosing <span style="color:#2B7D2B;"><span class="FPA-icons-V3"></span></span> \(Run with parameters\).

    > ### Note:  
    > It is not possible to run an SQL statement that contains parameters in combination with other SQL statements. If you run another SQL query that does not require any parameters, the SQL console displays a warning that any values and parameters currently defined in the *Parameters* tab will be ignored and discarded.

7.  Connect to a different database.

    To disconnect the SQL console for SAP HANA from the currently selected database and connect it to a different database, choose <span class="FPA-icons-V3"></span> \(Connect this SQL console to a different database\) in the tool bar of the SQL Console for SAP HANA and select the new database from the list displayed.

    > ### Tip:  
    > If you are using the SAP HANA Project Explorer for Visual Studio Code, you can connect to a local database or a SAP HANA User Store.


**Related Information**  


[Querying the Database \(SAP HANA Database Explorer Guide\)](https://help.sap.com/viewer/a2cea64fa3ac4f90a52405d07600047b/cloud/en-US/beec2b0b56d6498ea9fb3706dbfc9688.html)

[SQL Statement Syntax Help \(SAP HANA Database Explorer Guide\)](https://help.sap.com/docs/HANA_CLOUD/a2cea64fa3ac4f90a52405d07600047b/2f39e4fdd67545cf805b557357c5a7b3.html#statement-syntax-help)

[SAP HANA Database Explorer for VS Code \(Visual Studio Marketplace\)](https://marketplace.visualstudio.com/items?itemName=SAPSE.hana-database-explorer)

[Options, Settings, & Tools in the SQL Console for SAP HANA](options-settings-tools-in-the-sql-console-for-sap-hana-29ffdfb.md "An overview of the information and options available in the SQL Console.")

