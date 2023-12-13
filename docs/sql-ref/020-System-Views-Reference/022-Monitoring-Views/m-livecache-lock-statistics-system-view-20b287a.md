<!-- loio20b287a27519101486ee8aa918749af3 -->

# M\_LIVECACHE\_LOCK\_STATISTICS System View

Provides accumulated LiveCache lock statistics.



<a name="loio20b287a27519101486ee8aa918749af3___m__l_i_v_e_c_a_c_h_e__l_o_c_k__s_t_a_t_i_s_t_i_c_s_1struct_M_LIVECACHE_LOCK_STATISTICS"/>

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

CONTAINER\_EXCLUSIVE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on containers.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_SHARED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shared lock requests on containers.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock collisions on containers.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock timeouts on containers.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_EXCLUSIVE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on schemas.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_SHARED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shared lock requests on schemas.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock collisions on schemas.

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock timeouts on schemas.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_EXCLUSIVE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock requests on objects

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SHARED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shared lock requests on objects.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of lock collisions on objects.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of timeouts on objects.

</td>
</tr>
<tr>
<td valign="top">

COMMITTED\_REQUESTS\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of committed requests.

</td>
</tr>
</table>



<a name="loio20b287a27519101486ee8aa918749af3___m__l_i_v_e_c_a_c_h_e__l_o_c_k__s_t_a_t_i_s_t_i_c_s_1fulldesc_M_LIVECACHE_LOCK_STATISTICS"/>

## Additional Information

This view is only usable if liveCache is enabled.

The liveCache uses its own lock-manager for object locks, container locks, and schema locks. This view shows the accumulated statistics of the lock requests to this lock-manager, which have been executed since restart.

This view has a resettable counterpart; you can see the values since the last reset in the M\_LIVECACHE\_LOCK\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_LIVECACHE_LOCK_STATISTICS_RESET;`.

**Related Information**  


[M\_LIVECACHE\_LOCK\_STATISTICS\_RESET System View](m-livecache-lock-statistics-reset-system-view-20b2be6.md "LiveCache lock statistics (since last reset).")

[M\_LIVECACHE\_LOCKS System View](m-livecache-locks-system-view-20b2e3d.md "Detailed information on the Object Management System (OMS) locks.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

