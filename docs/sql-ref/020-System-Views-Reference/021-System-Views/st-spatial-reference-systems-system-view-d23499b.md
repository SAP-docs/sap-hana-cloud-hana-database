<!-- loiod23499bcd2951014ad38a3bd89faf03e -->

# ST\_SPATIAL\_REFERENCE\_SYSTEMS System View

Provides information about spatial reference systems.



<a name="loiod23499bcd2951014ad38a3bd89faf03e___s_t__s_p_a_t_i_a_l__r_e_f_e_r_e_n_c_e__s_y_s_t_e_m_s_1struct_ST_SPATIAL_REFERENCE_SYSTEMS"/>

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

Displays the owner name of the spatial reference system \(SRS\).

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

Displays the numeric identifier \(SRID\) of this spatial reference system.

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

Displays the name of the spatial reference system.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_EARTH

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Indicates whether the SRS type is ROUND EARTH \(TRUE\) or PLANAR \(FALSE\).

</td>
</tr>
<tr>
<td valign="top">

AXIS\_ORDER

</td>
<td valign="top">

NVARCHAR\(12\)

</td>
<td valign="top">

Displays how the database server interprets points with regards to latitude and longitude: x/y/z/m, long/lat/z/m, lat/long/z/m.

</td>
</tr>
<tr>
<td valign="top">

SNAP\_TO\_GRID

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Defines the granularity of the grid, in the LINEAR\_UNIT\_OF\_MEASURE, that geometries are snapped to on creation.

</td>
</tr>
<tr>
<td valign="top">

TOLERANCE

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Defines the precision to use when comparing points.

</td>
</tr>
<tr>
<td valign="top">

SEMI\_MAJOR\_AXIS

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the distance from the center of the ellipsoid to the equator for a ROUND EARTH SRS.

</td>
</tr>
<tr>
<td valign="top">

SEMI\_MINOR\_AXIS

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the distance from the center of the ellipsoid to the poles for a ROUND EARTH SRS.

</td>
</tr>
<tr>
<td valign="top">

INV\_FLATTENING

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the inverse flattening used for the ellipsoid in a ROUND EARTH SRS.

</td>
</tr>
<tr>
<td valign="top">

MIN\_X

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the minimum x value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

MAX\_X

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the maximum x value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

MIN\_Y

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the minimum y value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

MAX\_Y

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the maximum y value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

MIN\_Z

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the minimum z value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

MAX\_Z

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the maximum z value allowed in coordinates.

</td>
</tr>
<tr>
<td valign="top">

ORGANIZATION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the organization that created the coordinate system used by this spatial reference system.

</td>
</tr>
<tr>
<td valign="top">

ORGANIZATION\_COORDSYS\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ID given to the coordinate system by the organization that created it.

</td>
</tr>
<tr>
<td valign="top">

SRS\_TYPE

</td>
<td valign="top">

NVARCHAR\(11\)

</td>
<td valign="top">

Displays the type of SRS as defined by the SQL/MM standard: GEOGRAPHIC, PROJECTED, or ENGINEERING.

</td>
</tr>
<tr>
<td valign="top">

LINEAR\_UNIT\_OF\_MEASURE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the linear unit of measure used by this spatial reference system.

</td>
</tr>
<tr>
<td valign="top">

ANGULAR\_UNIT\_OF\_MEASURE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the angular unit of measure used by this spatial reference system.

</td>
</tr>
<tr>
<td valign="top">

POLYGON\_FORMAT

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the orientation of the rings in a polygon: COUNTERCLOCKWISE, CLOCKWISE, or EVENODD.

</td>
</tr>
<tr>
<td valign="top">

STORAGE\_FORMAT

</td>
<td valign="top">

NVARCHAR\(8\)

</td>
<td valign="top">

Indicates whether the data is stored in normalized format \(INTERNAL\), unnormalized format \(ORIGINAL\), or both \(MIXED\).

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the WKT definition of the spatial reference system in the format defined by the OGC standard.

</td>
</tr>
<tr>
<td valign="top">

TRANSFORM\_DEFINITION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the transform definition settings for use when transforming data from this SRS to another.

</td>
</tr>
</table>



<a name="loiod23499bcd2951014ad38a3bd89faf03e__section_bdz_xvz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[ST\_GEOMETRY\_COLUMNS System View](st-geometry-columns-system-view-d23480c.md "Provides information about spatial columns.")

[ST\_UNITS\_OF\_MEASURE System View](st-units-of-measure-system-view-d234b23.md "Provides information about spatial units of measure.")

[Spatial Data Types](../../010-SQL-Reference/spatial-data-types-8efe5a4.md "Spatial data types are used to store values that contain spatial data, such as points, lines, or polygons.")

[HANA Spatial Support](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/e4672cc39b584ea1a79a134ec0b7859b.html "") :arrow_upper_right:

