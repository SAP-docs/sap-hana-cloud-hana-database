<!-- loio20c7689a75191014ad52c1beb40ce2d2 -->

# M\_TABLES System View

Provides information on row and column tables.



<a name="loio20c7689a75191014ad52c1beb40ce2d2___m__t_a_b_l_e_s_1struct_M_TABLES"/>

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

RECORD\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of records in this table.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the allocated memory size for fixed-size and variable-size part in bytes.

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

Displays the type of the table: ROW, COLUMN, or COLLECTION.

</td>
</tr>
<tr>
<td valign="top">

IS\_PARTITIONED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is partitioned: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_REPLICATED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is replicated: TRUE/FALSE.

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

Displays whether table is tracking commit timestamps: TRUE/FALSE.

</td>
</tr>
</table>

**Related Information**  


[TABLES System View](../021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[LOCK TABLE Statement \(Transaction Management\)](../../010-SQL-Reference/012-SQL-Statements/lock-table-statement-transaction-management-20f88d8.md "Acquires an exclusive lock for a table.")

[RENAME TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-table-statement-data-definition-20fbadb.md "Changes the schema and/or the name of a table.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[TRUNCATE TABLE Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/truncate-table-statement-data-manipulation-20fe29f.md "Deletes all rows from a table or projection view.")

[DROP TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-table-statement-data-definition-20d7fd2.md "Removes a physical or virtual table from the database.")

[Managing Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/68554490aee94885ba31611489a04992.html "The SAP HANA database stores data in memory in tables, organized in columns, and partitions, distributed among multiple servers.") :arrow_upper_right:

