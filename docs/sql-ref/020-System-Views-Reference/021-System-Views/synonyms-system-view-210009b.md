<!-- loio210009ba75191014b061af7f6276da77 -->

# SYNONYMS System View

Lists available synonyms.



<a name="loio210009ba75191014b061af7f6276da77___s_y_n_o_n_y_m_s_1struct_SYNONYMS"/>

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

Displays the schema name of the synonym.

</td>
</tr>
<tr>
<td valign="top">

SYNONYM\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the synonym.

</td>
</tr>
<tr>
<td valign="top">

SYNONYM\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the synonym.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_DATABASE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database name of the referenced object.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the referenced object.

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

Displays the name of the referenced object.

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

Displays the type of the referenced object.

</td>
</tr>
<tr>
<td valign="top">

IS\_COLUMN\_OBJECT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view is a column object or not: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the synonym is valid or not: TRUE/FALSE. This value becomes FALSE when its base object is dropped.

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

Displays the creation time of the synonym.

</td>
</tr>
</table>



<a name="loio210009ba75191014b061af7f6276da77__section_x51_wvz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-synonym-statement-data-definition-20d5412.md "Creates an alternate name for a table, view, procedure, sequence or graph workspace.")

[DROP SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-synonym-statement-data-definition-20d7e17.md "Removes a synonym.")

[CREATE SCHEMA SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-schema-synonym-statement-data-definition-1b54e1f.md "Creates a schema synonym.")

[DROP SCHEMA SYNONYM Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-schema-synonym-statement-data-definition-f8ac4d9.md "Removes a schema synonym.")

[Synonyms](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/22f8edb7ab7944b3962f01007477bdd4.html "Use synonyms to create an alternative name for a virtual table or a remote table when using linked database with SAP HANA view modeling.") :arrow_upper_right:

