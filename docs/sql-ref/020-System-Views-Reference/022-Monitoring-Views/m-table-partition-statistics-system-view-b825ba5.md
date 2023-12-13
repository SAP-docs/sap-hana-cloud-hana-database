<!-- loiob825ba5920374182a7caf5645a6a2cee -->

# M\_TABLE\_PARTITION\_STATISTICS System View

Returns the table partition runtime statistics for column store partition tables only. This view is empty if the partition\_statistics\_select\_enabled property in the `indexserver.ini` configuration file is disabled.



<a name="loiob825ba5920374182a7caf5645a6a2cee__section_jdh_h22_5bb"/>

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

SELECT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times a partition has been selected.

</td>
</tr>
<tr>
<td valign="top">

LAST\_SELECT\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time that this partition was selected.

</td>
</tr>
</table>

**Related Information**  


[M\_TABLE\_PARTITIONS System View](m-table-partitions-system-view-6e81917.md "Provides information regarding partition-specific memory and disk usage for partitioned tables.")

[M\_EXPENSIVE\_STATEMENTS System View](m-expensive-statements-system-view-20af736.md "Provides all statements with a duration longer than a specified threshold.")

[Table Partitioning](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/c2ea130bbb571014b024ffeda5090764.html "The partitioning feature of the SAP HANA database splits column-store tables horizontally into disjunctive sub-tables or partitions. In this way, large tables can be broken down into smaller, more manageable parts. Partitioning is typically used in multiple-host systems, but it may also be beneficial in single-host systems.") :arrow_upper_right:

[TABLE\_PARTITIONS System View](../021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

