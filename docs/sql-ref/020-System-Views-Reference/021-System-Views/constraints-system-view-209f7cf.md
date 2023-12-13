<!-- loio209f7cf5751910149d9ce6b033d8ddce -->

# CONSTRAINTS System View

Provides information about defined constraints for tables.



<a name="loio209f7cf5751910149d9ce6b033d8ddce___c_o_n_s_t_r_a_i_n_t_s_1struct_CONSTRAINTS"/>

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

Displays the table name.

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

POSITION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the column position in this constraint.

</td>
</tr>
<tr>
<td valign="top">

CONSTRAINT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the constraint name.

</td>
</tr>
<tr>
<td valign="top">

IS\_PRIMARY\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the constraint is a primary key constraint: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_UNIQUE\_KEY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the constraint is a unique constraint: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CHECK\_CONDITION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the check condition of the check constraint.

</td>
</tr>
</table>



<a name="loio209f7cf5751910149d9ce6b033d8ddce__section_j3l_c1q_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[REFERENTIAL\_CONSTRAINTS System View](referential-constraints-system-view-20ccc0a.md "Provides information about referential constraints.")

[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[M\_TEMPORARY\_JOIN\_CONSTRAINTS System View](../022-Monitoring-Views/m-temporary-join-constraints-system-view-d21b187.md "Provides information about temporary join constraints.")

[System Limitations](../../010-SQL-Reference/system-limitations-20a7605.md "Limitations to take into consideration when administering an SAP HANA Cloud database.")

