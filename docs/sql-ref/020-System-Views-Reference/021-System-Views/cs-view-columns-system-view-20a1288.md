<!-- loio20a12889751910149febdf53931615c9 -->

# CS\_VIEW\_COLUMNS System View

Provides information about the columns defined for column store join views.



<a name="loio20a12889751910149febdf53931615c9___c_s__v_i_e_w__c_o_l_u_m_n_s_1struct_CS_VIEW_COLUMNS"/>

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

VIEW\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the join view name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the view column name.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of table.

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

Displays the table name of column.

</td>
</tr>
<tr>
<td valign="top">

ALIAS\_NUMBER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the alias number.

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

Displays the column name.

</td>
</tr>
<tr>
<td valign="top">

JOIN\_PATH

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the join path name.

</td>
</tr>
<tr>
<td valign="top">

EXPRESSION\_FLAGS

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the expression flags.

</td>
</tr>
<tr>
<td valign="top">

EXPRESSION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the expression.

</td>
</tr>
<tr>
<td valign="top">

IS\_TEXT\_SEARCHABLE.

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is text searchable: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_FUZZY\_SEARCHABLE.

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the column is fuzzy searchable: TRUE/FALSE

</td>
</tr>
</table>



<a name="loio20a12889751910149febdf53931615c9__section_s1k_bg1_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CS\_ALL\_COLUMNS System View](cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[M\_CS\_ALL\_COLUMNS System View](../022-Monitoring-Views/m-cs-all-columns-system-view-20acf4c.md "Provides runtime information for all columns in column tables, including internal column tables.")

[M\_CS\_ALL\_COLUMN\_STATISTICS System View](../022-Monitoring-Views/m-cs-all-column-statistics-system-view-2cb5b77.md "Provides information on how many scans and index searches were performed on any specified columns.")

[M\_CS\_COLUMNS System View](../022-Monitoring-Views/m-cs-columns-system-view-20ad197.md "Provides runtime information about columns in column tables.")

[M\_CS\_COLUMNS\_PERSISTENCE System View](../022-Monitoring-Views/m-cs-columns-persistence-system-view-14905bf.md "Provides column persistence information for column tables.")

[CS\_BO\_VIEWS System View](cs-bo-views-system-view-209fd90.md "Provides information about business object views for column store join views.")

[CS\_CONCAT\_COLUMNS System View](cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_FREESTYLE\_COLUMNS System View](cs-freestyle-columns-system-view-20a0065.md "Provides freestyle search columns for column store join views.")

[CS\_JOIN\_CONDITIONS System View](cs-join-conditions-system-view-20a034d.md "Provides join conditions for column store join views.")

[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[CS\_JOIN\_PATHS System View](cs-join-paths-system-view-20a09ec.md "Provides join paths for column store join views.")

[CS\_JOIN\_TABLES System View](cs-join-tables-system-view-20a0cc3.md "Provides information about the physical tables referred to by column store join views.")

[CS\_KEY\_FIGURES System View](cs-key-figures-system-view-20a0f88.md "Provides information about the key figures defined for column store join views.")

[CS\_VIEW\_PARAMETERS System View](cs-view-parameters-system-view-3abb271.md "Provides a list of parameters of the objects in the SAP HANA database. Only calculation views are considered. The parameters of a view are parsed from the definition of the underlying scenario.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

