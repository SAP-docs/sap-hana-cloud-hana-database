<!-- loiod520e47575b6480fbbc10c7728d5ac05 -->

# WORKLOAD\_CLASSES System View

Provides information about available workload classes.



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

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the workload class.

</td>
</tr>
<tr>
<td valign="top">

PRIORITY

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the priority. Zero is the lowest while nine is the highest and multiple workload classes can have the same priority. Five is the default.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_MEMORY\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum memory allocation per statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_MEMORY\_LIMIT\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the unit of measure \(gigabyte or percent\) for the statement memory limit.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_THREAD\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum number of parallel threads per statement.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_THREAD\_LIMIT\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the unit of measure \(counter or percent\) for the statement thread limit.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_MEMORY\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the aggregated memory limit, in gigabytes or percent, that applies to all statements currently being executed within the workload class.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_MEMORY\_LIMIT\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the unit of measure \(gigabyte or percent\) for the total statement memory limit.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_THREAD\_LIMIT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the aggregated thread limit that applies to all statements currently being executed within the workload class.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_STATEMENT\_THREAD\_LIMIT\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the unit of measure \(counter or percent\) for the total statement thread limit.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_TIMEOUT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the timeout, in seconds, of the statement execution.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_TRANSACTION\_LIFETIME

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the lifetime, in minutes, of long-running, uncommitted write transactions.

</td>
</tr>
<tr>
<td valign="top">

IDLE\_CURSOR\_LIFETIME

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the lifetime, in minutes, of long-lived cursors.

</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_REJECT\_CPU\_THRESHOLD

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the threshold value got rejection based on CPU consumption.

</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_REJECT\_MEMORY\_THRESHOLD

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the threshold value got rejection based on memory consumption.

</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_QUEUE\_CPU\_THRESHOLD

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the threshold value to queue based on CPU consumption.

</td>
</tr>
<tr>
<td valign="top">

ADMISSION\_CONTROL\_QUEUE\_MEMORY\_THRESHOLD

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the threshold value to queue based on memory consumption.

</td>
</tr>
<tr>
<td valign="top">

IS\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the workload class is enabled: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the parent workload class.

</td>
</tr>
</table>



<a name="loiod520e47575b6480fbbc10c7728d5ac05__section_kzj_xb1_fzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/create-workload-class-statement-workload-management-dc417c3.md "Defines workload classes.")

[ALTER WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-workload-class-statement-workload-management-d4b4659.md "Changes workload classes.")

[DROP WORKLOAD CLASS Statement \(Workload Management\)](../../010-SQL-Reference/012-SQL-Statements/drop-workload-class-statement-workload-management-22f628b.md "Removes workload classes.")

[M\_WORKLOAD System View](../022-Monitoring-Views/m-workload-system-view-20cb5a7.md "Provides information about the database workload collected every minute.")

[Managing Workload with Workload Classes](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/5066181717df4110931271d1efd84cbc.html "You can manage workload in SAP HANA by creating workload classes and workload class mappings. Appropriate workload parameters are then dynamically applied to each client session.") :arrow_upper_right:

[Workload Classes and Other Workload Management Features](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/dafe347e32dc4884a7b2b37909dabf94.html "Here we give examples to show how the workload management features interact together.") :arrow_upper_right:

[WORKLOAD\_MAPPINGS System View](workload-mappings-system-view-89a0660.md "Provides information about available workload mappings.")

