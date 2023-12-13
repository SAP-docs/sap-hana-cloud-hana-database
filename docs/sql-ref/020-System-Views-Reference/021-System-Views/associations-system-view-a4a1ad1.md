<!-- loioa4a1ad108be64b45a3a4477061580483 -->

# ASSOCIATIONS System View

Provides information about associations.



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

Displays the association owner schema name.

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

Displays the association owner table or view name.

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

Displays the association owner object type.

</td>
</tr>
<tr>
<td valign="top">

ASSOCIATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the association name.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the target schema name that the association is associated with.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the target table/view name that the association is associated with.

</td>
</tr>
<tr>
<td valign="top">

TARGET\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the target object type that the association is associated with.

</td>
</tr>
<tr>
<td valign="top">

JOIN\_CONDITION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the join condition.

</td>
</tr>
<tr>
<td valign="top">

JOIN\_CARDINALITY

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays the join cardinality type.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_FILTER

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default predicate filter for columns.

</td>
</tr>
</table>



<a name="loioa4a1ad108be64b45a3a4477061580483__section_o11_htc_nzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

