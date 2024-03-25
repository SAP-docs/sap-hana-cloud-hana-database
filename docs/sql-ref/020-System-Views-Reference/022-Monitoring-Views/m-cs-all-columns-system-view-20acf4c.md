<!-- loio20acf4cd75191014883fd492d33235e2 -->

# M\_CS\_ALL\_COLUMNS System View

Provides runtime information for all columns in column tables, including internal column tables.



<a name="loio20acf4cd75191014883fd492d33235e2___m__c_s__a_l_l__c_o_l_u_m_n_s_1struct_M_CS_ALL_COLUMNS"/>

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

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table, and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   The part ID -1 indicates that the table schema is being modified.



</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the sum of the MEMORY\_SIZE\_IN\_MAIN and MEMORY\_SIZE\_IN\_DELTA columns in bytes.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_MAIN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in main in bytes. Returns 0 if the memory is not loaded in main.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_DELTA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in delta in bytes. Returns 0 if the memory is not loaded in delta.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_PAGE\_LOADABLE\_MAIN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total paged memory size of the column in bytes.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For columns stored in persistent memory, displays the total memory size in bytes.

</td>
</tr>
<tr>
<td valign="top">

COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the record count. Returns 0 if the count is not loaded.

</td>
</tr>
<tr>
<td valign="top">

DISTINCT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the distinct count of values. Returns 0 if the count is not loaded.

</td>
</tr>
<tr>
<td valign="top">

COMPRESSION\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of column compression. This value can be: SPARSE, PREFIXED, CLUSTERED, INDIRECT, RLE, or DEFAULT \(if the column is only dictionary coded\). The columns in the M\_CS\_COLUMNS system view show the runtime value, which can be changed during the runtime.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of inverted index:


<dl>
<dt><b>

FULL

</b></dt>
<dd>

Displays that a FULL inverted index is defined on the column. A FULL index is a data structure that assigns a position to each value in the column. FULL indexes are the conventional form of index.



</dd><dt><b>

BLOCK

</b></dt>
<dd>

Displays that a block index is defined on the column.

A BLOCK index is a data structure where each value in the column is assigned to one of a list of fixed-size blocks for the column. BLOCK indexes are typically much smaller than FULL indexes. Reverse look-ups on BLOCK indexes are effectively a combination of reading the index \(fast\) and scanning the read blocks \(possibly slow, depending on the compression of the column\). BLOCK indexes can be used with compressed columns.



</dd><dt><b>

MINMAX

</b></dt>
<dd>

Displays that a min-max index is defined for the column.



</dd><dt><b>

NONE

</b></dt>
<dd>

Displays that no index is defined for the column.



</dd>
</dl>



</td>
</tr>
<tr>
<td valign="top">

INDEX\_LOADED

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the load status of the inverted index: NOT APPLICABLE, UNLOADED, or LOADED.

</td>
</tr>
<tr>
<td valign="top">

IMPLEMENTATION\_FLAGS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the column internal implementation specification summary.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ACCESS\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that the column was read or there was an INSERT to, UPDATE of, or DELETE from the column. This value is undefined for unloaded columns.

</td>
</tr>
<tr>
<td valign="top">

LOADED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the flag to indicate that the column is loaded into memory \(including DRAM or persistent memory\): TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LOADED\_FROM\_PERSISTENT\_MEMORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column was loaded from persistent memory: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

STORED\_IN\_PERSISTENT\_MEMORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether there is an associated persistent memory block: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

LOAD\_UNIT

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the load unit for the columns: PAGE, COLUMN, and UNKNOWN.

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

Displays the object ID of the table.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_MEMORY\_SIZE\_IN\_DATA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the data in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_MEMORY\_SIZE\_IN\_DICT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the dictionary in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_MEMORY\_SIZE\_IN\_INDEX

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the index in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_MEMORY\_SIZE\_IN\_MISC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the miscellaneous current memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_MEMORY\_SIZE\_IN\_DATA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the data in bytes.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_MEMORY\_SIZE\_IN\_DICT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the dictionary in bytes.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_MEMORY\_SIZE\_IN\_INDEX

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current memory consumption in the index in bytes.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_MEMORY\_SIZE\_IN\_MISC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the miscellaneous current memory consumption in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PAGE\_LOADABLE\_MEMORY\_SIZE\_IN\_DATA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total paged memory size of the column index vector in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PAGE\_LOADABLE\_MEMORY\_SIZE\_IN\_DICT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total paged memory of the column dictionary in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PAGE\_LOADABLE\_MEMORY\_SIZE\_IN\_INDEX

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total paged memory of the column's inverted index in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PAGE\_LOADABLE\_MEMORY\_SIZE\_IN\_MISC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total paged memory size of other column structures in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PERSISTENT\_MEMORY\_SIZE\_IN\_DATA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For columns stored in persistent memory, displays the current memory consumption in the data in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PERSISTENT\_MEMORY\_SIZE\_IN\_DICT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For columns stored in persistent memory, displays the current memory consumption in the dictionary in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PERSISTENT\_MEMORY\_SIZE\_IN\_INDEX

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For columns stored in persistent memory, displays the current memory consumption in the index in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PERSISTENT\_MEMORY\_SIZE\_IN\_MISC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

For columns stored in persistent memory, displays the current memory consumption not already accounted for in the other memory size columns in bytes.

</td>
</tr>
<tr>
<td valign="top">

MAIN\_PERSISTENT\_MEMORY\_SIZE\_UNUSED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the amount of persistent memory, in bytes, that is not directly mapped to a corresponding data structure during load, but was only read to construct the data structure in DRAM. This column also includes persistent memory block overhead if the requested persistent memory allocation is not a multiple of a block size.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_CREATE\_DURATION

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the time needed to create an inverted index.

</td>
</tr>
<tr>
<td valign="top">

DELTA\_IMPLEMENTATION\_FLAGS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the internal column implementation specification summary.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_ATTRIBUTE\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the attribute type for internal columns. Returns NULL for non-internal columns.

</td>
</tr>
<tr>
<td valign="top">

LAST\_LOAD\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that the column was loaded. This value is undefined for unloaded columns.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the persistent memory preference inferred from the user-specified preferences.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEX

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the NUMA node index where allocations are performed and columns are loaded.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MEMORY\_FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the persistent memory file associated with the column. If there is no associated persistent memory file, then NULL is returned.

</td>
</tr>
</table>



<a name="loio20acf4cd75191014883fd492d33235e2__section_gpc_wrh_skb"/>

## Additional Information

The information returned in the view is valid only for loaded columns \(LOADED = TRUE\).

**Related Information**  


[M\_CS\_ALL\_COLUMN\_STATISTICS System View](m-cs-all-column-statistics-system-view-2cb5b77.md "Provides information on how many scans and index searches were performed on any specified columns.")

[CS\_ALL\_COLUMNS System View](../021-System-Views/cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[CS\_CONCAT\_COLUMNS System View](../021-System-Views/cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_VIEW\_COLUMNS System View](../021-System-Views/cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[RENAME COLUMN Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-column-statement-data-definition-20fb2b8.md "Changes the name of a column.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

[Data Compression in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/bd9017c8bb571014ae79efaeb46940f3.html "The column store allows for the efficient compression of data. This makes it less costly for the SAP HANA database to keep data in main memory. It also speeds up searches and calculations.") :arrow_upper_right:

[Viewing Load Unit Information for Column Store Tables in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/61c9c0f4379c41f3b3e1c483f2395a11.html "Several system and monitoring views provide information on load unit preferences (PAGE loadable, COLUMN loadable, or DEFAULT loadable) set for the SAP HANA NSE column-store table.") :arrow_upper_right:

[Understanding Load Unit Behavior in SAP HANA NSE Column Store Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/202101e31f1a42c884dd1d2057c6a605.html "The loading behavior is determined by the load unit (one of PAGE, COLUMN, and DEFAULT) specified for the column, partition, and table in SAP HANA native storage extension (NSE) column-store tables.") :arrow_upper_right:

[Monitoring View Extensions for Column Store Paged Data Size](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/b06e99431b2740fdb4a47c7ee130f89d.html "A number of monitoring views provide information about the in-memory and on-disk size of the page-loadable data in relation to the in-memory and on-disk size of non-paged (column-loadable) data, helping you understand the effectiveness of page-loadable storage.") :arrow_upper_right:

