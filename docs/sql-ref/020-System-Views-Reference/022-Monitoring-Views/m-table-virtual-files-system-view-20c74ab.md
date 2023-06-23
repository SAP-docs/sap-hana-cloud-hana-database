<!-- loio20c74ab175191014b1ecfbf046994dea -->

# M\_TABLE\_VIRTUAL\_FILES System View

Provides information about all virtual files that belong to a table.



<a name="loio20c74ab175191014b1ecfbf046994dea___m__t_a_b_l_e__v_i_r_t_u_a_l__f_i_l_e_s_1struct_M_TABLE_VIRTUAL_FILES"/>

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

PART\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that the table schema is currently in being modified.



</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the container ID.



</td>
</tr>
<tr>
<td valign="top">

NAMESPACE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the namespace address in the database storage system.



</td>
</tr>
<tr>
<td valign="top">

NAME



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the name in the database storage system.



</td>
</tr>
<tr>
<td valign="top">

PHYSICAL\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the storage size used for the file in bytes.



</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of storage pages used for the file.



</td>
</tr>
</table>

**Related Information**  


[M\_TABLES System View](m-tables-system-view-20c7689.md "Provides information on row and column tables.")

[M\_TABLE\_LOB\_FILES System View](m-table-lob-files-system-view-20c63d0.md "Provides information about all LOB files that belong to a table.")

