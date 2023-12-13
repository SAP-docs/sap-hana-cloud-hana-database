<!-- loio21178f7134d040e59f24b58ebca3c0c2 -->

# M\_ADMISSION\_CONTROL\_EVENTS System View

Displays information about significant events.



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

EVENT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the event.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of event.

</td>
</tr>
<tr>
<td valign="top">

EVENT\_REASON

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the reason for the event.

</td>
</tr>
<tr>
<td valign="top">

QUEUE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the queue wait time, in microseconds.

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

Displays the session connection ID.

</td>
</tr>
<tr>
<td valign="top">

MESSAGE\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the request type.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the prepared statement ID.

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_HASH

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the unique identifier for an SQL string.

</td>
</tr>
<tr>
<td valign="top">

CPU\_USAGE\_RATIO

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the measured value of the CPU usage.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_RATIO

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the measured memory size, in bytes, as a percentage of the global allocation limit.

</td>
</tr>
<tr>
<td valign="top">

WORKLOAD\_CLASS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the effective workload class

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

**Related Information**  


[M\_ADMISSION\_CONTROL\_QUEUES System View](m-admission-control-queues-system-view-cc0fbe8.md "Provides detailed information regarding queued session requests by Session-Wise Admission Control.")

[M\_ADMISSION\_CONTROL\_STATISTICS System View](m-admission-control-statistics-system-view-69c4547.md "Provides the overall statistics values of the Session-Wise Admission Control feature.")

