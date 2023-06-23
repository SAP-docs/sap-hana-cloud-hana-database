<!-- loio66b63e6cd0c64d5bb5edef38a56465a9 -->

# M\_REMOTE\_SOURCE\_STATISTICS System View

Returns the remote source operational statistics for monitoring data provisioning components.



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

SUBSCRIPTION\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the subscription schema name.



</td>
</tr>
<tr>
<td valign="top">

SUBSCRIPTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the subscription name.



</td>
</tr>
<tr>
<td valign="top">

COLLECT\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the collection time.



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

Displays the name of the statistic.



</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_VALUE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the statistic value.



</td>
</tr>
</table>

**Related Information**  


[M\_REMOTE\_SOURCE\_LATENCY\_HISTORY System View](m-remote-source-latency-history-system-view-b36a777.md "")

[M\_REMOTE\_SOURCE\_LATENCY\_STATUS System View](m-remote-source-latency-status-system-view-322a772.md "Provides remote source latency status information.")

[M\_REMOTE\_SOURCES System View](m-remote-sources-system-view-4f6ae16.md "Provides remote source information.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:

[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

