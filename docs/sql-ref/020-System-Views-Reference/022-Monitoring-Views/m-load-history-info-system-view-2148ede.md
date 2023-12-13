<!-- loio2148ede574c742d49fa99a6b77ba9d59 -->

# M\_LOAD\_HISTORY\_INFO System View

Load history KPI description.



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

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the view name where the KPI can be found.

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

Displays the column name where the KPI can be found.

</td>
</tr>
<tr>
<td valign="top">

IS\_CUMULATIVE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the cumulative KPIs that return a relative value since the previous sample. Noncumulative KPIs return an absolute value for the current point in time.

</td>
</tr>
<tr>
<td valign="top">

SQL\_SOURCE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the equivalent SQL statement.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the KPI description.

</td>
</tr>
<tr>
<td valign="top">

SAMPLE\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the sample unit.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_HIERARCHY

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Displays the recommended display hierarchy/sorting criteria.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the recommended display name.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_UNIT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the recommended display unit.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_LINE\_COLOR

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the recommended display line color as RGB.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_LINE\_STYLE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the recommended display line style: 1=solid, 2=dotted, or 3=dashed.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_DIVIDER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the divider to convert SAMPLE\_UNIT in DISPLAY\_UNIT.

</td>
</tr>
<tr>
<td valign="top">

DISPLAY\_Y\_SCALE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Indicates that the KPIs with the same value should be shown with the same Y scale in a chart. Special value 1 is used for CPU KPIs with a fixed Y scale of 100.

</td>
</tr>
</table>

**Related Information**  


[M\_LOAD\_HISTORY\_HOST System View](m-load-history-host-system-view-3fa52ab.md "Host specific load history KPIs.")

[M\_LOAD\_HISTORY\_SERVICE System View](m-load-history-service-system-view-261022b.md "Lists service-specific load history KPIs.")

[LOAD Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/load-statement-data-manipulation-20f83c8.md "Explicitly loads column store table data into memory instead of upon first access.")

[PERSISTENCE\_HISTORY System View](../021-System-Views/persistence-history-system-view-a8cb93e.md "Records the database version history.")

