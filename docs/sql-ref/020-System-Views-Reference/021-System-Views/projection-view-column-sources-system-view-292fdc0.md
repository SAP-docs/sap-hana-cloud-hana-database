<!-- loio292fdc0e26e84b9ea62b488a2863f914 -->

# PROJECTION\_VIEW\_COLUMN\_SOURCES System View

Provides information about available projection view columns.



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

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the view name.

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

Displays the view column name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the source table schema name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the source table name.

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the source column name.

</td>
</tr>
</table>



<a name="loio292fdc0e26e84b9ea62b488a2863f914__section_gqs_1x4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE PROJECTION VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-projection-view-statement-data-definition-e35411b.md "Creates a projection view. Projection views can be used as updatable views; insert, update, and delete triggers on projection views are supported.")

[VIEW\_COLUMNS System View](view-columns-system-view-21028f1.md "Lists available view columns.")

