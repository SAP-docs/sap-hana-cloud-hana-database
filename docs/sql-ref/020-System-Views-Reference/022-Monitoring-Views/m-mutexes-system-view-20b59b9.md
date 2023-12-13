<!-- loio20b59b9975191014b1beb879400bb0c9 -->

# M\_MUTEXES System View

Provides information about single mutex \(mutual exclusion\) objects or groups of mutex objects.



<a name="loio20b59b9975191014b1beb879400bb0c9___m__m_u_t_e_x_e_s_1struct_M_MUTEXES"/>

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

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the statistics object name.

</td>
</tr>
<tr>
<td valign="top">

STATISTICS\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the statistics object unique ID.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock calls.

</td>
</tr>
<tr>
<td valign="top">

WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocking lock calls.

</td>
</tr>
<tr>
<td valign="top">

SPURIOUS\_WAKEUP\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of spurious wakeups \(collisions on futex\).

</td>
</tr>
<tr>
<td valign="top">

COLLISION\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the collision rate percentage.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the context ID of the owner context.

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

Displays the last time of the blocking lock calls in microseconds.

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

Displays the maximum time of the blocking lock calls in microseconds.

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

Displays the minimum time of the blocking lock calls in microseconds.

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

Displays the total time of the blocking lock calls in microseconds.

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

Displays the average time of the blocking lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of mutex creations \(for shared statistics only\).

</td>
</tr>
<tr>
<td valign="top">

DESTROY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of mutex destructions \(for shared statistics only\).

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
</table>



<a name="loio20b59b9975191014b1beb879400bb0c9___m__m_u_t_e_x_e_s_1fulldesc_M_MUTEXES"/>

## Additional Information

M\_MUTEXES does not contain information about all mutex objects. Information like LOCK\_COUNT, WAIT\_COUNT and WAIT\_TIMES can be used to analyze performance bottlenecks. You can find possible deadlocks using the OWNER\_ID column.

This view has a resettable counterpart; you can see the values since the last reset in the M\_MUTEXES\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_MUTEXES_RESET;`.

**Related Information**  


[M\_MUTEXES\_RESET System View](m-mutexes-reset-system-view-20b5bf1.md "Provides mutex statistics since the last reset.")

[M\_LOAD\_HISTORY\_SERVICE System View](m-load-history-service-system-view-261022b.md "Lists service-specific load history KPIs.")

