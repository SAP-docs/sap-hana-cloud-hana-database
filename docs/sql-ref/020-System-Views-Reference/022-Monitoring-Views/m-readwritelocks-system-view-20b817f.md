<!-- loio20b817fb751910149d859e59cc149cc1 -->

# M\_READWRITELOCKS System View

Provides read and write lock statistics.



<a name="loio20b817fb751910149d859e59cc149cc1___m__r_e_a_d_w_r_i_t_e_l_o_c_k_s_1struct_M_READWRITELOCKS"/>

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

OWNER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the context ID of the owner context \(for exclusive/intent locks\).

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_LOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of exclusive lock calls.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocking exclusive lock calls.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_CAS\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the collision count on atomic operations on exclusive locks.

</td>
</tr>
<tr>
<td valign="top">

EXCLUSIVE\_COLLISION\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the collision rate on exclusive locks percentage.

</td>
</tr>
<tr>
<td valign="top">

LAST\_EXCLUSIVE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time of blocking exclusive lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_EXCLUSIVE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of blocking exclusive lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_EXCLUSIVE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of blocking exclusive lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_EXCLUSIVE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of blocking exclusive lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_EXCLUSIVE\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of blocking exclusive lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

INTENT\_LOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of intent lock calls.

</td>
</tr>
<tr>
<td valign="top">

INTENT\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocking intent lock calls.

</td>
</tr>
<tr>
<td valign="top">

INTENT\_CAS\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the collision count on atomic operation on intent lock.

</td>
</tr>
<tr>
<td valign="top">

INTENT\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of timed out intent lock calls.

</td>
</tr>
<tr>
<td valign="top">

INTENT\_COLLISION\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the collision rate on intent locks percentage.

</td>
</tr>
<tr>
<td valign="top">

LAST\_INTENT\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time of blocking intent lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_INTENT\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of blocking intent lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_INTENT\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of blocking intent lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_INTENT\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of blocking intent lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_INTENT\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of blocking intent lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SHARED\_LOCK\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of shared lock calls.

</td>
</tr>
<tr>
<td valign="top">

SHARED\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of blocking shared lock calls.

</td>
</tr>
<tr>
<td valign="top">

SHARED\_CAS\_COLLISION\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the collision count on atomic operation on shared lock.

</td>
</tr>
<tr>
<td valign="top">

SHARED\_TIMEOUT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of timed out shared lock calls.

</td>
</tr>
<tr>
<td valign="top">

SHARED\_COLLISION\_RATE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the collision rate on shared lock percentage.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SHARED\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last time of blocking shared lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MAX\_SHARED\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum time of blocking shared lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

MIN\_SHARED\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the minimum time of blocking shared lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

SUM\_SHARED\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total time of blocking shared lock calls in microseconds.

</td>
</tr>
<tr>
<td valign="top">

AVG\_SHARED\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the average time of blocking shared lock calls in microseconds.

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

Displays the global collision rate percentage.

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

Displays the number of read and write lock creation \(for shared statistics only\).

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

Displays the number of read/write lock destructions \(for shared statistics only\).

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



<a name="loio20b817fb751910149d859e59cc149cc1___m__r_e_a_d_w_r_i_t_e_l_o_c_k_s_1fulldesc_M_READWRITELOCKS"/>

## Additional Information

This view contains information about single, or groups, of reader and writer lock objects. It does not contain information about all reader and writer lock. Information like LOCK\_COUNT, WAIT\_COUNT, and WAIT\_TIMES can be used to analyze performance bottlenecks.

This view has a resettable counterpart; you can see the values since the last reset in the M\_READWRITELOCKS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_READWRITELOCKS_RESET;`.

**Related Information**  


[M\_READWRITELOCKS\_RESET System View](m-readwritelocks-reset-system-view-20b841b.md "Provides read/write lock statistics since the last reset.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

[Manage Read-Write and Read-Only Access to a Remote Source](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/31a8a5dcd24b47e0a1c3e21f2427cb6f.html "The DML mode property specifies whether read-write or read-only access to the remote source is allowed. The DML mode, however, cannot override the restrictions of a remote source itself. For example, Amazon Athena and Google BigQuery remote sources are read-only and only the DML mode readonly is allowed.") :arrow_upper_right:

