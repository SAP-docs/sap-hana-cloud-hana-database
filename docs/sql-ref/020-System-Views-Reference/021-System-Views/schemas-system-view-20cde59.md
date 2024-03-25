<!-- loio20cde599751910149fc2954ef99edcd6 -->

# SCHEMAS System View

Shows available schemas.



<a name="loio20cde599751910149fc2954ef99edcd6___s_c_h_e_m_a_s_1struct_SCHEMAS"/>

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

SCHEMA\_OWNER

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema owner.

</td>
</tr>
<tr>
<td valign="top">

HAS\_PRIVILEGES

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Shows if the user is the schema owner or has any privileges for the schema or any object within the schema: TRUE/FALSE.

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

Displays the creation time of the schema.

</td>
</tr>
</table>



<a name="loio20cde599751910149fc2954ef99edcd6__section_ywg_hsz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-schema-statement-data-definition-20d4eca.md "Creates a schema in the current database.")

[SET SCHEMA Statement \(Session Management\)](../../010-SQL-Reference/012-SQL-Statements/set-schema-statement-session-management-20fd550.md "Changes the default schema for the session to the specified schema.")

[RENAME SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-schema-statement-data-definition-a521980.md "Rename a schema without creating a new schema.")

[DROP SCHEMA Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-schema-statement-data-definition-20d7891.md "Removes a schema.")

[CREATE SCHEMA SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-schema-synonym-statement-data-definition-1b54e1f.md "Creates a schema synonym.")

[DROP SCHEMA SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-schema-synonym-statement-data-definition-f8ac4d9.md "Removes a schema synonym.")

[CURRENT\_OBJECT\_SCHEMA Function \(Miscellaneous\)](../../010-SQL-Reference/011-SQL-Functions/current-object-schema-function-miscellaneous-8feedda.md "Returns the current schema name when creating a view.")

[List Virtual Tables By Schema](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/c9bb5442df154095ba106ec675c91c3f.html "Display the virtual tables of a remote source by schema using the SAP HANA database explorer.") :arrow_upper_right:

