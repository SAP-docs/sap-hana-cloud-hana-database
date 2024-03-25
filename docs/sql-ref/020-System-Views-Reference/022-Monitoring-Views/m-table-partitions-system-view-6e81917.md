<!-- loio6e819179eebd4560a09cb1679748c025 -->

# M\_TABLE\_PARTITIONS System View

Provides information regarding partition-specific memory and disk usage for partitioned tables.




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

NODE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the partition node.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_NODE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID of the parent node.

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
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



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

Displays the effective load unit. Valid values are PAGE \(when the partition uses page loadable storage\) and COLUMN \(when the partition uses column loadable storage\).

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

Displays the total paged memory size in bytes, which is the sum of the memory in the main, delta, and history parts.

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

Displays the current paged memory consumption in main in bytes. This value varies depending on the number of loaded attributes and includes data for open transactions.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_PAGE\_LOADABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total resident paged memory size, in bytes, of the partition.

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

Displays the current memory consumption in delta in bytes.

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

Displays the current pure persistent memory consumption \(in bytes\) for every column store table

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

Displays the total size of a table partition on a disk in bytes.

</td>
</tr>
<tr>
<td valign="top">

DISK\_SIZE\_IN\_PAGE\_LOADABLE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total disk size, in bytes, of page-loadable storage for this partition.

</td>
</tr>
<tr>
<td valign="top">

ESTIMATED\_MAX\_MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total estimated maximum memory consumption in bytes for fully loaded partitions. This value does not include data for open transactions.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ESTIMATED\_MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the last estimated memory consumption in bytes of a fully loaded partition.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ESTIMATED\_MEMORY\_SIZE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">



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

Displays the record count.

</td>
</tr>
<tr>
<td valign="top">

RAW\_RECORD\_COUNT\_IN\_MAIN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current number of entries in the main part. This value differs from the number of visible main rows because there are entries for modified rows that are marked as invalidated.Displays the last time that the last-estimated memory consumption was calculated.

</td>
</tr>
<tr>
<td valign="top">

RAW\_RECORD\_COUNT\_IN\_DELTA

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the current number of entries in the delta part. This value differs from the number of visible delta rows because there are additional entries, such as deleted rows or updated rows. This value can contain deleted records.

</td>
</tr>
<tr>
<td valign="top">

LOADED

</td>
<td valign="top">

NVARCHAR\(10\)

</td>
<td valign="top">

Displays the last time that the last-estimated memory consumptionDisplays how many columns in the table are loaded in memory. Valuse are: NO, PARTIALLY, or FULL. For a description of each column, see M\_CS\_COLUMNS.

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

Displays whether the part is a replica \(TRUE/FALSE\).

</td>
</tr>
<tr>
<td valign="top">

GROUP\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the effective group type.

</td>
</tr>
<tr>
<td valign="top">

SUBTYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the effective group subtype.

</td>
</tr>
<tr>
<td valign="top">

GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the effective group name.

</td>
</tr>
</table>

**Related Information**  


[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[M\_TABLE\_PARTITION\_STATISTICS System View](m-table-partition-statistics-system-view-b825ba5.md "Returns the table partition runtime statistics for column store partition tables only. This view is empty if the partition_statistics_select_enabled property in the indexserver.ini configuration file is disabled.")

[M\_CS\_COLUMNS System View](m-cs-columns-system-view-20ad197.md "Provides runtime information about columns in column tables.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

