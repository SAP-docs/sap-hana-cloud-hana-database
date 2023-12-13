<!-- loio3b7990e15a2f4a1cbc6181e196372796 -->

# AUTHORIZATION\_TYPES System View

Provides information about object types and subtypes used by authorization object IDs.



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

TYPE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the authorization object type.

</td>
</tr>
<tr>
<td valign="top">

TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the authorization object type.

</td>
</tr>
<tr>
<td valign="top">

SUBTYPE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the authorization object subtype.

</td>
</tr>
<tr>
<td valign="top">

SUBTYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the authorization object subtype.

</td>
</tr>
</table>



<a name="loio3b7990e15a2f4a1cbc6181e196372796__section_p53_hlc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AUTHORIZATION\_GRAPH System View](authorization-graph-system-view-209e7c7.md "Provides information about authorization dependencies of complex database objects.")

