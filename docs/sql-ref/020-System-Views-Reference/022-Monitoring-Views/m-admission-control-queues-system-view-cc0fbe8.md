<!-- loiocc0fbe8198134882a082a8a2507c50e8 -->

# M\_ADMISSION\_CONTROL\_QUEUES System View

Provides detailed information regarding queued session requests by Session-Wise Admission Control.



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

MESSAGE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the request ID of the client packet.

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

STATEMENT\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the statement type \(for example, DDL or DML\).

</td>
</tr>
<tr>
<td valign="top">

ENQUEUE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the request queue time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the estimated time, in microseconds, when the request should be timed-out.

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



<a name="loiocc0fbe8198134882a082a8a2507c50e8__section_ov3_xf2_qbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_ADMISSION\_CONTROL\_EVENTS System View](m-admission-control-events-system-view-21178f7.md "Displays information about significant events.")

[M\_ADMISSION\_CONTROL\_STATISTICS System View](m-admission-control-statistics-system-view-69c4547.md "Provides the overall statistics values of the Session-Wise Admission Control feature.")

