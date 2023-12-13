<!-- loio11a4a8a82b3c4273b8ab22ec9c3432d2 -->

# M\_NUMA\_NODES System View

Provides resource availability information on each NUMA node in the hardware topology, including inter-node distances and neighbor information.



<a name="loio11a4a8a82b3c4273b8ab22ec9c3432d2___m__m_v_c_c__t_a_b_l_e_s_1struct_M_MVCC_TABLES"/>

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

NUMA\_NODE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the physical NUMA node ID as shown by the operating system.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEX

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the logical NUMA node index. Indexes are in the range of 0 to MAX\_NUMA\_NODE\_COUNT.

</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_LOGICAL\_CORE\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total active logical core count in the NUMA node.

</td>
</tr>
<tr>
<td valign="top">

LOGICAL\_CORE\_IDS

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the range-separated list of logical core IDs in the NUMA node, for example, \(0-3,10-13\).

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total memory size, in bytes, present in the NUMA node.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_DISTANCES

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the distances from this node to all other nodes. Indexes in this list are NUMA\_NODE\_INDEX and the number of entries are as many as MAX\_NUMA\_NODE\_COUNT.

</td>
</tr>
<tr>
<td valign="top">

NEIGHBOUR\_NUMA\_NODE\_IDS

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the physical NUMA node ID of the neighboring nodes.

</td>
</tr>
</table>

**Related Information**  


[M\_NUMA\_RESOURCES System View](m-numa-resources-system-view-b70b8c0.md "Provides information on overall resource availability for the system.")

[IMPORT Statement \(Data Import Export\)](../../010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

