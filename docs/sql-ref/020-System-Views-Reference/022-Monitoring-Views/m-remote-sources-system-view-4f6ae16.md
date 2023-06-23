<!-- loio4f6ae165f5354f47809856693db2da0a -->

# M\_REMOTE\_SOURCES System View

Provides remote source information.



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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name.



</td>
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

LAST\_REFRESH\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last successful completion timestamp of the refresh operation.



</td>
</tr>
<tr>
<td valign="top">

REFRESH\_START\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the timestamp of when the refresh operation was executed.



</td>
</tr>
<tr>
<td valign="top">

REFRESH\_STATUS



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the refresh operation status: STARTED, COMPLETED,RUNNING \(GET OBJECTS\), RUNNING \(GET OBJECT DETAILS\),FAILED, CANCELLED, or CLEARED.



</td>
</tr>
<tr>
<td valign="top">

REFRESH\_ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR\(2000\)



</td>
<td valign="top">

Displays the exception message that occurred during the refresh operation.



</td>
</tr>
</table>

**Related Information**  


[REMOTE\_SOURCES System View](../021-System-Views/remote-sources-system-view-20ccdd3.md "Provides information about remote sources.")

[M\_REMOTE\_SOURCE\_LATENCY\_HISTORY System View](m-remote-source-latency-history-system-view-b36a777.md "")

[M\_REMOTE\_SOURCE\_LATENCY\_STATUS System View](m-remote-source-latency-status-system-view-322a772.md "Provides remote source latency status information.")

[M\_REMOTE\_SOURCE\_STATISTICS System View](m-remote-source-statistics-system-view-66b63e6.md "Returns the remote source operational statistics for monitoring data provisioning components.")

[Creating Remote Sources (Smart Data Access)](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/e8274a1cf62b4aa5b58f261bc904a4af.html "Create a smart data access remote source using SQL syntax or the SAP HANA database explorer.") :arrow_upper_right:

[Customizing Remote Source Behavior](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/0a97fa4dbb3649ccaab43bcaee95345f.html "The supported behaviors of an SAP HANA smart data access remote source may not be the same as those of the local SAP HANA Cloud, SAP HANA database. Smart data access provides a set of customizable properties, capabilities, functions, and data types to help address these differences.") :arrow_upper_right:

[CREATE REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-remote-source-statement-access-control-20d4834.md "Defines an external data source that can connect to the SAP HANA database.")

[ALTER REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-remote-source-statement-access-control-f423eb4.md "Modifies the configuration of an external data source that is connected to an SAP HANA database.")

[DROP REMOTE SOURCE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-remote-source-statement-access-control-20d7332.md "Removes an existing remote source.")

