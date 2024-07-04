<!-- loio6aff104ee1cd4e0899c0326f8f673958 -->

# VIRTUAL\_FUNCTIONS System View

Provides information about virtual functions.



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

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the schema name of the function.

</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the name of the function.

</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the function.

</td>
</tr>
<tr>
<td valign="top">

REMOTE\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the remote source name used in the function.

</td>
</tr>
<tr>
<td valign="top">

ADAPTER\_NAME

</td>
<td valign="top">

NVARCHAR \(32\)

</td>
<td valign="top">

Displays the name of the remote source adapter.

</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_CONFIGURATION

</td>
<td valign="top">

NVARCHAR \(5000\)

</td>
<td valign="top">

Displays the virtual function configuration.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the package schema name.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_NAME

</td>
<td valign="top">

NVARCHAR \(256\)

</td>
<td valign="top">

Displays the package name used by virtual functions.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR \(5\)

</td>
<td valign="top">

Displays whether the function is valid or not: TRUE/FALSE. This value becomes FALSE when its base objects are changed or dropped.

</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_USAGE\_TYPE

</td>
<td valign="top">

NVARCHAR\(6\)

</td>
<td valign="top">

Displays the usage type of the function: 'SCALAR', 'TABLE', 'AGGREGATE', or 'WINDOW'.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the owner of the function.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time.

</td>
</tr>
</table>



<a name="loio6aff104ee1cd4e0899c0326f8f673958__section_pts_x11_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[SQL Functions](../../010-SQL-Reference/011-SQL-Functions/sql-functions-20a61f2.md "Documents the built-in SQL functions that are provided with SAP HANA.")

[Virtualizing Table User-Defined Functions](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_3_QRC/en-US/2f6c8c47650b4acebe359598b6737e6c.html "In the SAP HANA Cloud, SAP HANA database, you can create virtual table user-defined functions (TUDFs) that point to remote table user-defined functions in another SAP HANA Cloud, SAP HANA database or in an SAP HANA on-premise system.") :arrow_upper_right:

