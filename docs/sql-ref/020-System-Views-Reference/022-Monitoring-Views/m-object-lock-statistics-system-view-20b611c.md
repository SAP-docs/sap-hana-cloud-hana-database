<!-- loio20b611c275191014aa0fe74fe3f2a8fa -->

# M\_OBJECT\_LOCK\_STATISTICS System View

Provides lock contention statistics, including lock wait count, wait time, and failed count, for each object.



<a name="loio20b611c275191014aa0fe74fe3f2a8fa___m__o_b_j_e_c_t__l_o_c_k__s_t_a_t_i_s_t_i_c_s_1struct_M_OBJECT_LOCK_STATISTICS"/>

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

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the object type: RECORD, TABLE, VIEW, SYNONYM, or SEQUENCE.

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

Displays the schema name that the object belongs to.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name.

</td>
</tr>
<tr>
<td valign="top">

PART\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the lock type: OBJECT/RECORD.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the lock wait count.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the lock wait time in microseconds.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_FAILED\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the RECORD type lock failed count.

</td>
</tr>
</table>



<a name="loio20b611c275191014aa0fe74fe3f2a8fa__section_gxw_14h_x2b"/>

## Additional Information

This view has a resettable counterpart; you can see the values since the last reset in the M\_OBJECT\_LOCK\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_OBJECT_LOCK_STATISTICS_RESET;`.

**Related Information**  


[M\_OBJECT\_LOCK\_STATISTICS\_RESET System View](m-object-lock-statistics-reset-system-view-20b644f.md "Provides lock contention statistics, including lock wait count, wait time, and failed count for each object since the last reset.")

[M\_OBJECT\_LOCKS System View](m-object-locks-system-view-20b66f9.md "Provides the status of currently acquired locks on objects with detailed information such as lock acquisition time and lock mode.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

