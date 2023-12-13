<!-- loiocdd43294c8a74652b4b6246272db7939 -->

# PARTITIONED\_TABLES System View

Provides general partitioning information for all partitions of a table.



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

LEVEL\_1\_EXPRESSION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the partitioning expression for first-level partitions.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_1\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of partitions at the first level.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_1\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the partitioning type at the first level: HASH, RANGE, ROUNDROBIN, REPLICATE, or RANGE HETEROGENEOUS.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_EXPRESSION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the partitioning expression for second-level partitions.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the total number of partitions at the second level.

</td>
</tr>
<tr>
<td valign="top">

LEVEL\_2\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the partitioning type at the second level: HASH, RANGE, RANGE HETEROGENEOUS, or HASH HETEROGENEOUS. Heterogeneous indicates an unbalanced partitioning scheme.

</td>
</tr>
<tr>
<td valign="top">

CROSS\_STORAGE\_UNIQUE\_CONSTRAINTS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether constraint checking is done across stores: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PARTITIONING\_ON\_NON\_PRIMARY\_KEY\_COLUMNS

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether partitioning is on a non-primary key: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PRIMARY\_KEY\_UPDATE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether UPDATE statements are allowed on primary key columns: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DYNAMIC\_RANGE\_THRESHOLD

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the threshold after which a new partition is created dynamically.

</td>
</tr>
<tr>
<td valign="top">

PARTITION\_DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the PARTITION BY clause.

</td>
</tr>
</table>



<a name="loiocdd43294c8a74652b4b6246272db7939__section_fvk_dv1_x2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view also requires the SELECT privilege to see information in a table owned by another user.

**Related Information**  


[TABLE\_PARTITIONS System View](table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[M\_TABLE\_PARTITIONS System View](../022-Monitoring-Views/m-table-partitions-system-view-6e81917.md "Provides information regarding partition-specific memory and disk usage for partitioned tables.")

[M\_TABLE\_PARTITION\_STATISTICS System View](../022-Monitoring-Views/m-table-partition-statistics-system-view-b825ba5.md "Returns the table partition runtime statistics for column store partition tables only. This view is empty if the partition_statistics_select_enabled property in the indexserver.ini configuration file is disabled.")

[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[M\_TABLES System View](../022-Monitoring-Views/m-tables-system-view-20c7689.md "Provides information on row and column tables.")

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[NSE-Enabled Partitioned Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/322bb45b63fd4d3c90ca4baf5e7558df.html "For SAP HANA NSE tables, partitioning can be heterogeneous or non-heterogenous. However, partition load unit can be set only for heterogeneous partitioning. This scenario describes a sequence of steps creating a page-loadable, partitioned table and then altering its load unit.") :arrow_upper_right:

[Heterogeneous Create Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/heterogeneous-create-partition-clauses-d496e58.md "Defines the various partitioning clauses available for heterogeneous partitions when creating a new table.")

