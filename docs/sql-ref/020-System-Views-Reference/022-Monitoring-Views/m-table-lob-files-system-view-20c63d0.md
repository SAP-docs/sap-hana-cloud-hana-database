<!-- loio20c63d0b7519101494baf61d17e2b326 -->

# M\_TABLE\_LOB\_FILES System View

Provides information about all LOB files that belong to a table.



<a name="loio20c63d0b7519101494baf61d17e2b326___m__t_a_b_l_e__l_o_b__f_i_l_e_s_1struct_M_TABLE_LOB_FILES"/>

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

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name.

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

Displays the partition ID. Returns the following:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   In the case of replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is in progress.



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

Displays the table OID, same as owner\_oid if the table is found; 0 otherwise.

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

PHYSICAL\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file size in bytes.

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

Displays the LOB size in bytes.

</td>
</tr>
<tr>
<td valign="top">

CHARACTER\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of characters in NCLOB.

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

Displays the number of pages used for a LOB file.

</td>
</tr>
<tr>
<td valign="top">

LOB\_TYPE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the type of LOB.

</td>
</tr>
</table>

**Related Information**  


[M\_TABLE\_LOB\_STATISTICS System View](m-table-lob-statistics-system-view-722e79c.md "Provides information about the aggregated file and packed LOB statistics per host, port, table, partition, and column.")

[Large Object \(LOB\) Data Types](../../010-SQL-Reference/large-object-lob-data-types-c374aca.md "LOB (large objects) data types, such as NCLOB, and BLOB, are used to store a large amount of data, such as text documents and images.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Hybrid LOBs (Large Objects)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/61ab21a1972846e0aa0b9a989ce4867a.html "To save memory you can store LOB data on disk, in this case the data is only loaded into memory when it is needed. Alternatively, you can use the configurable Hybrid LOB feature which is flexible and stores LOBs either on disk or in memory depending on their size.") :arrow_upper_right:

