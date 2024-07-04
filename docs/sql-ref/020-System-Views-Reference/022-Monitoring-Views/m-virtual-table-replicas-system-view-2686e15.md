<!-- loio2686e15ce25848db9bc1da827830d815 -->

# M\_VIRTUAL\_TABLE\_REPLICAS System View

Provides information on the status of a replica table and on the progress of initializing a replica table.



<a name="loio2686e15ce25848db9bc1da827830d815___v_i_r_t_u_a_l__t_a_b_l_e_s_1struct_VIRTUAL_TABLES"/>

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

Displays the port number.

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

Displays the replica schema name \(replication target\).

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

Displays the replica table name \(replication target\).

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TYPE

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the type of replication: ASYNCHRONOUS, SYNCHRONOUS.

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

Displays the schema name of the virtual table

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

Displays the virtual table name of the replication source.

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

Displays the partition ID. 0 for non-partitioned tables and 1 through the number of partitions for partitioned tables.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_ENABLING\_PROGRESS

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the current progress of replication when replication is being enabled.

</td>
</tr>
<tr>
<td valign="top">

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the current asynchronous replication status: ENABLED, ENABLING, DISABLED.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time when replication was enabled.

</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time when replication was disabled.

</td>
</tr>
<tr>
<td valign="top">

SHARE\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of virtual tables that are currently pointing to a shared replica.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SYNC\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last replication synchronization.

</td>
</tr>
</table>

**Related Information**  


[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

[VIRTUAL\_TABLE\_PARAMETERS System View](../021-System-Views/virtual-table-parameters-system-view-95054e1.md "Provides a list of parameters of the virtual tables that refer to column views in a remote SAP HANA database.")

[VIRTUAL\_TABLE\_PROPERTIES System View](../021-System-Views/virtual-table-properties-system-view-88396eb.md "Provides the properties set on virtual tables.")

[Managing Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/d16e86e414b54cd0b6facd4f6a2e7e01.html "Virtual tables point to remote tables or views in a remote source. When SQL queries are executed on a virtual table, they access the remote data as if it were stored locally.") :arrow_upper_right:

[Create a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/4ef3f55395dc47a89462b77b56d71f7f.html "Create a virtual table from the remote object of a remote source.") :arrow_upper_right:

[Delete a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/ebcb10f2c2d44b3294dfb0cadd88c396.html "Delete an existing virtual table from your schema using the SAP HANA database explorer.") :arrow_upper_right:

[List All Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/f4badb298616428ba585f68d4c68daa1.html "Provides a list of all virtual tables you have privilege to.") :arrow_upper_right:

[List Virtual Tables by Schema](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/682a0b4ee20349a0b36d3d940a6efaa0.html "Display the virtual tables of a remote source by schema using SQL syntax.") :arrow_upper_right:

[Refresh a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/14ea22d516634790a29c2e3676dcb9b1.html "Update a virtual table to reflect metadata changes in the corresponding remote source table using SQL syntax.") :arrow_upper_right:

