<!-- loio89694d4a9d7c4dd2b1b273056da1bbaa -->

# SAP HDI Sizing and Limitations

Information about limitations to the SAP HANA Deployment Infrastructure.



When configuring, maintaining, and using the SAP HANA deployment infrastructure \(HDI\), bear in mind the restrictions and limits described in the following table:


<table>
<tr>
<th valign="top">

Component Area

</th>
<th valign="top">

Limitation

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

Maximum number of objects per HDI container

</td>
<td valign="top">

Approximately 2 billion

</td>
<td valign="top">

HDI stores file information in a table, which limits the number of files that can be deployed to an HDI container. Depending on the number and types of the database artifacts that are created from each file, this could result in slightly more than 2 billion database objects, for example, if one `hdbsynonym` file contains multiple synonym definitions.

> ### Note:  
> Although a synonym-configuration file \(`hdbsynonymconfig`\) does not have a corresponding database object, it still counts towards the object limit.



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Maximum number of HDI containers

</td>
<td valign="top">

Application run-time: maximum number of Cloud Foundry services

</td>
<td valign="top">

In the application run-time, an HDI container corresponds to a service, so the maximum number of containers is closely related to the maximum number of services. The maximum number of containers is less than \(or equal to\) the maximum number of services, depending on whether there are other types of services.

</td>
</tr>
<tr>
<td valign="top">

Database: maximum number of table rows

</td>
<td valign="top">

In the database, the limit for HDI containers is approximately 80 million, due to the limits for table rows in SAP HANA.

</td>
</tr>
<tr>
<td valign="top">

Max number of services

</td>
<td valign="top">

Defined space quotas, account entitlements, etc.

</td>
<td valign="top">

For Cloud Foundry, the maximum number of services depends on the account entitlements and the space quota.

For more details, see *Related Information* below.

</td>
</tr>
<tr>
<td valign="top">

HDI container size

</td>
<td valign="top">

Schema sizing

</td>
<td valign="top">

You can evaluate the size of an HDI container in the same way as you evaluate any SAP HANA schema. The standard SAP HANA monitoring views should contain all information that is needed. It is also possible to use the built-in statements from the Database Explorer’s statement library to display details of the size of HDI containers. For more details, see *Related Information* below.

</td>
</tr>
<tr>
<td valign="top">

Memory requirements for HDI operations

</td>
<td valign="top">

Business scenario

</td>
<td valign="top">

Sizing recommendations for main memory and disk space provide an indication of execution time for HDI-related operations, for example:

-   Creating an empty container \(including configuring libraries and granting rights\)
-   Writing data into an empty container
-   Making container data \(deploy artifacts in the SAP HANA database\)
-   Dropping a container that contains data

Peak memory usage of 122.5 MB/container can be expected during a `Make` operation for a scenario using ~1GB in ~70 files and 9 folders.

> ### Note:  
> During a `Make` operation, additional main memory is used for temporary data structures, which are removed at the end of the `Make`.

For more details about sizing HDI containers, see *Related Information* below.

</td>
</tr>
</table>

**Related Information**  


[Sizing SAP HANA \(SAP HANA Master Guide\)](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/latest/en-US/d4a122a7bb57101493e3f5ca08e6b039.html)

[Managing Entitlements and Quotas Using SAP BTP Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c8248745dde24afb91479361de336111.html)

[System Views (SAP HANA SQL Reference Guide)](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/2024_1_QRC/en-US/3859e48180bb4cf8a207e15cf25a7e57.html "System views allow you to query for various information about the system state using SQL commands. The results appear as tables.") :arrow_upper_right:

