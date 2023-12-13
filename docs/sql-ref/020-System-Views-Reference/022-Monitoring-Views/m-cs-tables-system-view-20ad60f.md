<!-- loio20ad60f77519101498ccb610c33c3ca6 -->

# M\_CS\_TABLES System View

Provides runtime data for column tables.



<a name="loio20ad60f77519101498ccb610c33c3ca6___m__c_s__t_a_b_l_e_s_1struct_M_CS_TABLES"/>

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

MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays that the total memory size, in bytes, is the sum of memory size in the main, delta, and history parts.

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

Displays the current memory consumption, in bytes, in main. This value varies depending on the number of attributes actually loaded and includes data for open transactions.

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

Displays the current memory consumption, in bytes, in delta.

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

Displays the total paged memory size of the table.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE\_IN\_MISC

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the used memory size, in bytes, for the internal structures that are common to all columns in a table and that are not included in the MEMORY\_SIZE\_IN\_MAIN or MEMORY\_SIZE\_IN\_DELTA columns.

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

ESTIMATED\_MAX\_MEMORY\_SIZE\_IN\_TOTAL

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the estimated maximum memory consumption, in bytes, in total, for the fully loaded table \(data for open transactions is not included\).

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

Displays the last estimated memory consumption, in bytes, for the fully loaded table.

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

Displays the last time the last estimated memory consumption was calculated.

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

Displays the current number of entries in the main part of the table. This value differs from the number of visible table main rows because there are entries for modified rows that are marked as invalidated.

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

Displays the current number of entries in the table delta part. This value differs from the number of visible table delta rows because there are additional entries, such as deleted rows or updated rows. This column can contain deleted records.

</td>
</tr>
<tr>
<td valign="top">

LAST\_COMPRESSED\_RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of entries in main during the last optimize compression run.

</td>
</tr>
<tr>
<td valign="top">

MAX\_UDIV

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum table row number. This number is for internal use only.

</td>
</tr>
<tr>
<td valign="top">

MAX\_MERGE\_CID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum commit-ID of transactions for which changes were already merged into the main table.

</td>
</tr>
<tr>
<td valign="top">

MAX\_ROWID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the maximum row ID. This number is purely technical and only used internally.

</td>
</tr>
<tr>
<td valign="top">

IS\_DELTA2\_ACTIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether a second delta is used: TRUE/FALSE. During a table delta merge, updates and inserts are stored to a second delta because the first delta is locked.

</td>
</tr>
<tr>
<td valign="top">

IS\_DELTA\_LOADED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the delta part of the table is loaded: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_LOG\_DELTA

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether that currently the redo log is currently being written: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PERSISTENT\_MERGE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the new main part will be written to the disk during a table delta merge, unless requested differently: TRUE/FALSE.

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

Displays the creation time.

</td>
</tr>
<tr>
<td valign="top">

MODIFY\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the latest modify timestamp of any column store table run time data. This value is used to trigger invalidation of related translation tables used by the column store join operations.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MERGE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the point in time, in UNIX time format, of the last time the table delta part was merged into the main part.

</td>
</tr>
<tr>
<td valign="top">

LAST\_REPLAY\_LOG\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the point in time, in UNIX time format, of the last time the table log was replayed.

</td>
</tr>
<tr>
<td valign="top">

LAST\_TRUNCATION\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time the table was truncated.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONSISTENCY\_CHECK\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the last time the table consistency was checked with the CHECK\_TABLE\_CONSISTENCY procedure.

</td>
</tr>
<tr>
<td valign="top">

LAST\_CONSISTENCY\_CHECK\_ERROR\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of errors found in the last table consistency check.

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

Displays the flag to show how many columns of the table are loaded in memory: NO, PARTIALLY, and FULL. See M\_CS\_COLUMNS for each column.

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

Displays the load unit for the table: PAGE, COLUMN, and UNKNOWN.

</td>
</tr>
<tr>
<td valign="top">

READ\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of read accesses on the table or partition.

This is not the number of SELECT statements against this table. A SELECT statement may involve several read accesses.

</td>
</tr>
<tr>
<td valign="top">

WRITE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of write accesses on the table or partition.

This is not the number of DML and DDL statements against this table. A DML or DDL statement may involve several write accesses.

</td>
</tr>
<tr>
<td valign="top">

MERGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of delta merges done on the table or partition.

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

Displays the flag to indicate that the part is a replica.

</td>
</tr>
<tr>
<td valign="top">

UNUSED\_RETENTION\_PERIOD

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the unused retention period.

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

Displays whether the table is tracking commit timestamps: TRUE or FALSE.

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

Displays the persistent memory preference inferred from user-specified preferences in bottom-up manner starting from this object: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20ad60f77519101498ccb610c33c3ca6__section_zfb_tm4_qcb"/>

## Additional Information

While the counter MERGE\_COUNT counts merges of the table since the instance started, the corresponding LAST\_MERGE\_TIME timestamp persists permanently. Consequently, it is possible to see entries that have MERGE\_COUNT = 0 and LAST\_MERGE\_TIME at some TIMESTAMP in the past. Additionally, when you copy a column store table \(via CREATE COLUMN TABLE… LIKE … \) the LAST\_MERGE\_TIME of the original table gets copied, and the MERGE\_COUNT of the new table is set to 0.

**Related Information**  


[M\_CS\_COLUMNS System View](m-cs-columns-system-view-20ad197.md "Provides runtime information about columns in column tables.")

[TABLES System View](../021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

[RENAME TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-table-statement-data-definition-20fbadb.md "Changes the schema and/or the name of a table.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[TRUNCATE TABLE Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/truncate-table-statement-data-manipulation-20fe29f.md "Deletes all rows from a table or projection view.")

[DROP TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-table-statement-data-definition-20d7fd2.md "Removes a physical or virtual table from the database.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_4_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

