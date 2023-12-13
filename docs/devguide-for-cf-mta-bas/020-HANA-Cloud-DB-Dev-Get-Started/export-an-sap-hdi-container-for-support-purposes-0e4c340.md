<!-- loio0e4c3403b64d40f093a8a2cb78f9944b -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Export an SAP HDI Container for Support Purposes

An HDI container administrator or database administrator can export an HDI container to a table or a file.



<a name="loio0e4c3403b64d40f093a8a2cb78f9944b__prereq_ux4_zbq_sqb"/>

## Prerequisites

-   If the exported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the exported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.
-   The tables in the schema of the exported container must not be larger than 2GB.



## Context

The export of a source HDI container is performed by calling the built-in procedure `C1#DI.EXPORT_CONTAINER_FOR_COPY`. After the export procedure has completed successfully, the specified table or file contains not only the objects in the source container’s API schema \(`C1#DI`\) but also the deployed objects of the source container’s run-time schema, including all dependent data.

For more information about this procedure, see *Export an SAP HDI Container for Copy Purposes* in *Related Information* below.

> ### Note:  
> If you choose to include table data as part of the export package along with the table definition, bear in mind that tables can contain sensitive data, for example, personal information such as names, addresses, or credit-card details.

To export a container for support purposes, perform the following steps:



## Procedure

1.  Open in SAP Business Application Studio the application project whose database artifacts you want to export.

2.  Start the *Support Mode Export Assistant* Wizard.

    Use the alternate mouse button to select a database artifact in the application project explorer and choose *Start Support Mode Export* in the context-sensitive menu.

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
    
    Click <span style="font-size:24px;line-height: 28px;"><span class="SAP-icons"></span></span> \(Add artifacts\)to select the database artifacts you want to include in the export package.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Include container data* \(optional\)
    
    </td>
    <td valign="top">
    
    -   *Yes*

        Include the content of the objects selected for export, for example, tables.

        > ### Note:  
        > Tables can contain sensitive data, for example, personal information such as names, addresses, or credit-card details.

    -   *No* \(default\)

        Include only the catalog details; do not include the content of the objects selected for export.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    *Include external dependency options* \(optional\)
    
    </td>
    <td valign="top">
    
    -   *Yes* \(default\)

        Include in the export package any references to objects that are outside the HDI container in which the objects selected for export are located.

    -   *No* 

        Do not include references to objects that are outside the HDI container in which the objects selected for export are located.


    To collect external object definitions, the database user performing the export operation must have the "`CATALOG READ`" system privilege in the target database. The database user must also have the "`SELECT`" privilege on the "`_SYS_BI`" schema to export the BIMC entries. Typically this user is an HDI administrator, an HDI container administrator, if available, but could also be the `DBADMIN` of the database instance.

    > ### Note:  
    > To confirm that the specified user has access to the target database, provide the credentials for the database user and choose *Verify*.


    
    </td>
    </tr>
    </table>
    
4.  Export the specified artifacts.

    Choose *Export* to start the export process, which packs the selected artifacts into a `Zip` file that you can forward to the support team for analysis.

    SAP Business Application Studio displays the result of the export operation in the notification pane, for example:

    ***Exported files archived in /home/user/projects/FlightReservation/SupportModeExports/Export-1653461058076.zip***


**Related Information**  


[Export an SAP HDI Container for Copy Purposes (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/c25ee286cee5496cb96fdf5875f444a2.html "An HDI container administrator can export an HDI container to a table, which can then be used to import the container into a database.") :arrow_upper_right:

