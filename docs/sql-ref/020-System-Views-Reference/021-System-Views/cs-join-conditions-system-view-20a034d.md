<!-- loio20a034d2751910148b6ab955080c7127 -->

# CS\_JOIN\_CONDITIONS System View

Provides join conditions for column store join views.



<a name="loio20a034d2751910148b6ab955080c7127___c_s__j_o_i_n__c_o_n_d_i_t_i_o_n_s_1struct_CS_JOIN_CONDITIONS"/>

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

JOIN\_CONDITION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the join condition name.

</td>
</tr>
<tr>
<td valign="top">

JOIN\_ORDER

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the join order number.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of column 1.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name of COLUMN\_NAME1.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME1

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of COLUMN\_NAME1.

</td>
</tr>
<tr>
<td valign="top">

ALIAS\_NUMBER1

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the alias number of TABLE\_NAME1.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_SCHEMA\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of TABEL\_NAME2.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the table name of COLUMN\_NAME2.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_NAME2

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of COLUMN\_NAME2.

</td>
</tr>
<tr>
<td valign="top">

ALIAS\_NUMBER2

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the alias number of TABLE\_NAME2.

</td>
</tr>
<tr>
<td valign="top">

CONSTRAINTS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the join constraint name.

</td>
</tr>
<tr>
<td valign="top">

JOIN\_TYPE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the join type: INNER, LEFT, RIGHT, FULL.

</td>
</tr>
<tr>
<td valign="top">

CARDINALITY

</td>
<td valign="top">

NVARCHAR\(3\)

</td>
<td valign="top">

Displays the join cardinality: 1:1, 1:n, n:1, n:n.

</td>
</tr>
</table>



<a name="loio20a034d2751910148b6ab955080c7127__section_vlk_ccq_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_TEMPORARY\_JOIN\_CONDITIONS System View](../022-Monitoring-Views/m-temporary-join-conditions-system-view-d21ad20.md "Provides information about temporary join conditions.")

[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[CS\_JOIN\_PATHS System View](cs-join-paths-system-view-20a09ec.md "Provides join paths for column store join views.")

[CS\_JOIN\_TABLES System View](cs-join-tables-system-view-20a0cc3.md "Provides information about the physical tables referred to by column store join views.")

[CS\_ALL\_COLUMNS System View](cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[M\_CS\_ALL\_COLUMNS System View](../022-Monitoring-Views/m-cs-all-columns-system-view-20acf4c.md "Provides runtime information for all columns in column tables, including internal column tables.")

[M\_CS\_ALL\_COLUMN\_STATISTICS System View](../022-Monitoring-Views/m-cs-all-column-statistics-system-view-2cb5b77.md "Provides information on how many scans and index searches were performed on any specified columns.")

[M\_CS\_COLUMNS System View](../022-Monitoring-Views/m-cs-columns-system-view-20ad197.md "Provides runtime information about columns in column tables.")

[M\_CS\_COLUMNS\_PERSISTENCE System View](../022-Monitoring-Views/m-cs-columns-persistence-system-view-14905bf.md "Provides column persistence information for column tables.")

[CS\_BO\_VIEWS System View](cs-bo-views-system-view-209fd90.md "Provides information about business object views for column store join views.")

[CS\_CONCAT\_COLUMNS System View](cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_KEY\_FIGURES System View](cs-key-figures-system-view-20a0f88.md "Provides information about the key figures defined for column store join views.")

[CS\_VIEW\_COLUMNS System View](cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[CS\_VIEW\_PARAMETERS System View](cs-view-parameters-system-view-3abb271.md "Provides a list of parameters of the objects in the SAP HANA database. Only calculation views are considered. The parameters of a view are parsed from the definition of the underlying scenario.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

[SELECT Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

