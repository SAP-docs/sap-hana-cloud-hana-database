<!-- loio7e48a105833b4a9b940263cf103cb464 -->

# LIBRARIES System View

Provides information about available public language libraries.



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

Displays the schema name of the library.

</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the library.

</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the library.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the unqualified objects in the library.

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the query string for the library.

</td>
</tr>
<tr>
<td valign="top">

LIBRARY\_TYPE

</td>
<td valign="top">

NVARCHAR\(20\)

</td>
<td valign="top">

Displays the language of the library: SQLSCRIPT, BUILTIN.

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

Displays whether the library is valid: TRUE when base objects are valid and the definition is valid. FALSE when the base objects for the library are changed or dropped.

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

Displays the time when the library was created.

</td>
</tr>
</table>



<a name="loio7e48a105833b4a9b940263cf103cb464__section_xwv_5tb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[LIBRARY\_MEMBERS System View](library-members-system-view-215c8db.md "Provides member information for SQLScript user-defined libraries.")

[CREATE LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/create-library-statement-sqlscript-62263ce.md "Creates a SQLScript user-defined library.")

[ALTER LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/alter-library-statement-sqlscript-d0b979c.md "Alters a SQLScript user-defined library.")

[DROP LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/drop-library-statement-sqlscript-d416079.md "Drops a SQLScript user-defined library.")

[Library Members](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7ed0d89b6aa84696a3ce8cf5a8517415.html "") :arrow_upper_right:

[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[Built-In Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/d1faac82ec0d4bb382ab5fef6be4c0d5.html "") :arrow_upper_right:

[Library Member Functions and Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/2fdae398c0b446d6b61b991a9e1d8c3f.html "Library member functions and variables can be used directly in SQL or expressions in SQLScript.") :arrow_upper_right:

