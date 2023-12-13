<!-- loio5c8f947a37444e4e81379cf94b363de7 -->

# M\_TASKS System View

Provides task monitoring information.



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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name used in the task.

</td>
</tr>
<tr>
<td valign="top">

TASK\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the task.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection identifier.

</td>
</tr>
<tr>
<td valign="top">

TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction identifier used for the task execution.

</td>
</tr>
<tr>
<td valign="top">

TASK\_EXECUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the unique identifier of the task execution.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_TASK\_EXECUTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the parent task identifier.

</td>
</tr>
<tr>
<td valign="top">

IS\_ASYNC

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not this is an asynchronous task: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PARAMETERS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the input parameters for the task.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_PARAMETERS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the input procedure parameters for the task.

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

Displays the start time of the task.

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

Displays the end time of the task.

</td>
</tr>
<tr>
<td valign="top">

DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the execution time of the task in microseconds.

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the status of the task: STARTING, RUNNING, FAILED, or COMPLETED.

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_OPERATION

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the operation of the task.

</td>
</tr>
<tr>
<td valign="top">

PROCESSED\_RECORDS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of processed records.

</td>
</tr>
<tr>
<td valign="top">

PARTITION\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of task partitions for a task execution. This value is 1 if there is no task partitioning.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_PROGRESS\_PERCENT

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the total task progress percentage.

</td>
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

APPLICATION\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the application user name.

</td>
</tr>
<tr>
<td valign="top">

HAS\_SIDE\_EFFECTS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the task produces side effect data: TRUE/FALSE.

</td>
</tr>
</table>

