<!-- loio20c7c6ce75191014b99db76065ee3949 -->

# M\_TEMPORARY\_TABLES System View

Provides information about temporary tables.



<a name="loio20c7c6ce75191014b99db76065ee3949___m__t_e_m_p_o_r_a_r_y__t_a_b_l_e_s_1struct_M_TEMPORARY_TABLES"/>

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

TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the comment on the table.

</td>
</tr>
<tr>
<td valign="top">

FIXED\_PART\_SIZE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the fixed-size part of the record in bytes.

</td>
</tr>
<tr>
<td valign="top">

CONNECTION\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the anchor global session ID \(anchor connection ID\).

</td>
</tr>
<tr>
<td valign="top">

STATEMENT\_ID

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the statement ID of the CREATE statement.

</td>
</tr>
<tr>
<td valign="top">

RECORD\_COUNT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the record count.

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

Displays the memory consumed by the table in bytes.

</td>
</tr>
<tr>
<td valign="top">

IS\_LOGGED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether logging is enabled for the table: TRUE/FALSE.

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

IS\_INSERT\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is an insert only table: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_TEMPORARY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table is a temporary table: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

TEMPORARY\_TABLE\_TYPE

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the temporary table type.

</td>
</tr>
<tr>
<td valign="top">

IS\_USER\_DEFINED\_TYPE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the user defined a table type: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PRELOAD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the table uses preloading: TRUE/FALSE. This is only valid for column store tables.

</td>
</tr>
<tr>
<td valign="top">

IS\_SYSTEM\_TABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Returns TRUE if the table's schema is SYS, or if the table schema or name starts with \_SYS\_.

</td>
</tr>
</table>

**Related Information**  


[CREATE TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

[M\_TEMPORARY\_TABLE\_COLUMNS System View](m-temporary-table-columns-system-view-20c7a2c.md "Provides information about temporary table columns.")

[TABLES System View](../021-System-Views/tables-system-view-2101973.md "Provides information about tables in the database.")

[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[Managing Tables](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/68554490aee94885ba31611489a04992.html "The SAP HANA database stores data in memory in tables, organized in columns, and partitions, distributed among multiple servers.") :arrow_upper_right:

[Handling Temporary Data](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/cffa9243511a4858882de2aa398a4899.html "") :arrow_upper_right:

