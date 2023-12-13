<!-- loio210197377519101481cfb213f0b84848 -->

# TABLES System View

Provides information about tables in the database.



<a name="loio210197377519101481cfb213f0b84848___t_a_b_l_e_s_1struct_TABLES"/>

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

Displays the object ID of the table.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the table description.

</td>
</tr>
<tr>
<td valign="top">

FIXED\_PART\_SIZE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the fixed part size of the table.

</td>
</tr>
<tr>
<td valign="top">

IS\_LOGGED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not logging was on for the table at last restart time: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_COLUMN\_TABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is a column table: TRUE/FALSE.

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

Displays the type of the table: ROW, COLUMN, or VIRTUAL.

</td>
</tr>
<tr>
<td valign="top">

IS\_INSERT\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is an insert-only table: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_TEMPORARY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is a temporary table: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

TEMPORARY\_TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays the temporary table type.

</td>
</tr>
<tr>
<td valign="top">

COMMIT\_ACTION

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the setting for on commit deletion for global temporary tables.

</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_DEFINED\_TYPE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not this is a user-defined table type: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_PRIMARY\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table has a primary key: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

USES\_EXTKEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses an external key: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

AUTO\_MERGE\_ON

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not automatic delta table merge is activated for the table: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

USES\_DIMFN\_CACHE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses the DimFunctionCache feature: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

IS\_PUBLIC

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table is public: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

AUTO\_OPTIMIZE\_COMPRESSION\_ON

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not automatic optimize compression is activated for the table: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

COMPRESSED\_EXTKEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses a compressed external key: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

USES\_QUEUE\_TABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses a queue table: TRUE/FALSE. Only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

IS\_PRELOAD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses preloading: TRUE/FALSE. Only valid for column store tables. Preload information can be NULL for row storeor virtual columns.

</td>
</tr>
<tr>
<td valign="top">

IS\_PARTIAL\_PRELOAD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table uses partial preloading: TRUE/FALSE. Only valid for column store tables. Preload information can be NULL for row storeor virtual columns 

</td>
</tr>
<tr>
<td valign="top">

UNLOAD\_PRIORITY

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the unload priority of the table: 0 - 9 means not unloadable, 1 means latest unload, and 9 means earliest unload.

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

Displays whether or not the table is a replica: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

ROW\_ORDER\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the row order type: NULL/BY VALUE.

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

Displays the creation time of the table.

</td>
</tr>
<tr>
<td valign="top">

TEMPORAL\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the type of temporal table:

-   TEMPORAL - a table with system versioning enabled. Tables of this type have a corresponding entry in the TEMPORAL\_TABLES system table.

-   HISTORY - the history table associated with a system-versioned table.

-   NULL - all other types of tables.




</td>
</tr>
<tr>
<td valign="top">

HAS\_MASKED\_COLUMNS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not the table has a mask definition for at least one column: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

MASK\_MODE

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the mask mode to be applied if the table has masked columns: DEFAULT or SESSION USER; otherwise NULL.

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

Displays the user-specified persistent memory preference: TRUE \(persistent memory is ON\)/FALSE \(persistent memory OFF\). If the user has not specified a persistent memory preference, or if the preference is set to the default, then the value is NULL.

</td>
</tr>
<tr>
<td valign="top">

HAS\_RECORD\_COMMIT\_TIMESTAMP

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is tracking commit timestamps: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_REPLICATION\_LOG\_ENABLED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table's replication log is collected. Values are TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

NUMA\_NODE\_INDEXES

</td>
<td valign="top">

NVARCHAR \(1024\)

</td>
<td valign="top">

Displays a comma-separated list of user-specified logical NUMA node indexes for the table. For each column entry in this view there are preferences \(if set\); otherwise, the value is NULL.

The elements of the list are either individual nodes indexes or ranges of index nodes, or a mixture of both. For example, the value ***0, 1 TO 3, 6*** indicates node indexes 0, 1, 2, 3, and 6.

</td>
</tr>
<tr>
<td valign="top">

IS\_MOVABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table can be moved to another location: TRUE/FALSE.

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

Displays the load unit for the table partition: TABLE, PAGE \(when the partition uses paged attributes\), COLUMN, or DEFAULT.

</td>
</tr>
<tr>
<td valign="top">

IS\_SYSTEM\_TABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Returns TRUE if the table's schema is SYS, or if the table schema or name starts with \_SYS\_.

</td>
</tr>
</table>



<a name="loio210197377519101481cfb213f0b84848__section_qjs_rwz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[TABLE\_COLUMNS System View](table-columns-system-view-2100d33.md "Provides information about available table columns.")

[TABLE\_COLUMNS\_ODBC System View](table-columns-odbc-system-view-210065d.md "Provides information about available table columns.")

[TABLE\_GROUPS System View](table-groups-system-view-210103b.md "Provides an overview of table group relationships.")

[TABLE\_PARTITIONS System View](table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[TABLE\_PLACEMENT System View](table-placement-system-view-522cc8e.md "Provides table placement information.")

[TABLE\_REPLICAS System View](table-replicas-system-view-d2353ea.md "Provides information about replicated tables and their replicas.")

[TEMPORAL\_TABLES System View](temporal-tables-system-view-c978342.md "Provides information about system-versioned tables, history tables, and application-time period tables.")

[M\_TABLES System View](../022-Monitoring-Views/m-tables-system-view-20c7689.md "Provides information on row and column tables.")

[M\_TABLE\_LOCATIONS System View](../022-Monitoring-Views/m-table-locations-system-view-20c65d5.md "Provides information about tables and their logical location. Physical locations are shown in M_TABLE_PERSISTENCE_LOCATIONS.")

[M\_TABLE\_SNAPSHOTS System View](../022-Monitoring-Views/m-table-snapshots-system-view-f413b69.md "Provides snapshot information for tables that are blocked by table-wise GC.")

[M\_TABLE\_STATISTICS System View](../022-Monitoring-Views/m-table-statistics-system-view-882b8fd.md "Returns the table runtime statistics.")

[M\_TABLE\_STATISTICS\_RESET System View](../022-Monitoring-Views/m-table-statistics-reset-system-view-6e98780.md "Returns the table DML runtime statistics since the last reset.")

[M\_TABLE\_VIRTUAL\_FILES System View](../022-Monitoring-Views/m-table-virtual-files-system-view-20c74ab.md "Provides information about all virtual files that belong to a table.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

[RENAME TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-table-statement-data-definition-20fbadb.md "Changes the schema and/or the name of a table.")

[TRUNCATE TABLE Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/truncate-table-statement-data-manipulation-20fe29f.md "Deletes all rows from a table or projection view.")

[DROP TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-table-statement-data-definition-20d7fd2.md "Removes a physical or virtual table from the database.")

[Managing Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/68554490aee94885ba31611489a04992.html "The SAP HANA database stores data in memory in tables, organized in columns, and partitions, distributed among multiple servers.") :arrow_upper_right:

[Emptiness Check for Tables and Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/3905f921a16f41d6addcf8d7979560c2.html "") :arrow_upper_right:

[Table Parameter](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/9bd0c03743164aa7a87a93f9afb253b1.html "") :arrow_upper_right:

[Save Table](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/2bbdb7a5b2a04ae9b51291d1b9416bfb.html "") :arrow_upper_right:

[Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/c8a483c3fcc94c0ca390bd1a8776d081.html "") :arrow_upper_right:

[Table Types](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/afb0aa424dea4ef0af372d99135a6a76.html "") :arrow_upper_right:

