<!-- loioea8874bfb6464b4cb302f304faa4982b -->

# M\_WORKLOAD\_CAPTURES System View

Provides information about workload captures.



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

CAPTURE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique ID of the captured workload.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the user-specified name of the captured workload.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR \(5000\)

</td>
<td valign="top">

Displays the user-specified description of the captured workload.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_VERSION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the version number of the structure format for the captured workloads or capturing workload.

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

Displays the start timestamp of the capture.

</td>
</tr>
<tr>
<td valign="top">

UTC\_START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the UTC start timestamp of the capture.

</td>
</tr>
<tr>
<td valign="top">

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the end timestamp of the captured workload

</td>
</tr>
<tr>
<td valign="top">

UTC\_END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the UTC end timestamp of the captured workload.

</td>
</tr>
<tr>
<td valign="top">

IS\_FILTER\_APPLIED

</td>
<td valign="top">

NVARCHAR \(5\)

</td>
<td valign="top">

Displays the flag that is set to FALSE if the user Displays any non-default value to any filter parameters.

</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_ID

</td>
<td valign="top">

NVARCHAR \(3\)

</td>
<td valign="top">

Displays the system ID in which the capture has been done.

</td>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the database name in which the capture has been done.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the status of the workload captures.

</td>
</tr>
<tr>
<td valign="top">

IS\_LOADED

</td>
<td valign="top">

NVARCHAR \(5\)

</td>
<td valign="top">

Displays the flag that is set to TRUE if the captured data is loaded into the database.

</td>
</tr>
<tr>
<td valign="top">

PROGRESS

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the current progress of the load.

</td>
</tr>
<tr>
<td valign="top">

LEVEL

</td>
<td valign="top">

NVARCHAR \(16\)

</td>
<td valign="top">

Displays the level of workload captures.

</td>
</tr>
<tr>
<td valign="top">

PARAMETERS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the applied parameter's key/value pairs.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_DURATION\_THRESHOLD

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the threshold value for the workloads to be captured.

</td>
</tr>
<tr>
<td valign="top">

FLUSH\_INTERVAL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the interval of flushing out the file output stream.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the file name of the captured workload.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_SESSION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of current or captured logical sessions.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_STATEMENT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of current or captured statements.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_FETCH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number current or captured fetch operations.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_COMMITTED\_TRANSACTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of current or captured committed transactions.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the size of the captured workload file.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_FAILED\_STATEMENT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of failed current or capture statements.

</td>
</tr>
<tr>
<td valign="top">

CAPTURE\_FAILED\_FETCH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of failed current or capture fetch operations.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code generated by the system during capturing.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR \(5000\)

</td>
<td valign="top">

Displays the error message generated by system during capturing.

</td>
</tr>
</table>

**Related Information**  


[CREATE WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md "Defines workload classes.")

[ALTER WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-workload-class-statement-workload-management-d4b4659.md "Changes workload classes.")

[ALTER WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-workload-mapping-statement-workload-management-81fc16b.md "Changes workload mappings.")

[CREATE WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-mapping-statement-workload-management-996978a.md "Defines workload mappings.")

[DROP WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-workload-class-statement-workload-management-22f628b.md "Removes workload classes.")

[DROP WORKLOAD MAPPING Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-workload-mapping-statement-workload-management-8d90e94.md "Drops a workload mapping.")

[Workload Management](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/30f2e9cb92aa4f358dda4ac58e062d83.html "The load on an SAP HANA system can be managed by selectively applying limitations and priorities to how resources are used. Settings can be applied globally or at the level of individual user sessions by using workload classes.") :arrow_upper_right:

