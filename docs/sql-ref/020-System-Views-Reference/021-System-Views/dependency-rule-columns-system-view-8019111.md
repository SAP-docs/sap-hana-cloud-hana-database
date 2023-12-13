<!-- loio8019111d0406419aa7016ba093a8f112 -->

# DEPENDENCY\_RULE\_COLUMNS System View

For internal use only. Provides a list dependency rule columns in the system.



<a name="loio8019111d0406419aa7016ba093a8f112__section_lyt_nzc_yz"/>

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

DEPENDENCY\_RULE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the dependency rule.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_RULE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the dependency rule.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the table that contains the column.

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

Displays the name of the table that contains the column.

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
</table>



<a name="loio8019111d0406419aa7016ba093a8f112__section_g22_5dq_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[DEPENDENCY\_RULES System View](dependency-rules-system-view-f102d14.md "For internal use only. Provides a list of dependency rules in the system.")

