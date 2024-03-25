<!-- loioc4d1d111b3704938b356a6ea9c95ba3d -->

# M\_ST\_GEOMETRY\_COLUMNS System View

The M\_ST\_GEOMETRY\_COLUMNS system view provides information about the spatial extent of columns containing spatial data, including the schema name, table name, column name, and the minimum and maximum values for x, y, z, and m coordinates.



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

Specifies the schema name.

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

Specifies the table name.

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

Specifies the column name.

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

Specifies the minimum x value of the spatial column data.

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

Specifies the maximum x value of the spatial column data.

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

Specifies the minimum y value of the spatial column data.

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

Specifies the maximum y value of the spatial column data.

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

Specifies the minimum z value of the spatial column data.

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

Specifies the maximum z value of the spatial column data.

</td>
</tr>
<tr>
<td valign="top">

MIN\_M

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Specifies the minimum m value of the spatial column data.

</td>
</tr>
<tr>
<td valign="top">

MAX\_M

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Specifies the maximum m value of the spatial column data.

</td>
</tr>
</table>

**Related Information**  


[Spatial Extent with SYS.M_ST_GEOMETRY_COLUMNS](https://help.sap.com/viewer/bc9e455fe75541b8a248b4c09b086cf5/2024_1_QRC/en-US/33b2ae76d374445bb17f86072039f7d4.html "You can access the extent of spatial columns by accessing the monitoring view M_ST_GEOMETRY_COLUMNS.") :arrow_upper_right:

