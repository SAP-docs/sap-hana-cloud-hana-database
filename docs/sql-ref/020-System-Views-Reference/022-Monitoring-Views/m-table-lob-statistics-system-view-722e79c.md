<!-- loio722e79cedc304a9e8212b00297cfc124 -->

# M\_TABLE\_LOB\_STATISTICS System View

Provides information about the aggregated file and packed LOB statistics per host, port, table, partition, and column.



<a name="loio722e79cedc304a9e8212b00297cfc124___m__t_a_b_l_e__l_o_b__f_i_l_e_s_1struct_M_TABLE_LOB_STATISTICS"/>

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

Displays the name of the host.



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

Displays the schema name associated with the LOBs.



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

Displays the table name associated with the LOBs.



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

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the column name associated with the LOBs.



</td>
</tr>
<tr>
<td valign="top">

LOB\_STORAGE\_TYPE



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays that the LOB storage type is one of the following:


<dl>
<dt><b>

INPLACE

</b></dt>
<dd>

Small LOBs \(completely loaded into the main memory\).



</dd><dt><b>

PACKED

</b></dt>
<dd>

Medium-sized LOBs where the size is between two thresholds \(only loaded into the main memory when required\).



</dd><dt><b>

FILE

</b></dt>
<dd>

Large LOBs \(individually loaded into the main memory on demand\).



</dd>
</dl>



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

Displays the container ID of the packed LOB container; NULL for file LOBs.



</td>
</tr>
<tr>
<td valign="top">

DISK\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of bytes used for the LOBs on a disk.



</td>
</tr>
<tr>
<td valign="top">

BINARY\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the binary size in bytes of the LOBs. This value may be less than the DISK\_SIZE due to management information and paging.



</td>
</tr>
<tr>
<td valign="top">

CHARACTER\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of characters in the NCLOBs \(only\) column. For packed LOBs, this corresponds to the total number of characters of all of the LOBs in the container.



</td>
</tr>
<tr>
<td valign="top">

LOB\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the total number of associated LOBs.



</td>
</tr>
<tr>
<td valign="top">

READ\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the counter for read operations on the LOBs.



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

Displays the size in bytes of the LOB pages that are loaded in the memory.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_PAGE\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of LOB pages loaded in the memory.



</td>
</tr>
</table>

**Related Information**  


[M\_TABLE\_LOB\_FILES System View](m-table-lob-files-system-view-20c63d0.md "Provides information about all LOB files that belong to a table.")

[Large Object \(LOB\) Data Types](../../010-SQL-Reference/large-object-lob-data-types-c374aca.md "LOB (large objects) data types, such as NCLOB, and BLOB, are used to store a large amount of data, such as text documents and images.")

