<!-- loio77468df5d7cb4ba1aea71f0cfa10ed59 -->

# FULL\_SYSTEM\_INFO\_DUMPS System View

Provides the FSIDs for the current database.



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

FILE\_NAME

</td>
<td valign="top">

NVARCHAR\(512\)

</td>
<td valign="top">

Displays the file name of the collection.

</td>
</tr>
<tr>
<td valign="top">

FILE\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the file size in bytes.

</td>
</tr>
<tr>
<td valign="top">

FILE\_MTIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the date the file was modified.

</td>
</tr>
</table>



<a name="loio77468df5d7cb4ba1aea71f0cfa10ed59__section_dtg_r4b_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

