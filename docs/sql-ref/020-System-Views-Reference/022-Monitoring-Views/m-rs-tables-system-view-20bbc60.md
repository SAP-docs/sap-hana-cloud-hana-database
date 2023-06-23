<!-- loio20bbc60675191014bf16fd69e531fa78 -->

# M\_RS\_TABLES System View

Provides information about row tables, including detailed table sizes and record count.



<a name="loio20bbc60675191014bf16fd69e531fa78___m__r_s__t_a_b_l_e_s_1struct_M_RS_TABLES"/>

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

RECORD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of records in this table.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_FIXED\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the allocated memory size in bytes for the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_PAGE\_HEADER\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the allocated and used memory size in bytes for the page headers of the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_PAGE\_FRAGMENT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the fragmented memory size in bytes of the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

USED\_FIXED\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used memory size in bytes for the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_PART\_FRAGMENT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the fragmented memory size in bytes of the used fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

FIXED\_PART\_FREE\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the free memory size in bytes in the pages of the fixed-size part.



</td>
</tr>
<tr>
<td valign="top">

ALLOCATED\_VARIABLE\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the allocated memory size in bytes for the variable-size part.



</td>
</tr>
<tr>
<td valign="top">

USED\_VARIABLE\_PART\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the used memory size in bytes for the variable-size part.



</td>
</tr>
<tr>
<td valign="top">

VARIABLE\_PART\_FRAGMENT\_SIZE



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the fragmented memory size in bytes of the used variable-size part.



</td>
</tr>
<tr>
<td valign="top">

LOAD\_STATUS



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the loading state of the table: LOADED, NOW\_LOADING, PREPARING\_UNLOAD, NOW\_UNLOADING, UNLOADED, or NOT\_SUPPORTED



</td>
</tr>
<tr>
<td valign="top">

IS\_REPLICA



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays the flag to indicate a replica.



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the create time of the table.



</td>
</tr>
<tr>
<td valign="top">

CONTAINER\_COUNT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the number of containers for the table.



</td>
</tr>
<tr>
<td valign="top">

SCAN\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of table scans.



</td>
</tr>
</table>

**Related Information**  


[M\_RS\_MEMORY System View](m-rs-memory-system-view-20bb47a.md "Provides RS memory statistics.")

[M\_RS\_INDEXES System View](m-rs-indexes-system-view-20bb03a.md "Provides the statistics for B-tree and CPB-tree indexes.")

[M\_RS\_TABLE\_VERSION\_STATISTICS System View](m-rs-table-version-statistics-system-view-20bb882.md "Provides information on row table versions: detailed version counts and used sizes.")

[TABLES System View](../021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[DROP TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-table-statement-data-definition-20d7fd2.md "Removes a physical or virtual table from the database.")

[Managing Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/68554490aee94885ba31611489a04992.html "The SAP HANA database stores data in memory in tables, organized in columns, and partitions, distributed among multiple servers.") :arrow_upper_right:

