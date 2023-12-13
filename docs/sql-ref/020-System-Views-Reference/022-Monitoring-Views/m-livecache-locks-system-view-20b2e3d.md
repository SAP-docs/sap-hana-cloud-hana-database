<!-- loio20b2e3d575191014a7c893bbb84c15fa -->

# M\_LIVECACHE\_LOCKS System View

Detailed information on the Object Management System \(OMS\) locks.



<a name="loio20b2e3d575191014a7c893bbb84c15fa___m__l_i_v_e_c_a_c_h_e__l_o_c_k_s_1struct_M_LIVECACHE_LOCKS"/>

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

ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the ID of the lock: OID, container ID, or schema ID, depending on the lock class.

</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the corresponding container.

</td>
</tr>
<tr>
<td valign="top">

CLASS

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the class that the lock belongs to.

</td>
</tr>
<tr>
<td valign="top">

GRANTED\_MODE

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the mode that the lock has granted to some request\(s\).

</td>
</tr>
<tr>
<td valign="top">

MODE

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the mode that the request is requesting on the lock: Free, IntendShare, IntendExclusive, Share, ShareIntendExclusive, or Exclusive.

</td>
</tr>
<tr>
<td valign="top">

TYPE

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays when the lock can be removed, either at transaction-end \(EOT\) or if not visible anymore \(Consistent\).

</td>
</tr>
<tr>
<td valign="top">

STATE

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays the state of the lock request.

</td>
</tr>
<tr>
<td valign="top">

TID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the transaction ID belonging to this lock request.

</td>
</tr>
<tr>
<td valign="top">

TIMEOUT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays remaining timeout, if a timeout is specified.

</td>
</tr>
</table>



<a name="loio20b2e3d575191014a7c893bbb84c15fa___m__l_i_v_e_c_a_c_h_e__l_o_c_k_s_1fulldesc_M_LIVECACHE_LOCKS"/>

## Additional Information

The liveCache uses its own lock-manager for object locks, container locks, and schema locks. This view shows information about all the locks, which are currently kept in this lock manager.

Exclusive locks on objects are in most cases not managed by this lock manager, but the necessary lock-information is stored in the respective object header.

This view can only be used if liveCache is enabled.

**Related Information**  


[M\_LIVECACHE\_LOCK\_STATISTICS\_RESET System View](m-livecache-lock-statistics-reset-system-view-20b2be6.md "LiveCache lock statistics (since last reset).")

[M\_LIVECACHE\_LOCK\_STATISTICS System View](m-livecache-lock-statistics-system-view-20b287a.md "Provides accumulated LiveCache lock statistics.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

