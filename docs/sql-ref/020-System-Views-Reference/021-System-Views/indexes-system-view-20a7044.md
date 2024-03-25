<!-- loio20a7044375191014a939f50ae14306f7 -->

# INDEXES System View

Provides information about indexes on tables.



<a name="loio20a7044375191014a939f50ae14306f7___i_n_d_e_x_e_s_1struct_INDEXES"/>

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

TABLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the table where the index is on.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the table where the index is on.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the index.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID for the index.

</td>
</tr>
<tr>
<td valign="top">

INDEX\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the index type.

Row store index types: BTREE, BTREE\_UNIQUE, CPBTREE, or CPBTREE\_UNIQUE.

Column store index types: INVERTED VALUE, INVERTED VALUE UNIQUE, INVERTED HASH, INVERTED INDIVIDUAL.

</td>
</tr>
<tr>
<td valign="top">

CONSTRAINT

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the constraint on the index: UNIQUE, NOT\_NULL\_UNIQUE, or PRIMARY\_KEY.

</td>
</tr>
<tr>
<td valign="top">

BTREE\_FILL\_FACTOR

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the B-tree fill factor from 50-100.

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

Displays the time when the index was created.

</td>
</tr>
<tr>
<td valign="top">

LOAD\_UNIT

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the load unit for the index. Valid values are: COLUMN, PAGE, DEFAULT, or NULL.

</td>
</tr>
</table>



<a name="loio20a7044375191014a939f50ae14306f7__section_az1_yrb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[INDEX\_COLUMNS System View](index-columns-system-view-20a6a57.md "Provides information about index columns.")

[CREATE INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-index-statement-data-definition-20d44b4.md "Creates an index on a table column.")

[ALTER INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-index-statement-data-definition-20d014b.md "Alters an index.")

[RENAME INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-index-statement-data-definition-20fb6e1.md "Changes the name of an index.")

[DROP INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-index-statement-data-definition-20d6f4e.md "Removes an index.")

[Changing the Load Units for Indexes Using ALTER INDEX](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/02dc395617744584aa464f3e5e5ee509.html "") :arrow_upper_right:

[Using Indexes in SAP HANA NSE](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/d3c257d0a4ca40a8af5778dcb1bfea48.html "Indexes are stored on individual columns in a column store in SAP HANA Native Storage Extension (NSE), and contain the same data that is stored in the column, but sorted differently.") :arrow_upper_right:

[Index-Based Cell Access to Table Variables](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/a94ea1e47d734191be3df6c2ce5f32d6.html "") :arrow_upper_right:

