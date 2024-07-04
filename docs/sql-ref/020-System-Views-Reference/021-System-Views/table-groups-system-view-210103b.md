<!-- loio210103bd75191014a9ffbcb8c8e22a88 -->

# TABLE\_GROUPS System View

Provides an overview of table group relationships.



<a name="loio210103bd75191014a9ffbcb8c8e22a88___t_a_b_l_e__g_r_o_u_p_s_1struct_TABLE_GROUPS"/>

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

GROUP\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the group type.

</td>
</tr>
<tr>
<td valign="top">

SUBTYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the subtype.

</td>
</tr>
<tr>
<td valign="top">

GROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the group name.

</td>
</tr>
<tr>
<td valign="top">

IS\_GROUP\_LEAD

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Determines the leading table within a group.

</td>
</tr>
</table>



<a name="loio210103bd75191014a9ffbcb8c8e22a88__section_s3k_3xz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[TABLES System View](tables-system-view-2101973.md "Provides information about tables in the database.")

[Table Classification (Groups)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/dff79b704fb046a5af21170ee8e61c6d.html "Associated tables can be classified by a common table group.") :arrow_upper_right:

[Table Placement](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_3_QRC/en-US/22888f9344954f258284d2dd936d0d0a.html "Table classification and table placement configuration, enhanced by partitioning, build the foundation for controlling the data distribution in a SAP HANA scale-out environment.") :arrow_upper_right:

