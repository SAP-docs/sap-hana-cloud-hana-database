<!-- loio20a09ec275191014af78b3ec799bf038 -->

# CS\_JOIN\_PATHS System View

Provides join paths for column store join views.



<a name="loio20a09ec275191014af78b3ec799bf038___c_s__j_o_i_n__p_a_t_h_s_1struct_CS_JOIN_PATHS"/>

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

JOIN\_PATH\_NAME



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

JOIN\_CONDITIONS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the comma separated list of join conditions.



</td>
</tr>
<tr>
<td valign="top">

JOIN\_CONSTRAINTS



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the comma separated list of join constraints.



</td>
</tr>
</table>

**Related Information**  


[CS\_JOIN\_CONSTRAINTS System View](cs-join-constraints-system-view-20a06e5.md "Provides join constraints for column store join views.")

[CS\_JOIN\_CONDITIONS System View](cs-join-conditions-system-view-20a034d.md "Provides join conditions for column store join views.")

[CS\_JOIN\_TABLES System View](cs-join-tables-system-view-20a0cc3.md "Provides information about the physical tables referred to by column store join views.")

[M\_TEMPORARY\_JOIN\_CONSTRAINTS System View](../022-Monitoring-Views/m-temporary-join-constraints-system-view-d21b187.md "Provides information about temporary join constraints.")

[CS\_ALL\_COLUMNS System View](cs-all-columns-system-view-813f1ae.md "Provides information from all columns of column tables, including internal ones.")

[CS\_BO\_VIEWS System View](cs-bo-views-system-view-209fd90.md "Provides information about business object views for column store join views.")

[CS\_CONCAT\_COLUMNS System View](cs-concat-columns-system-view-02fb9ca.md "Provides information on concat columns in the database.")

[CS\_FREESTYLE\_COLUMNS System View](cs-freestyle-columns-system-view-20a0065.md "Provides freestyle search columns for column store join views.")

[CS\_KEY\_FIGURES System View](cs-key-figures-system-view-20a0f88.md "Provides information about the key figures defined for column store join views.")

[CS\_VIEW\_COLUMNS System View](cs-view-columns-system-view-20a1288.md "Provides information about the columns defined for column store join views.")

[CS\_VIEW\_PARAMETERS System View](cs-view-parameters-system-view-3abb271.md "Provides a list of parameters of the objects in the SAP HANA database. Only calculation views are considered. The parameters of a view are parsed from the definition of the underlying scenario.")

[Memory Management in the Column Store](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2023_2_QRC/en-US/bd6e6be8bb5710149e34e14608e07b76.html "The column store is the part of the SAP HANA database that manages data organized in columns in memory. Tables created as column tables are stored here.") :arrow_upper_right:

