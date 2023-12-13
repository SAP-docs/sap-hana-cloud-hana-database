<!-- loio9f8f35097e2f4b27819aaa1059d60d1f -->

# M\_TABLE\_REPLICAS System View

Provides detailed information on asynchronous/synchronous table replicas.



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

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistence volume ID.

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

Displays the schema name of the replica \(replication target\).

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

Displays the table name of the replica \(replication target\).

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(6\)

</td>
<td valign="top">

Displays the replica table type: ROW/COLUMN.

</td>
</tr>
<tr>
<td valign="top">

REPLICA\_TYPE

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the replication type: ASYNCHRONOUS/SYNCHRONOUS.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the replication source.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name of the replication source.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(6\)

</td>
<td valign="top">

Displays the source table type: ROW/COLUMN.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the volume ID of the source table.

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

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the table replication status: ENABLED, ENABLING, or DISABLED.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ENABLE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last replication enablement.

</td>
</tr>
<tr>
<td valign="top">

LAST\_DISABLE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last replication disablement.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_CODE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the last error code.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_MESSAGE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the last error message.

</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time of the last error.

</td>
</tr>
<tr>
<td valign="top">

INSERT\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the inserted record count.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the updated record count.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the deleted record count.

</td>
</tr>
<tr>
<td valign="top">

INSERT\_RETRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the insert statement retry count.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_RETRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the update statement retry count.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_RETRY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the delete statement retry count.

</td>
</tr>
</table>

**Related Information**  


[M\_TABLE\_REPLICAS\_RESET System View](m-table-replicas-reset-system-view-66d9c9d.md "Provides detailed information on asynchronous/synchronous table replicas.")

[TABLE\_REPLICAS System View](../021-System-Views/table-replicas-system-view-d2353ea.md "Provides information about replicated tables and their replicas.")

[ALTER SYSTEM \{ENABLE | DISABLE\} ALL \[ASYNCHRONOUS | SYNCHRONOUS\] TABLE REPLICAS Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-all-asynchronous-synchronous-table-replicas-stat-f948665.md "Activates or deactivates the overall replication operation of all replication tables or of asynchronous or synchronous tables only.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/33dd5d248add4b7a8c085846748b80ba.html "In a scale-out system tables (or selected columns of column store tables) may be replicated to multiple hosts. This can help to reduce network traffic when, for example, slowly-changing master data often has to be joined with tables, or partitions of tables, that are located on other hosts.") :arrow_upper_right:

[Table Replication Limitations](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/7683a6b0e9f649808cb956cd50087c5f.html "General restrictions that apply to the use of table replication.") :arrow_upper_right:

[Asynchronous Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/604ac507d6494e9eb70e5256220c5018.html "Asynchronous table replication can help reduce workload on hosts by balancing load across replica tables on worker hosts in a distributed SAP HANA system.") :arrow_upper_right:

