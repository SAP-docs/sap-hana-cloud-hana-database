<!-- loio882b8fd1c7f344e2a5bf70e215aa81ca -->

# M\_TABLE\_STATISTICS System View

Returns the table runtime statistics.



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

Displays the schema name to which the table belongs.

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

Displays the table name to be counted.

</td>
</tr>
<tr>
<td valign="top">

INSERT\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of INSERT statements for the table.

</td>
</tr>
<tr>
<td valign="top">

DELETE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of DELETE statements for the table.

</td>
</tr>
<tr>
<td valign="top">

UPDATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of UPDATE statements for the table.

</td>
</tr>
<tr>
<td valign="top">

REPLACE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the count of REPLACE statements for the table.

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

Displays the count of MERGE INTO statements for the table.

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

Displays the count of SELECT statements for the table.

</td>
</tr>
<tr>
<td valign="top">

LAST\_MODIFY\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the last INSERT, UPDATE, DELETE, or REPLACE statement was executed.

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

Displays the timestamp when the last SELECT statement was executed.

</td>
</tr>
</table>



## Additional Information

-   The M\_TABLE\_STATISTICS system view is not transactional; when a DML statement is rolled back, count values in the view remain unchanged.

-   DML statements that do not result in changes to data still increment the DML counters for the relevant tables.

-   DML-related counters and SELECT\_COUNT are only applicable to user tables.

-   Generally, when a single SELECT statement touches more than one table \(regardless of whether results are returned from those tables\), the SELECT\_COUNTER for each table touched is incremented. However, SELECT statements that are subqueries do not increment the SELECT\_COUNT counter for the tables referenced in the subquery. For example, a SELECT statement that is a subquery of an INSERT statement does not increment the SELECT\_COUNT counter.

-   Nested SELECT statements, for example in procedures, increment the SELECT counter, with one exception: for a SELECT statement in a calculation view, nested SELECT statements cannot increment the SELECT counter when nested SELECT statements are optimized.


This view has a resettable counterpart; you can see the values since the last reset in the M\_TABLE\_STATISTICS\_RESET system view. To reset the view, execute the following statement: `ALTER SYSTEM RESET MONITORING VIEW SYS.M_TABLE_STATISTICS_RESET;`.

**Related Information**  


[M\_TABLE\_STATISTICS\_RESET System View](m-table-statistics-reset-system-view-6e98780.md "Returns the table DML runtime statistics since the last reset.")

[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

[Create Statistics on a Virtual Table or Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/3992fa5a5f4f471a9f5f51d103beaa75.html "Create data statistic virtual objects that the query optimizer uses to make better decisions for query plans.") :arrow_upper_right:

[Alter Statistics on a Virtual Table or Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/518d7e0ff36b4b88adb555ac368df408.html "Alter the properties of a data statistic object for virtual tables or linked database.") :arrow_upper_right:

[Refresh Statistics on a Virtual Table or Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/bf5f385dcb684adbb122fd7e474cd438.html "Refreshes data statistic virtual objects that the query optimizer uses to make better decisions for query plans.") :arrow_upper_right:

[Drop Statistics on a Virtual Table or Linked Database](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/7c432b9a34ec4f7bbf2a1624a6b2076c.html "Drop data statistic virtual objects that the query optimizer uses to make better decisions for query plans.") :arrow_upper_right:

