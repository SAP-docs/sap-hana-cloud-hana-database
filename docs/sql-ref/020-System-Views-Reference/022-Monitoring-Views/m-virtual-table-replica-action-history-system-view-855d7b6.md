<!-- loio855d7b66b2b147879ab28c9024800cd0 -->

# M\_VIRTUAL\_TABLE\_REPLICA\_ACTION\_HISTORY System View

Provides replica action information.



<a name="loio855d7b66b2b147879ab28c9024800cd0___v_i_r_t_u_a_l__t_a_b_l_e_s_1struct_VIRTUAL_TABLES"/>

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

VARCHAR\(64\)

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

Displays the internal port number.

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

Displays the schema name of the replica table.

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

Displays the replica table name.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TYPE

</td>
<td valign="top">

VARCHAR\(12\)

</td>
<td valign="top">

Displays the replica type: ASYNCHRONOUS, SYNCHRONOUS.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the virtual table.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the virtual table name.

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

Displays the partition ID \(0 for non-partitioned tables\).

</td>
</tr>
<tr>
<td valign="top">

PARENT\_STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the statement ID which triggered the action.

</td>
</tr>
<tr>
<td valign="top">

IS\_ASYNC

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not an asynchronous job is created for the action: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ACTION\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the action type: ADD, ENABLE, DISABLE, ALTER, DROP, REFRESH, CANCEL.

</td>
</tr>
<tr>
<td valign="top">

START\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the replica action start time.

</td>
</tr>
<tr>
<td valign="top">

END\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the replica action end time.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the error time.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the error code.

</td>
</tr>
<tr>
<td valign="top">

ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the error message.

</td>
</tr>
</table>

**Related Information**  


[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

[VIRTUAL\_TABLES System View](../021-System-Views/virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[VIRTUAL\_TABLE\_REPLICAS System View](../021-System-Views/virtual-table-replicas-system-view-ce3d19f.md "Provides information on the relationships between virtual tables and replica tables.")

