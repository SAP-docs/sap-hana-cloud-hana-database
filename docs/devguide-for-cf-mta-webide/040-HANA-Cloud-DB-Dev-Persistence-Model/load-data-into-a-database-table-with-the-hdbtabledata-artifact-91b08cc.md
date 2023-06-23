<!-- loio91b08cc524064057a87a56ab3798d234 -->

# Load Data into a Database Table with the "hdbtabledata" Artifact

Use an `hdbtabledata` artifact to load data external data into an existing database table.



<a name="loio91b08cc524064057a87a56ab3798d234__prereq_wmq_cdt_sfb"/>

## Prerequisites

To complete this task successfully, note the following prerequisites:

-   You must have access to an SAP HANA system.
-   For the purposes of this tutorial, you must have access to SAP Web IDE Full-Stack. Generally though, you can use any text editor to create a design-time artifact.
-   You must have already created a development workspace and a multitarget application \(MTA\) project.
-   You must already have created a database module for your MTA application project.
-   You must already have set up an HDI container for the database artifacts

    > ### Note:  
    > A container setup file \(`.hdiconfig`\) is required to define which plug-ins to use to create the corresponding catalog objects from your design-time artifacts when the multi-target application \(or just the database module\) is deployed.

-   To view run-time objects, you must have access to the SAP HANA Database Explorer tools that enable you to view the contents of the catalog.



## Context

You can use the `hdbtabledata` development object to enable the loading of data from one or more comma-separated-values \(CSV\) files into the specified target tables during their creation. The CSV files used as the data source are also created as part of this exercise.



## Procedure

1.  Start SAP Web IDE Full-Stack.

2.  Open the application project to which you want to add your SQL DDL table-data artifact.

3.  Create the table-data definition file.

    Create a new folder for the table-data definition file in the database module of your application's project workspace, for example, <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data</code>, where you want to create the new SQL DDL table-data definition file and perform the following steps:

    1.  Right-click the folder where you want to create the SQL DDL table-data definition file and choose *New* \> *Folder* in the context-sensitive pop-up menu and enter *data* as the folder name.

    2.  Right-click the `data/` folder where you want to create the SQL DDL table-data definition file and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    3.  Enter the name of the table-definition file in the *File Name* box, for example, `PurchaseDemo.hdbtabledata`.

        > ### Tip:  
        > Use the drop-down menu in the *File Type* box to manually define the file extension, for example, `.hdbtabledata`. The file extension is used to determine which plug-in to use to create the corresponding run-time object during deployment. SQL DDL table-data definition artifacts have the file extension `.hdbtabledata`, for example, `PurchaseDemo.hdbtabledata`.

    4.  Choose *Finish* to save the new SQL DDL table-data definition file in the`data/` folder of the database module in your local project workspace.


4.  Define the structure of the table data you want to import.

    If the new table-data definition file is not automatically displayed by the file-creation wizard, double-click the table-data definition file you created in the previous step, for example, `PurchaseDemo.hdbtabledata`, and add the code that defines the data, for example: the data source \(a CSV file\), the target table where the data is inserted, any column mappings, etc., as illustrated in the following example:

    > ### Note:  
    > The following code example is provided for illustration purposes only.

    > ### Sample Code:  
    > <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data/PurchaseDemo.hdbtabledata</code>
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

    1.  Right-click the folder where you want to create the new folder, choose *New* \> *Folder* in the context-sensitive pop-up menu, and enter *loads* as the folder name.

    2.  Right-click the `data/loads/` folder where you want to create the CSV file and choose *New* \> *Database Artifact* in the context-sensitive pop-up menu.

    3.  Enter the name of the CSV file in the *File Name* box, for example, `header.csv`.

        > ### Tip:  
        > Use the drop-down menu in the *File Type* box to manually define the file extension, for example, `.csv`. The file extension is used to determine which plug-in to use to create the corresponding run-time object during deployment. CSV artifacts have the file extension `.csv`, for example, `header.csv`.

    4.  Choose *Finish* to save the new CSV file in the `data/loads` folder of the database module in your local project workspace.

    5.  Add data to the new CSV file `header.csv` in the `data/loads` folder of the database module in your local project workspace.

        > ### Sample Code:  
        > <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data/loads/header.csv</code>
        > 
        > ```json
        > 0500000000,0000000033,20120101,0000000033,20120101,9000000001,0100000000,EUR,13224.47,11113,2111.47,N,I,I,I,I
        > 0500000001,0000000033,20120102,0000000033,20120102,9000000001,0100000002,EUR,12493.73,10498.94,1994.79,N,I,I,I,I
        > ```

    6.  Create a new CSV file called `item.csv`.

        Repeat these steps described above to create a new CSV file that contains the data for the purchase order items. The CSV file should be called `item.csv` and be placed in the folder `loads` folder of the application's database module alongside the `header.csv` CSV file.

    7.  Add data to the new CSV file `item.csv` in the `data/loads` folder of the database module in your local project workspace.

        > ### Sample Code:  
        > <code><i class="varname">&lt;MyApp1&gt;</i>/HDB/src/data/loads/item.csv</code>
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

    8.  Save all the table-data definition and CSV files.

    9.  Build the database module again.


6.  Load the CSV data into the target tables.

    To activate the new table-data definition artifacts and load the source data into the target tables, rebuild the database module of your application, as follows:

    1.  Right-click the new database module in your application project.

    2.  In the context-sensitive pop-up menu, choose *Build* \> *Build*.

        > ### Tip:  
        > You can follow progress of the build in the console at the bottom of the code editor.


7.  View the content you loaded into the tables in the catalog.

    You can use the *Database Explorer* to view the activated tables in the run-time catalog and verify that the tables contain the imported data.

    1.  Right-click the database module in your application project and in the context menu choose *Open HDI Container*.

    2.  Select *Tables* from the list; a list of activated tables is displayed in the *Catalog* pane.

    3.  Select and right-click a table \(for example, `PurchaseOrder.Header` or `PurchaseOrder.Item`\) and in the context menu choose *Open Data*.



**Related Information**  


[Table Data Syntax (.hdbtabledata in SAP HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_2_QRC/en-US/35c4dd829d2046f29fc741505302f74d.html "Insert data from other files (for example, CSV, .properties, or .tags files) into database tables.") :arrow_upper_right:

[Create a Database Table with SQL Data Definition Language](create-a-database-table-with-sql-data-definition-language-879ce23.md "Define a design-time database table using the SQL Data Definition Language (DDL) syntax.")

[Data Definition Statements \(SQL Reference\)](https://help.sap.com/viewer/4fe29514fd584807ac9f2a04f6754767/latest/en-US/209ce8cd75191014bcd59c2b379a17c9.html)

