<!-- loioa2a181f61fab41b490a12ac2d82c9306 -->

# M\_TABLE\_PERSISTENT\_MEMORY\_FILES System View

Displays the persistent memory file information for all of the tables in the database.



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

VARCHAR\(64\)

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

COLUMN\_FRAGMENT\_TYPE

</td>
<td valign="top">

VARCHAR\(16\)

</td>
<td valign="top">

Displays the column fragment type: PAGED MAIN, SINGLE MAIN, or DELTA.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_FRAGMENT\_VERSION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the column fragment version.

</td>
</tr>
<tr>
<td valign="top">

FILE\_BLOCK\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the persistent memory block identifier inside the column fragment version.

</td>
</tr>
<tr>
<td valign="top">

FILE\_NAME

</td>
<td valign="top">

VARCHAR\(256\)

</td>
<td valign="top">

Displays the persistent memory block file name.

</td>
</tr>
<tr>
<td valign="top">

FILE\_STATUS

</td>
<td valign="top">

VARCHAR\(8\)

</td>
<td valign="top">

Displays the persistent memory file status: ACTIVE/INACTIVE.

</td>
</tr>
</table>

**Related Information**  


[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[EXPORT Statement \(Data Import Export\)](../../010-SQL-Reference/012-SQL-Statements/export-statement-data-import-export-20da0be.md "Exports catalog objects.")

[Non-Heterogeneous Alter Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/non-heterogeneous-alter-partition-clauses-f7ae27c.md "Modifies the partitions of an existing table with a non-heterogeneous partitioning schema.")

[Non-Heterogeneous Create Partition Clauses](../../010-SQL-Reference/012-SQL-Statements/non-heterogeneous-create-partition-clauses-ca6a99b.md "Defines the various partitioning clauses available for non-heterogeneous partitions when creating a new table.")

[UNLOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/unload-statement-data-manipulation-20fe92a.md "Unloads the column store table from memory.")

[IMPORT Statement \(Data Import Export\)](../../010-SQL-Reference/012-SQL-Statements/import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

