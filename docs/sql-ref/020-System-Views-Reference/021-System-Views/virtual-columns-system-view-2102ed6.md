<!-- loio2102ed64751910148e60a51d6bdb83da -->

# VIRTUAL\_COLUMNS System View

Provides information about virtual columns.



<a name="loio2102ed64751910148e60a51d6bdb83da___v_i_r_t_u_a_l__c_o_l_u_m_n_s_1struct_VIRTUAL_COLUMNS"/>

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

DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the SQL data type name of the column.

</td>
</tr>
<tr>
<td valign="top">

LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the number of characterss for character types, the number of maximum digits for numeric types, the number of characters for datetime types, or the number of bytes for LOB types.

</td>
</tr>
<tr>
<td valign="top">

SCALE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

For numeric types: displays the maximum number of digits to the right of the decimal point. For time, TIMESTAMP types: displays the decimal digits to the right of the decimal point in the second's component of the data.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the remote data type name.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the remote column length.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SCALE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the remote scale.

</td>
</tr>
<tr>
<td valign="top">

IS\_INSERTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not INSERT is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UPDATABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not UPDATE is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UPSERTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not UPSERT is supported: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_SELECTABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not SELECT is supported: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio2102ed64751910148e60a51d6bdb83da__section_qk5_511_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[VIRTUAL\_COLUMN\_PROPERTIES System View](virtual-column-properties-system-view-09f9176.md "Provides the properties set on virtual table columns.")

[VIRTUAL\_TABLES System View](virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

