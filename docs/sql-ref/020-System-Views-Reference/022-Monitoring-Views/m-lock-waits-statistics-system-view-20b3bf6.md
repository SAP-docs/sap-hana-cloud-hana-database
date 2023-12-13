<!-- loio20b3bf6575191014b994b2a0c342fe4c -->

# M\_LOCK\_WAITS\_STATISTICS System View

Provides the accumulated lock wait count and duration for record locks, table locks, and metadata locks for all available services from database start up until the current time.



<a name="loio20b3bf6575191014b994b2a0c342fe4c___m__l_o_c_k__w_a_i_t_s__s_t_a_t_i_s_t_i_c_s_1struct_M_LOCK_WAITS_STATISTICS"/>

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

LOCK\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the lock type: RECORD/TABLE.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAITS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait count.

</td>
</tr>
<tr>
<td valign="top">

TOTAL\_LOCK\_WAIT\_TIME

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total lock wait duration in microseconds.

</td>
</tr>
</table>

**Related Information**  


[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

