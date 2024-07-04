<!-- loio69c454794bd044f6a6552a0e2317196a -->

# M\_ADMISSION\_CONTROL\_STATISTICS System View

Provides the overall statistics values of the Session-Wise Admission Control feature.



<a name="loio69c454794bd044f6a6552a0e2317196a__section_pfr_rrv_xy"/>

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

TOTAL\_ADMIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated request admission count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_REJECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated request rejection count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_ENQUEUE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated request queued count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_DEQUEUE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated request dequeued count \(the executed request count\).

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the accumulated request dequeued count due to timeout \(the rejected request count\).

</td>
</tr>
<tr>
<td valign="top">

CURRENT\_QUEUE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current waiting request queued count.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CPU\_USAGE\_RATIO

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last measured value of the CPU usage, as a percentage of \(max\_concurrency / vcpus\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_CPU\_USAGE\_MEASURE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time at which the last CPU usage ratio was measured.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last measured memory size in GB.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_RATIO

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last measured memory size, as a percentage of the global allocation limit \(last\_memory\_size/memory\_allocation\_limit\).

</td>
</tr>
<tr>
<td valign="top">

LAST\_MEMORY\_MEASURE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time at which the last memory size was measured.

</td>
</tr>
<tr>
<td valign="top">

LAST\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last wait time of the request in the queue in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average wait time of the request in the queue in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum wait time of the request in the queue in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum wait time of the request in the queue in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total wait time of the request in the queue in microseconds.

</td>
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
</table>



<a name="loio69c454794bd044f6a6552a0e2317196a__section_yb3_tg2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_ADMISSION\_CONTROL\_EVENTS System View](m-admission-control-events-system-view-21178f7.md "Displays information about significant events.")

[M\_ADMISSION\_CONTROL\_QUEUES System View](m-admission-control-queues-system-view-cc0fbe8.md "Provides detailed information regarding queued session requests by Session-Wise Admission Control.")

