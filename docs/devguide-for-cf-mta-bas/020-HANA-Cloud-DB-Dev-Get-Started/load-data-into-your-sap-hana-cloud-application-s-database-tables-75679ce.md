<!-- loio75679ced7f8d40a09128161f00c194c1 -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Load Data into your SAP HANA Cloud Application's Database Tables

Use the tools provided with SAP Business Application Studio to populate the new database tables with data stored in CSV \(comma separated values\) files.



<a name="loio75679ced7f8d40a09128161f00c194c1__prereq_tql_yyh_qmb"/>

## Prerequisites

-   You are logged into SAP Business Application Studio.
-   The application project you created in the previous tutorial is available.
-   The application project contains a database module called *db*
-   The tables you created in the *db* module in the previous tutorial \(`passengers` and `flightreservation`\) are available.



<a name="loio75679ced7f8d40a09128161f00c194c1__context_lhm_xyh_qmb"/>

## Context

This tutorial shows how to use `hdbtabledata` artifacts to populate database tables with data stored in CSV files that are part of application's database module.

> ### Tip:  
> The *Get Started with SAP HANA* tutorial in SAP Business Application Studio's *Guided Development* tool helps you to complete this task. Choose ![](images/BAS_icon_GuidedDevCenter_b7736b4.svg) \(*Guided Development Center*\) in SAP Business Application Studio's *Views* pane or open the command palette \(*View* \> *Command Palette...*\) and search for *Guided Development Center*. In the list of guided development tutorials, choose *Create SAP HANA Database Applications & Artifacts* \> *Get Started with SAP HANA*.



<a name="loio75679ced7f8d40a09128161f00c194c1__steps_hm4_wvh_qmb"/>

## Procedure

1.  Create a new folder for your table-data and CSV files.

    In the `db` module's `src` folder, create a new folder named "`loads`".

2.  Add a file named `BookingDemo.hdbtabledata` to the `src/loads` folder.

    1.  Open the command palette.

        -   Press [Crtl\] + [Shift\] + [P\]  or
        -   Press [F1\] or
        -   Choose *View* \> *Command Palette...*

    2.  Create a new SAP HANA database artifact.

        Type `hana` in the command palette and choose *SAP HANA: Create SAP HANA Database Artifact* in the list of commands displayed.

        The *Create SAP HANA Database Artifact* Wizard is displayed.

    3.  Choose the file location where you want to add the new database artifact.

        Choose *Browse for Folder*, select the project's *src/loads/* folder, and choose *Open*.

    4.  Select the database version.

        Use the drop-down menu provided to choose *SAP HANA Cloud* as the database where you want to create the new database role.

    5.  Select the database artifact type, for example, table.

        In the *Artifact Type* box, type `hdbt`, and choose *Table Data \(hdbtabledata\)* from the list that appears.

    6.  Name the file *BookingDemo*.

        The appropriate file suffix \(`.hdbtabledata`

        > ### Tip:  
        > The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. SQL DDL table-data-definition artifacts have the file extension \) is appended to the name by the Wizard. `.hdbtabledata`, for example, `MyTableDataDefinition.hdbtabledata`

    7.  Save the changes and create the new database table-data artifact; choose *Create*.


3.  Open the new database table artifact for editing.

    > ### Tip:  
    > SAP Business Application Studio provides a wide variety of dedicated editors that correspond to the database artifact types supported by the SAP HANA Deployment Infrastructure \(HDI\). The artifact type, for example, `hdbtable` or `hdbtabledata`, is used by SAP Business Application Studio to determine which editor to open by default to enable editing. Some editors also provide a default template for the artifact type, which you can either adapt, delete, or replace as required.

    Add the following code to the new table data artifact `BookingDemo.hdbtabledata`.

    > ### Sample Code:  
    > `BookingDemo.hdbtabledata` 
    > 
    > ```
    > { 
    >   "format_version": 1, 
    >   "imports": [{ 
    >         "target_table": "PASSENGERS", 
    >         "source_data": { 
    >         "data_type": "CSV", 
    >         "file_name": "passengers.csv", 
    >         "has_header": false, 
    >         "dialect": "HANA", 
    >         "type_config": { 
    >           "delimiter": "," 
    >         } 
    >      }, 
    >      "import_settings": { 
    >         "include_filter" : [ ], 
    >         "import_columns": ["PASSENGERID","NAME","ACTIVE","ADDRESS","COUNTRY","PASSPORT","PASSENGERPRIORITYSTATUS"] 
    >      }, 
    >      "column_mappings": { 
    >         "PASSENGERID": 1, 
    >         "NAME": 2, 
    >         "ACTIVE": 3, 
    >         "ADDRESS": 4, 
    >         "COUNTRY": 5, 
    >         "PASSPORT": 6,
    >         "PASSENGERPRIORITYSTATUS":7 
    >      } 
    >   }, 
    >   { 
    >      "target_table": "FLIGHTRESERVATION", 
    >      "source_data": { 
    >         "data_type": "CSV", 
    >         "file_name": "flightreservation.csv", 
    >         "has_header": false, 
    >         "dialect": "HANA", 
    >         "type_config": { 
    >           "delimiter": "," 
    >         } 
    >      }, 
    >      "import_settings": { 
    >         "include_filter" : [ ], 
    >         "import_columns": ["RESERVATIONID","PASSENGERID","MANDT","CARRID","CONNID","FLDATE","SEAT","BOOKINGTIME" ] 
    >      }, 
    >      "column_mappings": { 
    >         "RESERVATIONID": 1, 
    >         "PASSENGERID" : 2, 
    >         "MANDT": 3,      
    >         "CARRID": 4,      
    >         "CONNID": 5, 
    >         "FLDATE": 6,      
    >         "SEAT" : 7 , 
    >         "BOOKINGTIME" : 8 
    >      } 
    >   }] 
    > } 
    > ```

4.  Add a file named `passengers.csv` to the `src/loads` folder.

    In the command palette, choose *SAP HANA: Create SAP HANA Database artifact*, select the project's *src/loads* folder in the database module, choose the database version *SAP HANA Cloud* and the artifact type *csv*, and name the new file `passengers`.

    > ### Tip:  
    > The appropriate file suffix \(`.csv`\) is appended to the file name by the file-creation Wizard. The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. CSV artifacts have the file extension `.csv`, for example, `MyTableData.csv`

5.  Add the following code to the new table data artifact `passengers.csv`.

    > ### Sample Code:  
    > `passengers.csv` 
    > 
    > ```
    > 1,JOEN DIVRO,1,BAR ILAN 8 RAANANA,IL,34567,A
    > 2,MAX MUSTERMANN,1,UNTER DEN LINDEN 528 BERLIN,DE,7362728,B
    > 3,KWADWO OSEI,1,INDEPENDENCE AVE 1957 KUMASI,GH,852741,C
    > 4,FUNMILAYO ADEBANJO,1,ABAYOMI ST 60 LAGOS,NG,978564,D
    > 5,FENG MIAN LIN,1,TANGLIN RD 250 SINGAPORE,SG,436682,E
    > 6,ANAISHA ANAND,1,CHANAKYAPURI 1960 MUMBAI,IN,5579166,F
    > ```

6.  Add a file named `flightreservations.csv` to the `src/loads` folder.

    In the command palette, choose *SAP HANA: Create SAP HANA Database artifact*, select the project's *src/loads* folder in the database module, choose the database version *SAP HANA Cloud* and the artifact type *csv*, and name the new file `flightreservations`.

    > ### Tip:  
    > The appropriate file suffix \(`.csv`\) is appended to the file name by the file-creation Wizard. The file extension is mandatory; it is used to determine which HDI plug-in to call when creating the corresponding run-time object during application build or deployment. CSV artifacts have the file extension `.csv`, for example, `MyTableData.csv`



7.  Add the following code to the new table data artifact `flightreservations.csv`.

    > ### Sample Code:  
    > `flightreservations.csv` 
    > 
    > ```
    > 1,1,300,LH,0402,20100712,43,20100612
    > 2,2,300,LH,0402,20100722,44,20100501
    > 3,3,300,LH,0402,20100726,12,20100315
    > 4,4,300,LH,0402,20101016,15,20100315
    > 5,5,300,LH,0402,20100712,43,20100612
    > 6,6,300,LH,0402,20100722,44,20100501
    > 7,1,400,SQ,0502,20110712,43,20110612
    > 8,2,400,SQ,0502,20110722,44,20110501
    > 9,3,400,SQ,0502,20110726,12,20110315
    > 10,4,400,SQ,0502,20111016,15,20110315
    > 11,5,400,SQ,0502,20110712,43,20110612
    > 12,6,400,SQ,0502,20110722,44,20110501
    > ```

8.  Deploy the database module.

    In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to deploy and choose ![](images/BAS_icon_deploy_4423157.svg) \(*Deploy*\).

    > ### Note:  
    > A mismatch between the installed SAP HANA version and the SAP HANA version specified in the `.hdbconfig` file \(with the optional parameter `"minimmum_feature_version"`\) can cause problems with the deployment operation.

9.  Check that the tables now contain data.

    1.  Display the contents of the HDI container bound to the deployed application.

        In the *SAP HANA PROJECTS* explorer, locate the project containing the artifacts you want to check and choose <span class="SAP-icons-watt"></span> \(Open HDI Container\).

        Alternatively, you can choose *SAP HANA: Open Database Explorer* from the command palette \([Ctrl\] + [Shift\] + [P\] \).

        The selected HDI container is displayed in the SAP HANA Database Explorer, and you can browse through the different categories of database artifacts, for example, *Column Views*, *Tables*, or *Views*.

    2.  Expand the *FlightReservation...* node in the SAP HANA Database Explorer.

    3.  Choose *Tables*.

    4.  Check the two tables \(`PASSENGERS` and `FLIGHTRESERVATION`\) are listed in the results pane.

    5.  Select each table to display the table's contents in the details pane.

        > ### Note:  
        > In the details pane, choose *Open Data* to display the table's raw data.



**Related Information**  


[Add Database Artifacts to your SAP HANA Cloud Database Application](add-database-artifacts-to-your-sap-hana-cloud-database-application-1aa9165.md "Add the underlying design-time database objects to your SAP HANA application.")

[Create a Calculation View for your Application in Business Application Studio](create-a-calculation-view-for-your-application-in-business-application-studio-d74bfe7.md "Use the tools provided with Business Application Studio to create a calculation view.")

[Working with SAP Business Application Studio](working-with-sap-business-application-studio-ebd3400.md "SAP Business Application Studio provides a modular development environment for the development of business applications for SAP HANA Cloud.")

