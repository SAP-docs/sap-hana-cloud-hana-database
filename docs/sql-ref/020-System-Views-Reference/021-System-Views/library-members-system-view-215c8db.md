<!-- loio215c8dbd140a4f0fa0c427b53e1a6a68 -->

# LIBRARY\_MEMBERS System View

Provides member information for SQLScript user-defined libraries.



<a name="loio215c8dbd140a4f0fa0c427b53e1a6a68__section_grk_yrf_scb"/>

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

MEMBER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the library member.

</td>
</tr>
<tr>
<td valign="top">

MEMBER\_TYPE

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the member type: VARIABLE, PROCEDURE, or FUNCTION.

</td>
</tr>
<tr>
<td valign="top">

ACCESS\_MODE

</td>
<td valign="top">

NVARCHAR\(9\)

</td>
<td valign="top">

Displays the access mode of the library member:

-   PUBLIC when the member is accessible without restriction.
-   PRIVATE when the member is accessible within the library.



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

Displays the definition of the library member.

</td>
</tr>
<tr>
<td valign="top">

PRAGMAS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the SQLScript user-defined test library pragmas.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the comments defined on user-defined libraries and members.

</td>
</tr>
</table>



<a name="loio215c8dbd140a4f0fa0c427b53e1a6a68__section_pfh_ntb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[LIBRARIES System View](libraries-system-view-7e48a10.md "Provides information about available public language libraries.")

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/create-library-statement-sqlscript-62263ce.md "Creates a SQLScript user-defined library.")

[ALTER LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/alter-library-statement-sqlscript-d0b979c.md "Alters a SQLScript user-defined library.")

[DROP LIBRARY Statement \(SQLScript\)](../../010-SQL-Reference/012-SQL-Statements/drop-library-statement-sqlscript-d416079.md "Drops a SQLScript user-defined library.")

[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[Library Members](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7ed0d89b6aa84696a3ce8cf5a8517415.html "") :arrow_upper_right:

[Built-In Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/d1faac82ec0d4bb382ab5fef6be4c0d5.html "") :arrow_upper_right:

[Library Member Functions and Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/2fdae398c0b446d6b61b991a9e1d8c3f.html "Library member functions and variables can be used directly in SQL or expressions in SQLScript.") :arrow_upper_right:

