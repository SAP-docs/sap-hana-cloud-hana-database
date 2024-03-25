<!-- loio04185884e83e4706aa732c1ab1666397 -->

# VIRTUAL\_PACKAGES System View

Provides the list of virtual packages.



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

Displays the schema name of the virtual package.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the virtual package.

</td>
</tr>
<tr>
<td valign="top">

ADAPTER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the remote source adapter.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the virtual package was created.

</td>
</tr>
<tr>
<td valign="top">

CONTENT

</td>
<td valign="top">

BLOB

</td>
<td valign="top">

Displays the content of the virtual package.

</td>
</tr>
</table>



<a name="loio04185884e83e4706aa732c1ab1666397__section_xn3_bb1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

