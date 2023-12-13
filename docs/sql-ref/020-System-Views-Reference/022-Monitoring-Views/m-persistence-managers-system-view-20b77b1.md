<!-- loio20b77b1075191014a708b95dd1f25f54 -->

# M\_PERSISTENCE\_MANAGERS System View

Provides persistence manager statistics.



<a name="loio20b77b1075191014a708b95dd1f25f54___m__p_e_r_s_i_s_t_e_n_c_e__m_a_n_a_g_e_r_s_1struct_M_PERSISTENCE_MANAGERS"/>

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

Displays the persistence volume ID.

</td>
</tr>
<tr>
<td valign="top">

MAX\_TID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum known TID.

</td>
</tr>
<tr>
<td valign="top">

CCH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of normal consistent changes in terminated sessions.

</td>
</tr>
<tr>
<td valign="top">

MASS\_CCH\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of consistent changes for mass operations in terminated sessions.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time spent in normal consistent changes in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time spent in normal consistent changes in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time spent in normal consistent changes in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time spent in normal consistent changes in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time spent in normal consistent changes in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MASS\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time spent in consistent changes for mass operations in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_MASS\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time spent in consistent changes for mass operations in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_MASS\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time spent in consistent changes for mass operations in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_MASS\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time spent in consistent changes for mass operations in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_MASS\_CCH\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time spent in consistent changes for mass operations in terminated sessions in microseconds.

</td>
</tr>
<tr>
<td valign="top">

PREPARE\_COMMIT\_POS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the newest known log position of the prepare commit. This value is for the secondary node only.

</td>
</tr>
<tr>
<td valign="top">

primary node\_COMMIT\_POS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the newest known log position of the commit record on the transaction primary node from the point of view of this node.

</td>
</tr>
<tr>
<td valign="top">

INDOUBT\_WAITERS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of in-doubt waiters for the currently-running COMMIT. This value is for the primary node only.

</td>
</tr>
<tr>
<td valign="top">

INDOUBT\_RESTART\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of open in-doubt transactions before the restart. This value is for the primary node only.

</td>
</tr>
<tr>
<td valign="top">

INDOUBT\_ONLINE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of open in-doubt transactions since the last restart. This value is for the primary node only.

</td>
</tr>
<tr>
<td valign="top">

SAVEPOINT\_CONFIG\_FREQUENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the configured savepoint frequency in seconds.

</td>
</tr>
<tr>
<td valign="top">

SAVEPOINT\_ACTIVE\_FREQUENCY

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the currently active savepoint frequency in seconds.

</td>
</tr>
<tr>
<td valign="top">

CHECKSUM\_ALGORITHM

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the currently used checksum algorithm for the modified pages and log buffers.

</td>
</tr>
</table>



<a name="loio20b77b1075191014a708b95dd1f25f54___m__p_e_r_s_i_s_t_e_n_c_e__m_a_n_a_g_e_r_s_1fulldesc_M_PERSISTENCE_MANAGERS"/>

## Additional Information

Persistence manager is the module responsible for low-level operations on the persistent data structures. This view shows various statistics counters, which are used to measure the performance of those operations.

This view has a resettable counterpart; you can see the values since the last reset in the M\_PERSISTENCE\_MANAGERS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_PERSISTENCE_MANAGERS_RESET;`.

**Related Information**  


[M\_PERSISTENCE\_MANAGERS\_RESET System View](m-persistence-managers-reset-system-view-20b7a20.md "Provides persistence manager statistics since the last reset.")

[M\_GARBAGE\_COLLECTION\_STATISTICS System View](m-garbage-collection-statistics-system-view-20b04b8.md "Provides garbage collection and history manager statistics.")

