<!-- loio67f3a4e822a043898bf2c723e0e0f2b1 -->

# M\_SERIES\_TABLES System View

Provides statistics on the physical contents of series tables.



<a name="loio67f3a4e822a043898bf2c723e0e0f2b1___m__s_n_a_p_s_h_o_t_s_1struct_M_SNAPSHOTS"/>

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

Displays the column table name.



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

SERIES\_KEY\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of distinct series identified by the SERIES KEY columns.



</td>
</tr>
<tr>
<td valign="top">

PERIOD\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of distinct periods represented in the period column.



</td>
</tr>
<tr>
<td valign="top">

ROWS\_EQUIDISTANT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows optimized to be in a piecewise equidistant segment.



</td>
</tr>
<tr>
<td valign="top">

ROWS\_NOT\_EQUIDISTANT\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows that have not been optimized to be in a piecewise equidistant segment.



</td>
</tr>
<tr>
<td valign="top">

ROWS\_REORGANIZED\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows that have been optimized by the ALTER TABLE SERIES REORGANIZE statement.



</td>
</tr>
<tr>
<td valign="top">

ROWS\_NOT\_REORGANIZED\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the number of rows that have not been processed by the ALTER TABLE SERIES REORGANIZE statement.



</td>
</tr>
</table>

**Related Information**  


[ALTER TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-table-statement-data-definition-20d329a.md "Alters a base or temporary table. See the ALTER VIRTUAL TABLE statement for altering virtual tables.")

[SERIES\_PERIOD\_TO\_ELEMENT Function \(Series Data\)](../../010-SQL-Reference/011-SQL-Functions/series-period-to-element-function-series-data-eb21d79.md "Returns the one-based series element number that the given period value is associated with.")

