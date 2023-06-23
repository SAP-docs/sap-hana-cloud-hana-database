<!-- loio09f9176a592c442d82830e4a51833e57 -->

# VIRTUAL\_COLUMN\_PROPERTIES System View

Provides the properties set on virtual table columns.



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

Displays the schema name of the virtual table.



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

Displays the virtual table name.



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

Displays the virtual table column name.



</td>
</tr>
<tr>
<td valign="top">

PROPERTY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the property name.



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(512\)



</td>
<td valign="top">

Displays the property value.



</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether or not the property is read-only: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[VIRTUAL\_COLUMNS System View](virtual-columns-system-view-2102ed6.md "Provides information about virtual columns.")

[VIRTUAL\_TABLES System View](virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

