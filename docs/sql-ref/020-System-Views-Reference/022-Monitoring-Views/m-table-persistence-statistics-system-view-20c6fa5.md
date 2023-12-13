<!-- loio20c6fa56751910149503fe5fcf7d8595 -->

# M\_TABLE\_PERSISTENCE\_STATISTICS System View

Provides persistence summary statistics for tables.



<a name="loio20c6fa56751910149503fe5fcf7d8595___m__t_a_b_l_e__p_e_r_s_i_s_t_e_n_c_e__s_t_a_t_i_s_t_i_c_s_1struct_M_TABLE_PERSISTENCE_STATISTICS"/>

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

DISK\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total disk size, in bytes, of all of the table parts.

</td>
</tr>
<tr>
<td valign="top">

PAGE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the total number of pages of all of the table parts.

</td>
</tr>
<tr>
<td valign="top">

BYTES\_WRITTEN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of bytes that are written to the table.

</td>
</tr>
<tr>
<td valign="top">

BYTES\_APPENDED

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of bytes that are appended to the table.

</td>
</tr>
<tr>
<td valign="top">

BYTES\_READ

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of bytes that are read from the table.

</td>
</tr>
<tr>
<td valign="top">

BYTESTREAM\_WRITTEN

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of bytes that are written to the table via a streaming interface.

</td>
</tr>
<tr>
<td valign="top">

APPEND\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times that the table was appended to.

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

Displays the number of times that the table was written to.

</td>
</tr>
<tr>
<td valign="top">

OPTIMIZE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times that the table was optimized.

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

Displays the number of times that the table was read from.

</td>
</tr>
<tr>
<td valign="top">

TRUNCATE\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times that the table was truncated.

</td>
</tr>
<tr>
<td valign="top">

COPY\_COUNT

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of times that the table was copied.

</td>
</tr>
</table>

**Related Information**  


[CREATE STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-statistics-statement-data-definition-20d5252.md "Creates data statistic objects that allow the query optimizer to make better decisions for query plans.")

[ALTER STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-statistics-statement-data-definition-c656476.md "Alters the properties of a data statistics object.")

[REFRESH STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/refresh-statistics-statement-data-definition-20fae6d.md "Specifies a column that is part of the data sources.")

[DROP STATISTICS Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-statistics-statement-data-definition-20d7c59.md "Drops user-defined data statistic objects that the query optimizer uses to make decisions for query plans.")

