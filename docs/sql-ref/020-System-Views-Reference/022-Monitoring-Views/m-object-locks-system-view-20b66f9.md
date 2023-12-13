<!-- loio20b66f9475191014b981b6b2b5432e61 -->

# M\_OBJECT\_LOCKS System View

Provides the status of currently acquired locks on objects with detailed information such as lock acquisition time and lock mode.



<a name="loio20b66f9475191014b981b6b2b5432e61___m__o_b_j_e_c_t__l_o_c_k_s_1struct_M_OBJECT_LOCKS"/>

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

LOCK\_OWNER\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction object ID owning the lock.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_OWNER\_UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the write transaction ID owning the lock.

</td>
</tr>
<tr>
<td valign="top">

ACQUIRED\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the lock acquisition time.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object OID.

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

Displays the schema name.

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

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the object type.

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

Displays the ID of the locked partition, or 0 for a non-partition lock.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_MODE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the lock mode: EXCLUSIVE/INTENTIONAL EXCLUSIVE

</td>
</tr>
</table>

**Related Information**  


[M\_OBJECT\_LOCK\_STATISTICS System View](m-object-lock-statistics-system-view-20b611c.md "Provides lock contention statistics, including lock wait count, wait time, and failed count, for each object.")

[M\_OBJECT\_LOCK\_STATISTICS\_RESET System View](m-object-lock-statistics-reset-system-view-20b644f.md "Provides lock contention statistics, including lock wait count, wait time, and failed count for each object since the last reset.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

