<!-- loiob36a777e1d434dfe99b4f7ed6d9eb3b8 -->

# M\_REMOTE\_SOURCE\_LATENCY\_HISTORY System View



## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name.

</td>
</tr>
<tr>
<td valign="top">

LATENCY\_TICKET\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the latency ticket name.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the start time.

</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the service name.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the component.

</td>
</tr>
<tr>
<td valign="top">

SUB\_COMPONENT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the subcomponent.

</td>
</tr>
<tr>
<td valign="top">

STATISTIC\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the statistic name.

</td>
</tr>
<tr>
<td valign="top">

STATISTIC\_VALUE

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the statistic value.

</td>
</tr>
</table>

**Related Information**  


[M\_REMOTE\_SOURCE\_LATENCY\_STATUS System View](m-remote-source-latency-status-system-view-322a772.md "Provides remote source latency status information.")

[M\_REMOTE\_SOURCES System View](m-remote-sources-system-view-4f6ae16.md "Provides remote source information.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:

[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

