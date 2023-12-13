<!-- loiod23480cdd2951014bc59de575a0b05fa -->

# ST\_GEOMETRY\_COLUMNS System View

Provides information about spatial columns.



<a name="loiod23480cdd2951014bc59de575a0b05fa___s_t__g_e_o_m_e_t_r_y__c_o_l_u_m_n_s_1struct_ST_GEOMETRY_COLUMNS"/>

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

Displays the name of the schema to which the table containing the spatial column belongs.

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

Displays the name of the table containing the spatial column.

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

Displays the name of the spatial column.

</td>
</tr>
<tr>
<td valign="top">

SRS\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the numeric identifier \(SRID\) for the spatial reference system \(SRS\) associated with the spatial column.

</td>
</tr>
<tr>
<td valign="top">

SRS\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the SRS associated with the spatial column.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the spatial data type.

</td>
</tr>
<tr>
<td valign="top">

COORD\_DIMENSION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the dimension of the spatial column.

</td>
</tr>
<tr>
<td valign="top">

INTERNAL\_LAYOUT

</td>
<td valign="top">

NVARCHAR\(13\)

</td>
<td valign="top">

The internal geometry layout, either PLAIN or HILBERT CURVE. For details see the column definition and column configuration.

</td>
</tr>
<tr>
<td valign="top">

SPATIAL\_INDEX\_PREFERENCE

</td>
<td valign="top">

VARCHAR\(8\)

</td>
<td valign="top">

Displays the spatial index preference: DEFAULT, RDICT, or RTREE. For details see the column definition and the column configuration.

</td>
</tr>
<tr>
<td valign="top">

VALIDATION

</td>
<td valign="top">

NVARCHAR\(4\)

</td>
<td valign="top">

Displays the geometry validation level: NONE \(checked for bad representation\)/FULL \(checked for all known invalid representations as defined by the OGC standard\).

</td>
</tr>
<tr>
<td valign="top">

HAS\_BOUNDARY\_CHECK

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Checks whether the geometries in the column are within the SRS boundaries

</td>
</tr>
</table>



<a name="loiod23480cdd2951014bc59de575a0b05fa___r_e_o_r_g__p_l_a_n_1fulldesc_REORG_PLAN"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

Spatial columns in virtual tables are not shown in the system view ST\_GEOMETRY\_COLUMNS.

**Related Information**  


[ST\_SPATIAL\_REFERENCE\_SYSTEMS System View](st-spatial-reference-systems-system-view-d23499b.md "Provides information about spatial reference systems.")

[ST\_UNITS\_OF\_MEASURE System View](st-units-of-measure-system-view-d234b23.md "Provides information about spatial units of measure.")

[Spatial Data Types](../../010-SQL-Reference/spatial-data-types-8efe5a4.md "Spatial data types are used to store values that contain spatial data, such as points, lines, or polygons.")

[TABLE\_COLUMNS System View](table-columns-system-view-2100d33.md "Provides information about available table columns.")

[VIEW\_COLUMNS System View](view-columns-system-view-21028f1.md "Lists available view columns.")

