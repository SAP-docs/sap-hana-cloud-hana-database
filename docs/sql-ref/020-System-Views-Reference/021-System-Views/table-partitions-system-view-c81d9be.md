<!-- loioc81d9beea383495c99ad48789b983708 -->

# TABLE\_PARTITIONS System View

Partition-specific information for partitioned tables.



## Structure


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data Type

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

Returns the table partition ID:

-   For partitioned tables, the part ID is equal to the sequential number of the partition, starting at 1.
-   For replicated tables, the part ID is 1 for the original table and subsequent part IDs are assigned to replica tables.
-   The part ID is 0 for tables that are not partitioned.
-   A part ID value of -1 indicates that a modification of the table schema is currently in progress.



</td>
</tr>
<tr>
<td valign="top">

LEVEL\_1\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the first level partition ID. Possible values are 1 through the number of first-level partitions. First-level partitions \(those used in ALTER TABLE...MOVE\) may have subpartitions. Displays the logical partition ID. Possible values are 1 through the number of partitions for partitioned tables. This is the ID shown in all monitoring views.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_PARTITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the subpartition ID. Possible values are 0 for tables without multilevel partitioning and 1 through the number of subpartitions for partitioned tables with multilevel partitioning.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_1\_RANGE\_MIN\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the minimum value of the range partition at the first level for a range-partitioned table; empty otherwise.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_1\_RANGE\_MAX\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Specifies the exclusive maximum value of the range partition at the first level for a range-partitioned table; empty otherwise. This value is not included in the range.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_RANGE\_MIN\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the minimum value of the range partition at the second level for a range-partitioned table; empty otherwise.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_RANGE\_MAX\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Specifies the exclusive maximum value of the range partition at the second level for a range-partitioned table; empty otherwise. This value is not included in the range.

</td>
</tr>
<tr>
<td valign="top">

IS\_CURRENT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the partition is the current partition: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

UNIQUE\_CONSTRAINTS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays if unique constraints are checked for this partition or not: TRUE/FALSE.

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

Displays the load unit for partition: PAGE \(when the partition uses page loadable storage\), COLUMN \(when the partition uses column loadable storage\), or DEFAULT.

</td>
</tr>
<tr>
<td valign="top">

INSERT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether INSERT statements are allowed on the partition: TRUE/FALSE.

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

NUMA\_NODE\_INDEXES

</td>
<td valign="top">

NVARCHAR \(1024\)

</td>
<td valign="top">

Displays a comma-separated list of user-specified logical NUMA node indexes for the table partition. The elements of the list are either individual nodes indexes or ranges of index nodes, or a mixture of both. For example, the value ***0, 1 TO 3, 6*** indicates node indexes 0, 1, 2, 3, and 6.

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

Displays the group type.

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

Displays the group subtype.

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

Displays the group name.

</td>
</tr>
</table>



<a name="loioc81d9beea383495c99ad48789b983708__section_epr_grq_xhb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

You must own or have SELECT permission on the tables.

To see table information, you must own or have SELECT permission on the tables.

**Related Information**  


[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[M\_TABLE\_PARTITIONS System View](../022-Monitoring-Views/m-table-partitions-system-view-6e81917.md "Provides information regarding partition-specific memory and disk usage for partitioned tables.")

[M\_TABLE\_PARTITION\_STATISTICS System View](../022-Monitoring-Views/m-table-partition-statistics-system-view-b825ba5.md "Returns the table partition runtime statistics for column store partition tables only. This view is empty if the partition_statistics_select_enabled property in the indexserver.ini configuration file is disabled.")

[Heterogeneous Create Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/heterogeneous-create-partition-clauses-d496e58.md "Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.")

[Heterogeneous Alter Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/heterogeneous-alter-partition-clauses-a4258b8.md "Modifies the partitions of an existing table with a heterogeneous partitioning schema.")

[Non-Heterogeneous Create Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/non-heterogeneous-create-partition-clauses-ca6a99b.md "Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.")

[Non-Heterogeneous Alter Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md "Modifies the partitions of an existing table with a non-heterogeneous partitioning schema.")

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

