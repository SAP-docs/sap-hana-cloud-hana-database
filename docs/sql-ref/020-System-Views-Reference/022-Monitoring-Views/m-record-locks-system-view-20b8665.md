<!-- loio20b8665a751910148dd0e46c9b8b7783 -->

# M\_RECORD\_LOCKS System View

Provides the record lock status.



<a name="loio20b8665a751910148dd0e46c9b8b7783___m__r_e_c_o_r_d__l_o_c_k_s_1struct_M_RECORD_LOCKS"/>

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

RECORD\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the record ID.

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

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name.

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

Displays the lock mode \(exclusive lock\).

</td>
</tr>
</table>

**Related Information**  


[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

