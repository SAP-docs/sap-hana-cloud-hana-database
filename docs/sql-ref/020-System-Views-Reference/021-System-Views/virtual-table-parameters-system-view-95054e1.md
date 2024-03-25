<!-- loio95054e1f35f24ab590be5a18370da9a9 -->

# VIRTUAL\_TABLE\_PARAMETERS System View

Provides a list of parameters of the virtual tables that refer to column views in a remote SAP HANA database.



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

Unit

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

 

</td>
<td valign="top">

Displays the schema name of the virtual table.

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

 

</td>
<td valign="top">

Displays the object name of the virtual table.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the name of the parameter.

</td>
</tr>
<tr>
<td valign="top">

IS\_MANDATORY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays whether a parameter is mandatory or not: TRUE/FALSE. If TRUE, the value of the parameter should be provided either by setting the default value or through the SQL query. If FALSE, setting the value of the parameter is optional.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

 

</td>
<td valign="top">

Displays the default value of the parameter. This column is set to an empty string when the parameter has no default value.

</td>
</tr>
</table>



<a name="loio95054e1f35f24ab590be5a18370da9a9__section_dyl_fb1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[VIRTUAL\_TABLES System View](virtual-tables-system-view-21031a8.md "Provides information about virtual tables.")

[CREATE VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-virtual-table-statement-data-definition-d2a0406.md "Creates a virtual table at a remote source.")

[ALTER VIRTUAL TABLE Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-virtual-table-statement-data-definition-5182698.md "Modifies a virtual table's column properties, and lets you refresh the metadata of a virtual table.")

[VIRTUAL\_TABLE\_PROPERTIES System View](virtual-table-properties-system-view-88396eb.md "Provides the properties set on virtual tables.")

[Managing Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/d16e86e414b54cd0b6facd4f6a2e7e01.html "Virtual tables point to remote tables or views in a remote source. When SQL queries are executed on a virtual table, they access the remote data as if it were stored locally.") :arrow_upper_right:

[Create a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/4ef3f55395dc47a89462b77b56d71f7f.html "Create a virtual table from the remote object of a remote source.") :arrow_upper_right:

[Delete a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/ebcb10f2c2d44b3294dfb0cadd88c396.html "Delete an existing virtual table from your schema using the SAP HANA database explorer.") :arrow_upper_right:

[List All Virtual Tables](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/f4badb298616428ba585f68d4c68daa1.html "Provides a list of all virtual tables you have privilege to.") :arrow_upper_right:

[List Virtual Tables by Schema](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/682a0b4ee20349a0b36d3d940a6efaa0.html "Display the virtual tables of a remote source by schema using SQL syntax.") :arrow_upper_right:

[Refresh a Virtual Table](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2024_1_QRC/en-US/14ea22d516634790a29c2e3676dcb9b1.html "Update a virtual table to reflect metadata changes in the corresponding remote source table using SQL syntax.") :arrow_upper_right:

[Table Parameter](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/9bd0c03743164aa7a87a93f9afb253b1.html "") :arrow_upper_right:

[Any Table Type Parameter](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/9abb5bede2ac4d47abe3311062a7eb47.html "The any table type parameter is a table parameter whose type is defined during DDL time as a wildcard and is determined later during query compilation.") :arrow_upper_right:

[Type and Length Check for Table Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/4c9b66c38d0d4cf68b38ed11c9a6b573.html "") :arrow_upper_right:

