<!-- loio20c80e27751910149630eeed4b4b577b -->

# M\_TEMPORARY\_VIEWS System View

Displays temporary views.



<a name="loio20c80e27751910149630eeed4b4b577b___m__t_e_m_p_o_r_a_r_y__v_i_e_w_s_1struct_M_TEMPORARY_VIEWS"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

</td>
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

Displays the view name.

</td>
</tr>
<tr>
<td valign="top">

VIEW\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the view.

</td>
</tr>
<tr>
<td valign="top">

IS\_READ\_ONLY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view is a read-only or an updatable view: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_CHECK\_OPTION

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether this view has an updatable view condition: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

HAS\_COLUMN\_ALIASES

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the view has a columns alias: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the definition of the view.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the description on the view.

</td>
</tr>
<tr>
<td valign="top">

IS\_COLUMN\_VIEW

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether or not this view is a column view: TRUE/FALSE

</td>
</tr>
<tr>
<td valign="top">

VIEW\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of view: ROW, OLAP, JOIN, HIERARCHY, or CALC.

</td>
</tr>
</table>

**Related Information**  


[M\_TEMPORARY\_VIEW\_COLUMNS System View](m-temporary-view-columns-system-view-20c7e97.md "Provides information about temporary view columns.")

[VIEWS System View](../021-System-Views/views-system-view-2102bf2.md "Lists available views.")

