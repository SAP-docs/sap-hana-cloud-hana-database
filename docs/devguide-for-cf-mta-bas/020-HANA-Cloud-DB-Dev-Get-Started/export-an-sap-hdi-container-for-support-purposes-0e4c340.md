<!-- loio0e4c3403b64d40f093a8a2cb78f9944b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Export an SAP HDI Container for Support Purposes

You can use the *Support Mode Export Assistant* to export selected objects \(and dependencies\) from an HDI container to a table or a file that can be used by support teams to troubleshoot problems.



<a name="loio0e4c3403b64d40f093a8a2cb78f9944b__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   A database user is available who has the permissions required to access the external dependencies and container metadata.
-   The tables in the schema of the exported container must not be larger than 2GB.



## Context

If a support team requires a copy of an HDI container \(or selected database obects in an HDI container\) to investigate a problem, you can use the *Support Mode Export Assistant* provided by SAP HANA Native Application dev space for SAP Business Application Studio to export selected objects \(along with any relevant dependencies\) from the specified HDI container to a table or file. The exported package can then be forwarded to the support team for analysis. You can also have the option of including additional components in the export package, for example:

-   External-dependency object definitions
-   HDI metadata \(for example, of calculation views in the `_SYS_BI` schema\)
-   SQL query and a corresponding plan graph \(PlanVisualization\)

> ### Note:  
> A database user with special privileges is required to collect external object definitions and HDI container metadata \(for example, for calculation views\). For more information about which privileges are required, see step 3 \(defining options\) in the procedure below.

To export an HDI container \(or selected database objects\) to a table or file for troubleshooting purposes, perform the following steps:



## Procedure

1.  Start SAP Business Application Studio and open the application project whose database artifacts you want to export.

2.  Start the *Support Mode Export Assistant* Wizard.

    Use the alternate mouse button to select a database artifact in the application project explorer and choose *Start Support Mode Export* in the context-sensitive menu.

    > ### Tip:  
    > You can also start the export Wizard from the command palette. Press [Ctrl\] + [Shift\] + [P\] , search for “`support`”, and choose *SAP HANA: Support Mode Export Assistant* from the list of options displayed.

3.  Define the options desired for the export process.


    <table>
    <tr>
    <th valign="top">

    Option
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    *Select artifacts* 
    
    </td>
    <td valign="top">
    
    If you launched the *Support Mode Export Assistant* Wizard from the context-sensitive menu in the project explorer, the database artifact you selected is displayed in the list of artifacts to be exported. To include additional artifacts in the export package, choose <span style="font-size:24px;line-height: 28px;"><span class="SAP-icons-V5"></span></span> \(Add Artifacts\).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Include container data?* \(optional\)
    
    </td>
    <td valign="top">
    
    -   *Yes*: Include the content of the objects selected for export, for example, tables.

        > ### Note:  
        > Tables can contain sensitive data, for example, personal information such as names, addresses, or credit-card details.

    -   *No* \(default\): Include only the catalog details; do not include the content of the objects selected for export.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Include external dependency object definitions?* \(optional\)
    
    </td>
    <td valign="top">
    
    -   *Yes* \(default\): Include in the export package any references to objects that are outside the HDI container in which the objects selected for export are located.

        > ### Tip:  
        > See *Database user credentials* below for more information about the privileges required to access external dependency object definitions.

    -   *No*: Do not include references to objects that are outside the HDI container in which the objects selected for export are located.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Include calculation-view metadata from the \_SYS\_BI schema?* \(optional\)
    
    </td>
    <td valign="top">
    
    -   *Yes* \(default\): Include in the export package any metadata for HDI objects in the `_SYS_BI` schema, which is typically related to calculation views.

        > ### Tip:  
        > See *Database user credentials* below for more information about the privileges required to read a calculation view's metadata.

    -   *No*: Do not include in the export package any metadata for HDI objects in the `_SYS_BI` schema.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Database user credentials* \(optional\)
    
    </td>
    <td valign="top">
    
    If you want to include external object definitions and calculation-view metadata in the export package, you must specify a database user who has the "`CATALOG READ`" system privilege in the target database and the "`SELECT`" privilege on the "`_SYS_BI`" schema, respectively .

    > ### Tip:  
    > The `DBADMIN` user has these privileges and can grant the required privileges to another database user. To confirm that the specified user has the required access to the external objects, type the credentials of the database user in the boxes provided and choose *Verify*.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Plan graph \(PlanViz\)* \(optional\)
    
    </td>
    <td valign="top">
    
    If you want to include an SQL query in the export package, choose *Yes* and paste the query into the box provided.

    You can choose to generate a Plan Vizualizer graph for the SQL query and include the plan graph in the export package.

    You also need to confirm if the default run-time \(RT\) user account should be used to generate the plan graph.

    > ### Note:  
    > If you choose not to use the run-time \(RT\) user to generate the plan graph, you must provide the credentials of an alternative database user who has the privileges required to generate the plan graph. Choose *Verify* to test the connection.


    
    </td>
    </tr>
    </table>
    
4.  Export the specified artifacts.

    Choose *Export* to start the export process, which packs the selected artifacts into a `Zip` file that you can forward to the support team for analysis.

    SAP Business Application Studio displays the result of the export operation in the notification pane, for example:

    ***Exported files archived in /home/user/projects/FlightReservation/SupportModeExports/Export-1653461058076.zip***


**Related Information**  


[Export an SAP HDI Container for Copy Purposes (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_3_QRC/en-US/c25ee286cee5496cb96fdf5875f444a2.html "An HDI container administrator can export an HDI container to a table, which can then be used to import the container into a database.") :arrow_upper_right:

[Analyzing SQL Execution with the Plan Visualizer \(SAP HANA Cloud, SAP HANA Database Administration Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/f0c2cd381a39460aab7c20d9bb11f74d.html)

