<!-- loio20ad197a75191014ad6f935d3c9200ca -->

# M\_CS\_COLUMNS System View

Provides runtime information about columns in column tables.



<a name="loio20ad197a75191014ad6f935d3c9200ca___m__c_s__c_o_l_u_m_n_s_1struct_M_CS_COLUMNS"/>

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
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
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

Displays the sum, in bytes, of the memory used.

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

Displays the current memory consumption, in bytes, in main. Returns 0 if the memory is not loaded in main.

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

Displays the current memory consumption, in bytes, in delta. Returns 0 if the memory is not loaded in delta.

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

Displays the record count. This value is -1 if the count is not loaded.

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

Displays a distinct count of values, generally. This value is 0 if the count is not loaded.

The values in this column are not equal to actual values that might be returned by a SELECT DISTINCT query. Do not use these values in a production system if precision is required.

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

Displays the type of column compression:

-   SPARSE
-   PREFIXED
-   CLUSTERED
-   INDIRECT
-   RLE
-   DEFAULT \(if the column is only dictionary coded\)



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

Displays that a conventional index is defined on the column.



</dd><dt><b>

BLOCK

</b></dt>
<dd>

Displays that a block index is defined on the column.



</dd><dt><b>

MINMAX

</b></dt>
<dd>

Displays that a min-max index is defined on the column.



</dd><dt><b>

NONE

</b></dt>
<dd>

Displays that no index is defined on the column.



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

Displays the internal implementation specification summary of the column.

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

Indicates whether the column is loaded into the memory: TRUE/FALSE.

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

Displays the load unit for the column: PAGE, COLUMN, and UNKNOWN.

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

Displays the last time that the column was loaded. This is undefined for unloaded columns.

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

Displays the persistent memory preference inferred from the user-specified preferences in a bottom-up manner starting from this object: TRUE/FALSE.

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

> ### Note:  
> The value -1 for NUME\_NODE\_INDEX indicates that the supplied NUMA \(Non-Uniform Memory Access\) number is invalid. This can occur when there is only one NUMA node available in the system, and the provided NUMA number is greater than one. In this case, the value will be set to -1.
> 
> Additionally, a -1 value for the NUMA node index can also signify that no specific and valid node is defined. This might be the case when NUMA handling is completely disabled for a system, either manually or when there is only one socket, which means there is no NUMA configuration.



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



<a name="loio20ad197a75191014ad6f935d3c9200ca__section_irw_3z5_tbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.



<a name="loio20ad197a75191014ad6f935d3c9200ca__section_gpc_wrh_skb"/>

## Additional Information

The information returned in the view is valid only for loaded columns \(LOADED = TRUE\).

**Related Information**  


[M\_CS\_ALL\_COLUMNS System View](m-cs-all-columns-system-view-20acf4c.md "Provides runtime information for all columns in column tables, including internal column tables.")

[CS\_ALL\_COLUMNS System View](../021-System-Views/cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[CS\_CONCAT\_COLUMNS System View](../021-System-Views/cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_VIEW\_COLUMNS System View](../021-System-Views/cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[RENAME COLUMN Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-column-statement-data-definition-20fb2b8.md "Changes the name of a column.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

[Data Compression in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd9017c8bb571014ae79efaeb46940f3.html "The column store allows for the efficient compression of data. This makes it less costly for the SAP HANA database to keep data in main memory. It also speeds up searches and calculations.") :arrow_upper_right:

[Viewing Load Unit Information for Column Store Tables in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/61c9c0f4379c41f3b3e1c483f2395a11.html "Several system and monitoring views provide information on load unit preferences (PAGE loadable, COLUMN loadable, or DEFAULT loadable) set for the SAP HANA NSE column-store table.") :arrow_upper_right:

[Understanding Load Unit Behavior in SAP HANA NSE Column Store Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/202101e31f1a42c884dd1d2057c6a605.html "The loading behavior is determined by the load unit (one of PAGE, COLUMN, and DEFAULT) specified for the column, partition, and table in SAP HANA native storage extension (NSE) column-store tables.") :arrow_upper_right:

[Monitoring View Extensions for Column Store Paged Data Size](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/b06e99431b2740fdb4a47c7ee130f89d.html "A number of monitoring views provide information about the in-memory and on-disk size of the page-loadable data in relation to the in-memory and on-disk size of non-paged (column-loadable) data, helping you understand the effectiveness of page-loadable storage.") :arrow_upper_right:

