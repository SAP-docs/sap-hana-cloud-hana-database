<!-- loio91b08cc524064057a87a56ab3798d234 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Load Data into a Database Table with the "hdbtabledata" Artifact

Use an `hdbtabledata` artifact to load data external data into an existing database table.



<a name="loio91b08cc524064057a87a56ab3798d234__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Business Application Studio with the *SAP HANA Native Application* extension installed in your development workspace. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a dev space and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multi-target application \(or just the database module\) is deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



## Context

You can use the `hdbtabledata` development object to enable the loading of data from one or more comma-separated-values \(CSV\) files into the specified target tables during their creation. The CSV files used as the data source are also created as part of this exercise.



## Procedure

1.  Start SAP Business Application Studio.

2.  Open the application project to which you want to add your SQL DDL table-data artifact.

3.  Create the table-data definition file.

    Create a new folder for the table-data definition file in the database module of your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data</code>, where you want to create the new SQL DDL table-data definition file and perform the following steps:

    1.  Create a new folder for your table-data file.

        In the `db` module of your application project, right click the `src/` folder, create a new folder named "`data`".

    2.  Open the command palette.

        -   Press  [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Find Command...*

    3.  Create a new SAP HANA database artifact.

        Type ***hana*** in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    4.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *db/src/data* folder, and choose *Open*.

    5.  Select the database version.

        Use the drop-down menu provided to choose *HANA Cloud* as the database where you want to create the new artifact.

    6.  Select the database artifact type, for example, table data.

        In the *Artifact Type* box, type ***hdbt***, and choose *Table Data \(hdbtabledata\)* from the list that appears.

    7.  Name the file *PurchaseDemo*.

        The appropriate file suffix \(`.hdbtabledata`\) is appended to the name by the Wizard.

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL table-data definition artifacts have the file extension `.hdbtabledata`, for example, `PurchaseDemo.hdbtabledata`.

    8.  Save the changes and create the new database table-data artifact; choose *Create*.


4.  Define the structure of the table data you want to import.

    If the new table-data definition file is not automatically displayed by the file-creation wizard, double-click the table-data definition file you created in the previous step, for example, `PurchaseDemo.hdbtabledata`, and add the code that defines the data, for example: the data source \(a CSV file\), the target table where the data is inserted, any column mappings, etc., as illustrated in the following example:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > `db/src/data/PurchaseDemo.hdbtabledata`
    > 
    > ```json
    > {
    > 	"format_version": 1,
    > 	"imports": [{
    > 		"target_table": "PurchaseOrder.Header",
    > 		"source_data": {
    > 			"data_type": "CSV",
    > 			"file_name": "header.csv",
    > 			"has_header": false,
    > 			"dialect": "HANA",
    > 			"type_config": {
    > 				"delimiter": ","
    > 			}
    > 		},
    > 		"import_settings": {
    >          	"include_filter" : [ ],		
    > 			"import_columns": ["PURCHASEORDERID",
    > 			"NOTEID",
    > 			"PARTNER",
    > 			"CURRENCY",
    > 			"GROSSAMOUNT",
    > 			"NETAMOUNT",
    > 			"TAXAMOUNT",
    > 			"LIFECYCLESTATUS",
    > 			"APPROVALSTATUS",
    > 			"CONFIRMSTATUS",
    > 			"ORDERINGSTATUS",
    > 			"INVOICINGSTATUS"]
    > 		},
    > 		"column_mappings": {
    > 			"PURCHASEORDERID": 1,
    > 			"NOTEID": 6,
    > 			"PARTNER": 7,
    > 			"CURRENCY": 8,
    > 			"GROSSAMOUNT": 9,
    > 			"NETAMOUNT": 10,
    > 			"TAXAMOUNT": 11,
    > 			"LIFECYCLESTATUS": 12,
    > 			"APPROVALSTATUS": 13,
    > 			"CONFIRMSTATUS": 14,
    > 			"ORDERINGSTATUS": 15,
    > 			"INVOICINGSTATUS": 16
    > 		}
    > 	},
    > 	{
    > 		"target_table": "PurchaseOrder.Item",
    > 		"source_data": {
    > 			"data_type": "CSV",
    > 			"file_name": "item.csv",
    > 			"has_header": false,
    > 			"dialect": "HANA",
    > 			"type_config": {
    > 				"delimiter": ","
    > 			}
    > 		},
    > 		"import_settings": {
    >            	"include_filter" : [ ],		
    > 			"import_columns": ["POHeader.PURCHASEORDERID",
    > 			"PRODUCT",
    > 			"NOTEID",
    > 			"CURRENCY",
    > 			"GROSSAMOUNT",
    > 			"NETAMOUNT",
    > 			"TAXAMOUNT",
    > 			"QUANTITY",
    > 			"QUANTITYUNIT" ]
    > 		},
    > 		"column_mappings": {
    > 			"POHeader.PURCHASEORDERID": 1,
    > 			"PRODUCT": 3,
    > 			"NOTEID": 4,
    > 			"CURRENCY": 5,
    > 			"GROSSAMOUNT": 6,
    > 			"NETAMOUNT": 7,
    > 			"TAXAMOUNT": 8,
    > 			"QUANTITY": 9,
    > 			"QUANTITYUNIT": 10
    > 
    > 		}
    > 	}]
    > }
    > 
    > ```

5.  Create the comma-separated-values \(CSV\) files to use as the source for the table data you want to import into your database table.

    You should also create a new folder called "`loads`" to store the data-source files in your project, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data/loads</code> where you want to create the new CSV data-source files and perform the following steps:

    1.  Create a new folder for your CSV files.

        In the `db` module, right-click the `src/data` folder, create a new folder named "`loads`".

    2.  Add a CSV file named `header.csv` to the `db/src/data/loads` folder.

        In the command palette, choose *SAP HANA: Create SAP HANA Database artifact*, select the project's *db/src/data/loads* folder in the database module, choose the database version *HANA Cloud* and the artifact type *csv*, and name the new file "***header***".

    3.  Add data to the new CSV file `header.csv`.

        Paste the following code into the new `header.csv` file:

        > ### Code Syntax:  
        > `db/src/data/loads/header.csv`
        > 
        > ```json
        > 0500000000,0000000033,20120101,0000000033,20120101,9000000001,0100000000,EUR,13224.47,11113,2111.47,N,I,I,I,I
        > 0500000001,0000000033,20120102,0000000033,20120102,9000000001,0100000002,EUR,12493.73,10498.94,1994.79,N,I,I,I,I
        > ```

    4.  Add another CSV file named `item.csv` to the `db/src/data/loads` folder.

        In the command palette, choose *SAP HANA: Create SAP HANA Database artifact*, select the project's *db/src/data/loads* folder in the database module, choose the database version *HANA Cloud* and the artifact type *csv*, and name the new file ***item***.

    5.  Add data to the new CSV file `item.csv`.

        Paste the following code into the new `item.csv` file:

        > ### Code Syntax:  
        > `db/src/data/loads/item.csv`
        > 
        > ```json
        > 0500000000,0000000010,HT-1000,,EUR,1137.64,956,181.64,1,EA,20121204
        > 0500000000,0000000020,HT-1091,,EUR,61.88,52,9.88,2,EA,20121204
        > 0500000000,0000000030,HT-6100,,EUR,1116.22,938,178.22,2,EA,20121204
        > 0500000000,0000000040,HT-1001,,EUR,2275.28,1912,363.28,2,EA,20121204
        > 0500000000,0000000050,HT-1092,,EUR,92.82,78,14.82,3,EA,20121204
        > 0500000000,0000000060,HT-6101,,EUR,1116.22,938,178.22,2,EA,20121204
        > 0500000000,0000000070,HT-1002,,EUR,2275.28,1912,363.28,2,EA,20121204
        > 0500000000,0000000080,HT-1090,,EUR,61.88,52,9.88,2,EA,20121204
        > 0500000000,0000000090,HT-6102,,EUR,1674.33,1407,267.33,3,EA,20121204
        > 0500000000,0000000100,HT-1007,,EUR,3412.92,2868,544.92,3,EA,20121204
        > 0500000001,0000000010,HT-1100,,USD,213.96,179.8,34.16,2,EA,20121204
        > 0500000001,0000000020,HT-2026,,USD,35.69,29.99,5.7,1,EA,20121204
        > 0500000001,0000000030,HT-1002,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000040,HT-1101,,USD,213.96,179.8,34.16,2,EA,20121204
        > 0500000001,0000000050,HT-2027,,USD,71.38,59.98,11.4,2,EA,20121204
        > 0500000001,0000000060,HT-1003,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000070,HT-1102,,USD,320.94,269.7,51.24,3,EA,20121204
        > 0500000001,0000000080,HT-2028,,USD,107.06,89.97,17.09,3,EA,20121204
        > 0500000001,0000000090,HT-1004,,USD,3736.6,3140,596.6,2,EA,20121204
        > 0500000001,0000000100,HT-1103,,USD,320.94,269.7,51.24,3,EA,20121204
        > ```


6.  Load the CSV data into the target tables.

    To activate the new table-data definition artifacts and load the source data into the target tables, rebuild the database module of your application, as follows:

    1.  In the *SAP HANA PROJECTS* explorer, locate the application project you want to deploy.

    2.  Choose <span class="FPA-icons"></span> \(Deploy\).

        > ### Note:  
        > A mismatch between the installed SAP HANA version and the version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.


7.  View the content you loaded into the tables in the catalog.

    You can use the *Database Explorer* to view the activated tables in the run-time catalog and verify that the tables contain the imported data.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \( [Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  In the SAP HANA Database Explorer, expand the HDI container that contains the new database artifacts.

    3.  Choose *Tables*.

    4.  Check the two tables `PurchaseOrder.Header` or `PurchaseOrder.Item` are listed in the results pane.

    5.  Select each table to display the contents in the details pane.



**Related Information**  


[Table Data Syntax (.hdbtabledata in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_2_QRC/en-US/35c4dd829d2046f29fc741505302f74d.html "Insert data from other files (for example, CSV, .properties, or .tags files) into database tables.") :arrow_upper_right:

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

