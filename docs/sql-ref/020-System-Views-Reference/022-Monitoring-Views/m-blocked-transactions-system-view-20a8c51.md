<!-- loio20a8c51d75191014b6c0e177ae946724 -->

# M\_BLOCKED\_TRANSACTIONS System View

Provides a transaction list waiting for locks.



<a name="loio20a8c51d75191014b6c0e177ae946724___m__b_l_o_c_k_e_d__t_r_a_n_s_a_c_t_i_o_n_s_1struct_M_BLOCKED_TRANSACTIONS"/>

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

BLOCKED\_TRANSACTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the transaction object ID of the transaction waiting for a lock.

</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_UPDATE\_TRANSACTION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the write transaction ID of the write transaction waiting for the lock.

</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID associated with the blocked write transaction.

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

Displays the transaction object ID of the transaction holding the lock.

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

Displays the write transaction ID of the write transaction holding the lock.

</td>
</tr>
<tr>
<td valign="top">

LOCK\_OWNER\_CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the connection ID associated with the write transaction holding the lock.

</td>
</tr>
<tr>
<td valign="top">

BLOCKED\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the blocked timestamp.

</td>
</tr>
<tr>
<td valign="top">

WAITING\_RECORD\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the ID of the record on which the lock is currently placed.

</td>
</tr>
<tr>
<td valign="top">

WAITING\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the schema on which the lock is currently placed.

</td>
</tr>
<tr>
<td valign="top">

WAITING\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object on which the lock is currently placed.

</td>
</tr>
<tr>
<td valign="top">

WAITING\_OBJECT\_TYPE

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

WAITING\_PART\_ID

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

LOCK\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the lock type: RECORD, TABLE, or METADATA.

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

Displays the lock mode: SHARED, EXCLUSIVE, or INTENTIONAL EXCLUSIVE.

</td>
</tr>
</table>

**Related Information**  


[M\_TRANSACTIONS System View](m-transactions-system-view-20c9610.md "Provides information about all transactions created by users or the database.")

[SET TRANSACTION AUTOCOMMIT DDL Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/set-transaction-autocommit-ddl-statement-transaction-management-d538d11.md "Specifies the auto commit property for DDL statements specific to the session.")

[Autonomous Transaction](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/4ad70daee8b64b90ab162565ed6f73ef.html "") :arrow_upper_right:

