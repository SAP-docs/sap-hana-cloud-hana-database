<!-- loio82282c5cee704095bb0bbc869b9e8929 -->

# HIERARCHY\_OBJECTS System View

Provides the list of objects that hierarchy navigation functions can be run on.



<a name="loio82282c5cee704095bb0bbc869b9e8929___g_r_a_n_t_e_d__r_o_l_e_s_1struct_GRANTED_ROLES"/>

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

Displays the schema name for the hierarchy.

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

Displays the name of the hierarchy.

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

Displays the object type of the hierarchy: TABLE, VIEW, or FUNCTION.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Dispalys the object ID of the hierarchy.

</td>
</tr>
<tr>
<td valign="top">

HIERARCHY\_TYPE

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">

Describes the hierarchy's source and result structure. Possible values are RECURSIVE, LEVELED, and TEMPORAL.

</td>
</tr>
</table>



<a name="loio82282c5cee704095bb0bbc869b9e8929__section_xfb_rrb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Hierarchy Functions](../../010-SQL-Reference/011-SQL-Functions/hierarchy-functions-2969da8.md "Hierarchy functions allow you to work with hierarchical data such as tables with rows arranged in a tree or directed graph.")

[SAP HANA Cloud, SAP HANA Database Hierarchy Developer Guide](https://help.sap.com/viewer/09f734c2169c4661b1aa15c00022ab21/2024_1_QRC/en-US/a93c356d32ef4e7fbd6143b554278eab.html "This guide explains how to use the hierarchy functions that are an integral part of SAP HANA core functionality.") :arrow_upper_right:

