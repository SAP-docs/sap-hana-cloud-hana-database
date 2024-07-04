<!-- loio1416264774bb45f69944bc8bbfe16491 -->

# M\_REMOTE\_TABLE\_REPLICAS System View

Provides remote table replication information.



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

VOLUME\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistent volume ID of the server.

</td>
</tr>
<tr>
<td valign="top">

IS\_SOURCE\_SYSTEM

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether or not the system has a source table: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name on the replication system.

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

Displays the schema name of the replication table.

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

Displays the table name of the replication table.

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

Displays the Table OID of the replication table.

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

Displays the type of replication table: ROW/COLUMN.

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

Displays the replication type: SYNCHRONOUS/ASYNCHRONOUS.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the remote source name on the source system.

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

Displays the schema name of the source table.

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

Displays the table name of the source table.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the table OID of a source table.

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

REPLICATION\_STATUS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the replication status: ENABLING, ENABLED, DISABLED, or SUSPENDED.

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

Displays the timestamp when the table was last enabled.

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

Displays the timestamp when the table was last disabled.

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

Displays the last error code number.

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

Displays the timestamp when the last error occurred.

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

Displays the number of inserted records.

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

Displays the number of updated records.

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

Displays the number of deleted records.

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

Displays the number of retries to insert.

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

Displays the number of retries to update.

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

Displays the number of retries to delete.

</td>
</tr>
</table>

**Related Information**  


[TABLE\_REPLICAS System View](../021-System-Views/table-replicas-system-view-d2353ea.md "Provides information about replicated tables and their replicas.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[ALTER SYSTEM \{ENABLE | DISABLE\} ALL \[ASYNCHRONOUS | SYNCHRONOUS\] TABLE REPLICAS Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-enable-disable-all-asynchronous-synchronous-table-replicas-stat-f948665.md "Activates or deactivates the overall replication operation of all replication tables or of asynchronous or synchronous tables only.")

[Table Replication](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/33dd5d248add4b7a8c085846748b80ba.html "In a scale-out system tables (or selected columns of column store tables) may be replicated to multiple hosts. This can help to reduce network traffic when, for example, slowly-changing master data often has to be joined with tables, or partitions of tables, that are located on other hosts.") :arrow_upper_right:

