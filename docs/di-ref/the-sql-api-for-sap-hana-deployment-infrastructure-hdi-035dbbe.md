<!-- loio035dbbe23ac14242b1f7d724dd102825 -->

# The SQL API for SAP HANA Deployment Infrastructure \(HDI\)

An SQL application programming interface \(API\) is available to help maintain the SAP HANA Deployment Infrastructure \(HDI\).

In this topic, you can find information about the following components of the SQL API for HDI:

-   [SQL APIs for HDI](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_jx1_f4c_l1b)

-   [Parameters for API Procedures](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_s3f_x2b_31b)

-   [Table Types](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_r14_y2b_31b)

-   [Predefined Parameter Tables](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_sy1_z2b_31b)

-   [Result Sets](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_grb_1fb_31b)

-   [Return Codes](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_nsr_1fb_31b)

-   [Request ID](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_yff_bfb_31b)

-   [Messages](the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md#loio035dbbe23ac14242b1f7d724dd102825__section_vjs_bfb_31b)




<a name="loio035dbbe23ac14242b1f7d724dd102825__section_jx1_f4c_l1b"/>

## SQL APIs for HDI

The SAP HANA Deployment Infrastructure \(HDI\) can be seen as a layer on top of the SAP HANA database. The HDI includes an SQL-based API that is accessible by means of standard SAP HANA SQL connection data. HDI clients use the HDI SQL API to manage containers and their content. Examples of HDI clients include the following: the HDI command-line client and the development environment.

The HDI API is based on a combination of SQL and database procedures. For example, the system-wide container-management API contains procedures for creating and dropping HDI containers. Each HDI container has a container API consisting of container-specific procedures for uploading, listing, and retrieving design-time objects \(write, read, list\); for deploying uploaded design-time objects \(make\); and for granting or revoking access to \(or from\) the container’s schemas and API \(grant, revoke\).

HDI containers can be grouped into container groups, where a corresponding group-level management API restricts the management operations \(for example, create, drop, configure, etc.\) to the set of HDI containers that are assigned to the specific HDI container group.

The following SQL APIs are provided to help you manage and work with HDI:

**SQL APIs for HDI**


<table>
<tr>
<th valign="top">

HDI SQL API



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

HDI administration API



</td>
<td valign="top">

Used mainly for managing container groups and the administrative access to them. Use of the HDI administration API requires the privileges of an HDI administrator.

> ### Note:  
> SYSTEM user privileges are required to create the first HDI administrator, who can then create other HDI administrators, if required. After creation of the first HDI administrator, the SYSTEM user can be deactivated.



</td>
</tr>
<tr>
<td valign="top">

HDI container group administration API



</td>
<td valign="top">

Used for managing a set of containers inside a container group and the administrative access to them. To use this API, a user needs to be granted the privileges of an HDI container group administrator by an HDI administrator.



</td>
</tr>
<tr>
<td valign="top">

HDI container administration API



</td>
<td valign="top">

Used for configuring a container and controlling the access to it. To use this API, a user needs to be granted the privileges of an HDI container administrator by an HDI container group administrator.



</td>
</tr>
<tr>
<td valign="top">

HDI container content development API:



</td>
<td valign="top">

Used for enabling applications to deploy or undeploy HDI artifacts within a container and manage access to the containers. To use this API, a user must be granted the privileges of an HDI container content developer by an HDI container administrator.

> ### Note:  
> The HDI container content development API is not described in this HDI administration section.



</td>
</tr>
</table>



<a name="loio035dbbe23ac14242b1f7d724dd102825__section_s3f_x2b_31b"/>

## Parameters of HDI API Procedures

HDI APIs usually expect a number of input and output parameters, where output parameters are always being the last parameters to be passed. Most of the HDI APIs return the following information as output parameters:

-   A return code

-   A request ID

-   A messages table




<a name="loio035dbbe23ac14242b1f7d724dd102825__section_r14_y2b_31b"/>

## Table Types

HDI's predefined table types can be found in the `_SYS_DI` schema, and are identified by the prefix "`TT_`. The privileges required for access to these table types are granted to a user by means of the grant APIs available to the HDI administrator, the HDI container-group administrator, or the HDI container administrator. To pass a parameter to an HDI API that expects an HDI table type, a temporary table of that type must be created before calling the API procedure. This temporary table must then be filled with the data that the API expects. For example:

> ### Sample Code:  
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #CONFIG_PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
> INSERT INTO #CONFIG_PARAMETERS (KEY, VALUE) VALUES ('make.max_parallel_jobs', '8'); 
> CALL C#DI.CONFIGURE_CONTAINER_PARAMETERS(#CONFIG_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?); 
> DROP TABLE #CONFIG_PARAMETERS; 
> ```



<a name="loio035dbbe23ac14242b1f7d724dd102825__section_sy1_z2b_31b"/>

## Predefined Parameter Tables

HDI's predefined tables are located in the `_SYS_DI` schema and are identified by the prefix "`T_`". The privileges required to access these tables are granted to a user by means of the grant APIs available to the HDI administrator, the HDI container-group administrator, or the HDI container administrator. The predefined tables provide tables with frequently needed default content. For example, when no special parameters need to be given to an HDI API, the `_SYS_DI.T_NO_PARAMETERS` table can be used.

> ### Sample Code:  
> ```sql
> CALL C#DI.CONFIGURE_CONTAINER_PARAMETERS(_SYS_DI.T_NO_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> ```



<a name="loio035dbbe23ac14242b1f7d724dd102825__section_grb_1fb_31b"/>

## Result Sets

The SAP HANA DI SQL API calls usually return the following result sets;

1.  A result set that contains a result code \(for example, 0 or 1\) and a request ID \(a unique ID for the API call\).

2.  A result set that includes a table of messages containing information about the execution of the HDI call.




<a name="loio035dbbe23ac14242b1f7d724dd102825__section_nsr_1fb_31b"/>

## Return Codes

The return code indicates if the API call was successful, or if there were problems during the execution of the call. The meaning of the possible return codes is described in the following table:

**SQL API Return Codes for HDI**


<table>
<tr>
<th valign="top">

Return Code



</th>
<th valign="top">

Meaning



</th>
<th valign="top">

Details



</th>
</tr>
<tr>
<td valign="top">

 ***0*** 



</td>
<td valign="top">

Success



</td>
<td valign="top">

The call was successful, and the messages did not report any warnings or errors



</td>
</tr>
<tr>
<td valign="top">

 ***1*** 



</td>
<td valign="top">

Warning



</td>
<td valign="top">

The messages contain warnings, but no errors.



</td>
</tr>
<tr>
<td valign="top">

 ***\-1*** 



</td>
<td valign="top">

Error



</td>
<td valign="top">

The messages contain errors.



</td>
</tr>
<tr>
<td valign="top">

 ***\-2*** 



</td>
<td valign="top">

Fatal Error



</td>
<td valign="top">

No messages could be logged. This indicates a problem with the database.



</td>
</tr>
</table>



<a name="loio035dbbe23ac14242b1f7d724dd102825__section_yff_bfb_31b"/>

## Request ID

The request ID is a unique ID generated for each API call. This ID is always the same for messages that originate from the same API call. It can, for example, be used by a container administrator to query the messages that were produced by a certain API call.



<a name="loio035dbbe23ac14242b1f7d724dd102825__section_vjs_bfb_31b"/>

## Messages

Most APIs return a table of messages with information about the execution of the HDI call. The message, content, and format is explained in the following table:

**SQL API Message Tables for HDI**


<table>
<tr>
<th valign="top">

Message Table



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

REQUEST\_ID



</td>
<td valign="top">

The unique ID of the API call that produced this message. This ID is always the same for messages that originate from the same API call.



</td>
</tr>
<tr>
<td valign="top">

ROW\_ID



</td>
<td valign="top">

An increasing number representing the line number of the message log.



</td>
</tr>
<tr>
<td valign="top">

LEVEL



</td>
<td valign="top">

The indentation level of the message \(used for better visual representation\).



</td>
</tr>
<tr>
<td valign="top">

TYPE



</td>
<td valign="top">

The type of message returned; the following list describes the possible message types:

-   SUMMARY

    A summary of the API call

-   HDI:

    The message from HDI

-   PLUGIN:

    The message from a plug-in




</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_ID



</td>
<td valign="top">

The ID of the library \(for messages from a plug-in\)



</td>
</tr>
<tr>
<td valign="top">

PLUGIN\_ID



</td>
<td valign="top">

The ID of the plug-in \(for messages from a plug-in\)



</td>
</tr>
<tr>
<td valign="top">

PATH



</td>
<td valign="top">

The path to the artifact that is being processed



</td>
</tr>
<tr>
<td valign="top">

SEVERITY



</td>
<td valign="top">

The severity of the message, for example: INFO, WARNING, ERROR, ...



</td>
</tr>
<tr>
<td valign="top">

MESSAGE\_CODE



</td>
<td valign="top">

A unique code corresponding to the MESSAGE field



</td>
</tr>
<tr>
<td valign="top">

MESSAGE



</td>
<td valign="top">

The message text



</td>
</tr>
<tr>
<td valign="top">

LOCATION



</td>
<td valign="top">

The Position \(for example, "line:column"\) within the artifact that the message refers to



</td>
</tr>
<tr>
<td valign="top">

LOCATION\_PATH



</td>
<td valign="top">

The XPath expression within the artifact that the message refers to



</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP\_UTC



</td>
<td valign="top">

The time stamp indicating when the message was created



</td>
</tr>
</table>

**Related Information**  


[SAP HANA Deployment Infrastructure in the Cloud](sap-hana-deployment-infrastructure-in-the-cloud-3ef0ee9.md "Understand the benefits of using the SAP HANA Deployment Infrastructure (HDI).")

