<!-- loiof413b6996f5b1014a86cea1ecb471939 -->

# M\_TABLE\_SNAPSHOTS System View

Provides snapshot information for tables that are blocked by table-wise GC.



<a name="loiof413b6996f5b1014a86cea1ecb471939___m__t_a_b_l_e__s_n_a_p_s_h_o_t_s_1struct_M_TABLE_SNAPSHOTS"/>

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

TABLE\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the table object ID.



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the table type: ROW/COLUMN.



</td>
</tr>
<tr>
<td valign="top">

MIN\_MVCC\_SNAPSHOT\_TIMESTAMP



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the minimum MVCC timestamp which is held by the table-wise GC blocker transaction or cursor.



</td>
</tr>
<tr>
<td valign="top">

VERSION\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of versions \(for a column table, this value is the number of unconsolidated udivlists\).



</td>
</tr>
</table>

**Related Information**  


[M\_SNAPSHOTS System View](m-snapshots-system-view-20c5439.md "Provides information about existing snapshots.")

[M\_MVCC\_SNAPSHOTS System View](m-mvcc-snapshots-system-view-b41f6b2.md "Provides detailed snapshot information of the Multiversion Concurrency Control (MVCC) manager.")

