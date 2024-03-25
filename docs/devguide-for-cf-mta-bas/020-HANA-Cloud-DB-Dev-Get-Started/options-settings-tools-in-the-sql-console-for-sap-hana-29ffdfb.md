<!-- loio29ffdfba2e0f43cd892734f66e490b3f -->

<link rel="stylesheet" type="text/css" href="../css/sap-icons.css"/>

# Options, Settings, & Tools in the SQL Console for SAP HANA

An overview of the information and options available in the SQL Console.



<a name="loio29ffdfba2e0f43cd892734f66e490b3f__section_cd3_krt_xzb"/>

## Overview

The information in this topic is divided into the following areas:

-   [SQL Statement Run Options](options-settings-tools-in-the-sql-console-for-sap-hana-29ffdfb.md#loio29ffdfba2e0f43cd892734f66e490b3f__section_ec5_grt_xzb)
-   [SQL File Options](options-settings-tools-in-the-sql-console-for-sap-hana-29ffdfb.md#loio29ffdfba2e0f43cd892734f66e490b3f__section_yh5_4rt_xzb)
-   [SQL Console Information and Connection Options](options-settings-tools-in-the-sql-console-for-sap-hana-29ffdfb.md#loio29ffdfba2e0f43cd892734f66e490b3f__section_rdf_frt_xzb)



<a name="loio29ffdfba2e0f43cd892734f66e490b3f__section_ec5_grt_xzb"/>

## SQL Statement Run Options

The SQL console for SAP HANA permits the following *Run* options:


<table>
<tr>
<th valign="top">

Run Menu Item

</th>
<th valign="top">

Keyboard Combination

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

*Run* 

</td>
<td valign="top">

[F8\] 

</td>
<td valign="top">

Runs all SQL statements

</td>
</tr>
<tr>
<td valign="top">

*Run Statement* 

</td>
<td valign="top">

[F9\] 

</td>
<td valign="top">

Runs individual SQL statements

</td>
</tr>
<tr>
<td valign="top">

*Run Line* 

</td>
<td valign="top">

[Ctrl\] + [F8\]  

</td>
<td valign="top">

Runs the contents of the currently selected line of SQL code

</td>
</tr>
<tr>
<td valign="top">

*Run with parameters* 

</td>
<td valign="top">

N/A

> ### Tip:  
> The run-with-parameters option is only available in the *Parameters* tab.



</td>
<td valign="top">

Runs the contents of the currently selected line of SQL code with the parameters provided

</td>
</tr>
</table>



<a name="loio29ffdfba2e0f43cd892734f66e490b3f__section_yh5_4rt_xzb"/>

## SQL File Options

The SQL console for SAP HANA permits the following *File* options:


<table>
<tr>
<th valign="top">

Run Menu Item

</th>
<th valign="top">

Result

</th>
</tr>
<tr>
<td valign="top">

:open_file_folder: 

</td>
<td valign="top">

Run the SQL statements that are stored in a file.

> ### Tip:  
> The name of the open file is displayed in the tab title, and the contents of the open file are displayed in the SQL console.



</td>
</tr>
<tr>
<td valign="top">

:floppy_disk: 

</td>
<td valign="top">

Manually save changes to the currently open SQL file.

> ### Tip:  
> The SQL console periodically saves the contents of the SQL console to the currently open file, whose name is displayed in the tab title.



</td>
</tr>
<tr>
<td valign="top">

![](images/BAS_icon_SQLsaveToFile_f441257.svg) \(*Save SQL to file*\)

</td>
<td valign="top">

Save the code that is currently displayed in the SQL console to a file in a local file system.

> ### Tip:  
> The name of the specified \(open/saved\) file is displayed in the tab title.



</td>
</tr>
</table>



<a name="loio29ffdfba2e0f43cd892734f66e490b3f__section_rdf_frt_xzb"/>

## SQL Console Information & Connection Options

The following table lists the information displayed in the SQL Console for SAP HANA and the options and tools provided:


<table>
<tr>
<th valign="top">

UI Text or Tool

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

*FlightReservation-hdidb-ws-ab1cd* 

</td>
<td valign="top">

The name of the database instance that the SQL console for SAP HANA is currently connected to. By default, this name comprises the following elements:

<code><i class="varname">&lt;App Project Name&gt;</i>-<i class="varname">&lt;MTA resource name&gt;</i>-ws-<i class="varname">&lt;Workspace-ID&gt;</i></code>

</td>
</tr>
<tr>
<td valign="top">

*\(ABC\)* 

</td>
<td valign="top">

The name \(in brackets\) of the XS advanced space to which the database instance is assigned.

</td>
</tr>
<tr>
<td valign="top">

<span class="FPA-icons-V3"></span> \(Instance Information\) 

</td>
<td valign="top">

Display details of the currently connected database instance, for example, the database type \(SAP HANA, SAP HANA Cloud, or HDI container\) and the user name \(database user or the HDI container's run-time user\).

</td>
</tr>
<tr>
<td valign="top">

<span class="SAP-icons-watt"></span> \(Connect\) 

</td>
<td valign="top">

Connect the SQL console for SAP HANA to the currently selected database instance.

While the SQL console for SAP HANA is connected to a database, the connect icon is inactive. When you hover the mouse cursor over the connect icon, <span style="color:#BB0000;"><span class="FPA-icons-V3"></span></span> indicates that another connection is not currently possible.

</td>
</tr>
<tr>
<td valign="top">

<span class="SAP-icons-watt"></span> \(Disconnect\) 

</td>
<td valign="top">

Disconnect the SQL console for SAP HANA from the currently selected database instance.

While the SQL console for SAP HANA remains connected to the selected database instance, the disconnect icon is active.

</td>
</tr>
<tr>
<td valign="top">

<span class="FPA-icons-V3"></span> \(Different database\) 

</td>
<td valign="top">

Connect the SQL console to a different database instance. For more information about how to perform this action, see step *Related Information* below.

</td>
</tr>
<tr>
<td valign="top">

<span class="SAP-icons-V5"></span> \(View connection settings\)

</td>
<td valign="top">

Enable or disable auto-commit for any database changes required by SQL statements running in the SQL console

</td>
</tr>
<tr>
<td valign="top">

<span class="BusinessSuiteInAppSymbols-V2"></span> \(Show/Hide Statement Help\) 

</td>
<td valign="top">

Display \(or hide\) a side panel in the SQL console, which shows syntax suggestions for SQL statements and provides access to information about metadata SQL objects.

</td>
</tr>
</table>

**Related Information**  


[Use the SQL Console for SAP HANA to Query the Database](use-the-sql-console-for-sap-hana-to-query-the-database-7ffe3cc.md "Learn how to use the SQL console for SAP HANA to run queries on SAP HANA databases.")

