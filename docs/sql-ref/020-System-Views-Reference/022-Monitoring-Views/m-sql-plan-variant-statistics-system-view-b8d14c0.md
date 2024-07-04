<!-- loiob8d14c08d3574a0ea6eccc3af30a5e65 -->

# M\_SQL\_PLAN\_VARIANT\_STATISTICS System View

Provides statistics for Plan Variant, a method that enables the caching of multiple plans \(variant plans\) for each parameterized query.




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

VARCHAR\(64\)

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

VOLUMN\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume id.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last connection ID that executed the plan.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the logical plan id used in the SQL plan cache.

</td>
</tr>
<tr>
<td valign="top">

PLAN\_VARIANT\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the logical plan variant id used in plan variant cache.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_STRING

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the statement string.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">

Displays the MD5 hash value for the STATEMENT\_STRING column.

</td>
</tr>
<tr>
<td valign="top">

VARIANT\_FILTERS

</td>
<td valign="top">

VARCHAR\(5000\)

</td>
<td valign="top">

Displays the list of variant filters.

</td>
</tr>
<tr>
<td valign="top">

PREPARATION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of plan preparations

</td>
</tr>
<tr>
<td valign="top">

LAST\_PREPARATION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last preparation timestamp.

</td>
</tr>
<tr>
<td valign="top">

LAST\_PREPARATION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the tracked actual memory. consumption of last preparation

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time of the plan preparation in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of the plan preparation in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of the plan preparation in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_PREPARATION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the plan preparation in microseconds.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXECUTION\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last execution timestamp.

</td>
</tr>
<tr>
<td valign="top">

EXECUTION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated count of the plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time of the plan execution, including the communication time with clients, in microseconds

</td>
</tr>
<tr>
<td valign="top">

AVG\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of the plan execution, including the communication time with clients, in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of the plan execution, including the communication time with clients, in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CURSOR\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the plan execution, including the communication time with clients, in microseconds

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time of the plan executions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of the plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of the plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of the plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time establishing result sets in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time that the cursor is open in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time for cursor open in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_OPEN\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time for cursor open in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time for transferring rows in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time for cursor fetch in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time for cursor fetch in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_FETCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time for cursor fetch in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of time for result set cleanup in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time for cursor close in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time for cursor close in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_CLOSE\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time for cursor close in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total size of tracked actual memory consumption.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average size of tracked actual memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum size of tracked actual memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum size of tracked actual memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total amount of tracked CPU time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average amount of tracked CPU time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum amount of tracked CPU time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXECUTION\_CPU\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum amount of tracked CPU time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_RESULT\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated number of records during plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated lock wait count for the plan.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAIT\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated lock wait duration in microseconds for the plan.

</td>
</tr>
<tr>
<td valign="top">

AVG\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average count of called threads used during plan execution.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum count of called threads used during plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_CALLED\_THREAD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total batch count per one execution for cached DML plans.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average count of service network requests during plan execution.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum count of service network requests during plan execution.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total count of called threads used during plan execution.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average time of the service network requests during plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the maximum time of the service network requests during plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_DURATION

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the maximum time of the service network requests during plan execution in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

REAL

</td>
<td valign="top">

Displays the average data amount of service network requests during plan execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum amount of service network requests during plan execution in bytes.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_SERVICE\_NETWORK\_REQUEST\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total amount of service network requests during plan execution in bytes.

</td>
</tr>
</table>

