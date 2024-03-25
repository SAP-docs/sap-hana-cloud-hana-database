<!-- loiod234b23dd2951014bec9fb46e67facfa -->

# ST\_UNITS\_OF\_MEASURE System View

Provides information about spatial units of measure.



<a name="loiod234b23dd2951014bec9fb46e67facfa___s_t__u_n_i_t_s__o_f__m_e_a_s_u_r_e_1struct_ST_UNITS_OF_MEASURE"/>

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

OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the owner name of this unit of measure.

</td>
</tr>
<tr>
<td valign="top">

UNIT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of this unit of measure.

</td>
</tr>
<tr>
<td valign="top">

UNIT\_TYPE

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the type of this unit of measure: ANGULAR/LINEAR.

</td>
</tr>
<tr>
<td valign="top">

CONVERSION\_FACTOR

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the conversion factor of this unit of measure.

</td>
</tr>
</table>



<a name="loiod234b23dd2951014bec9fb46e67facfa__section_tpc_svz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Spatial Data Types](../../010-SQL-Reference/spatial-data-types-8efe5a4.md "Spatial data types are used to store values that contain spatial data, such as points, lines, or polygons.")

[ST\_GEOMETRY\_COLUMNS System View](st-geometry-columns-system-view-d23480c.md "Provides information about spatial columns.")

[ST\_SPATIAL\_REFERENCE\_SYSTEMS System View](st-spatial-reference-systems-system-view-d23499b.md "Provides information about spatial reference systems.")

