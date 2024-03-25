<!-- loioaa0a92bc5b37419884144cbea92f0fcc -->

# EFFECTIVE\_MASK\_EXPRESSIONS System View

Provides information as to how data is exposed to certain users in terms of data masking.



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

ROOT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name. An equal predicate is required.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object. An equal predicate is required.

</td>
</tr>
<tr>
<td valign="top">

ROOT\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the column name. An equal predicate is required.

</td>
</tr>
<tr>
<td valign="top">

USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the user name. An equal predicate is required.

</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_USER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the session user or the owner of the definer dependent object, based on the mask mode \(DEFAULT or SESSION USER\).

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the dependent column.

</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the object at its current level.

</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name of the object at its current level.

</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type name of the object at its current level.

</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column at its current level.

</td>
</tr>
<tr>
<td valign="top">

MASK\_EXPRESSION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the mask expression string.

</td>
</tr>
<tr>
<td valign="top">

MASK\_EXPRESSION\_STATUS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the status of the applied masking: NULL, APPLIED, NOT APPLIED, SESSION USER APPLIED, or SESSION USER NOT APPLIED. The status is NOT APPLIED if the effective user has an UNMASKED privilege. The status is NULL if the specified column does not have a mask definition.

</td>
</tr>
</table>



<a name="loioaa0a92bc5b37419884144cbea92f0fcc__section_k3x_ndk_h2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

This view also requires an equal \(=\) predicate on ROOT\_SCHEMA\_NAME, ROOT\_OBJECT\_NAME, ROOT\_COLUMN\_NAME, and USER\_NAME.

**Related Information**  


[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[System Views for Verifying Users' Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

