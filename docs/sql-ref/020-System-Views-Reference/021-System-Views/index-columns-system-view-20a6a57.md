<!-- loio20a6a57e751910149887cbf423a0a16a -->

# INDEX\_COLUMNS System View

Provides information about index columns.



<a name="loio20a6a57e751910149887cbf423a0a16a___i_n_d_e_x__c_o_l_u_m_n_s_1struct_INDEX_COLUMNS"/>

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

Displays the object ID of the table.

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

Displays the index name.

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

Displays the object ID of the index.

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

Displays the type of constraint on the index: UNIQUE, NOT\_NULL\_UNIQUE, PRIMARY\_KEY.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the indexed column.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ordinal position of the indexed column.

</td>
</tr>
<tr>
<td valign="top">

ASCENDING\_ORDER

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the indexed column is in ascending order: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20a6a57e751910149887cbf423a0a16a__section_ur2_3rb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[INDEXES System View](indexes-system-view-20a7044.md "Provides information about indexes on tables.")

[CREATE INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-index-statement-data-definition-20d44b4.md "Creates an index on a table column.")

[ALTER INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-index-statement-data-definition-20d014b.md "Alters an index.")

[RENAME INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/rename-index-statement-data-definition-20fb6e1.md "Changes the name of an index.")

[DROP INDEX Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-index-statement-data-definition-20d6f4e.md "Removes an index.")

