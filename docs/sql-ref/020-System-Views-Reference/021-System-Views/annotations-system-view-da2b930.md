<!-- loioda2b930e241147faa906c8f3056a4615 -->

# ANNOTATIONS System View

Provides information about annotations that have been added to SQL objects.



<a name="loioda2b930e241147faa906c8f3056a4615___a_f_l__t_e_x_t_s_1struct_AFL_TEXTS"/>

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

Displays the schema name of the object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of object, for example, a table.

</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the subobject, if applicable.

</td>
</tr>
<tr>
<td valign="top">

SUBOBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the type of subobject, if applicable, for example, a table column.

</td>
</tr>
<tr>
<td valign="top">

KEY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the annotation key.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the annotation key value.

</td>
</tr>
</table>



<a name="loioda2b930e241147faa906c8f3056a4615__section_ijs_b3c_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ANNOTATE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/annotate-statement-data-definition-534df83.md "Annotates SQL objects such as tables, views, columns, table functions, procedures, and parameters.")

