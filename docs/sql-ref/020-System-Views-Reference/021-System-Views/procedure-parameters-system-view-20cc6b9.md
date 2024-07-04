<!-- loio20cc6b9575191014a73bf6875843cd78 -->

# PROCEDURE\_PARAMETERS System View

Provides information about the stored procedure parameters.



<a name="loio20cc6b9575191014a73bf6875843cd78___p_r_o_c_e_d_u_r_e__p_a_r_a_m_e_t_e_r_s_1struct_PROCEDURE_PARAMETERS"/>

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

Displays the schema name of the stored procedure.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the stored procedure.

</td>
</tr>
<tr>
<td valign="top">

PROCEDURE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the stored procedure.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the parameter name.

</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the data type ID.

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

Displays the data type name.

</td>
</tr>
<tr>
<td valign="top">

LENGTH

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the parameter length.

</td>
</tr>
<tr>
<td valign="top">

SCALE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the scale of the parameter.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ordinal position of the parameter.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE\_SCHEMA

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the table type if DATA\_TYPE\_NAME is TABLE\_TYPE.

</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the table type if DATA\_TYPE\_NAME is TABLE\_TYPE.

</td>
</tr>
<tr>
<td valign="top">

IS\_INPLACE\_TYPE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the parameter type is an inplace type: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_TYPE

</td>
<td valign="top">

NVARCHAR\(7\)

</td>
<td valign="top">

Displays the parameter mode: IN, OUT, or INOUT.

</td>
</tr>
<tr>
<td valign="top">

HAS\_DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the parameter has a default value: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_NULLABLE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the parameter accepts a NULL value: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default value of the parameter.

</td>
</tr>
</table>



<a name="loio20cc6b9575191014a73bf6875843cd78__section_cdq_5r4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Procedure Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/3809c45287c44908a3d45a4db1514a55.html "") :arrow_upper_right:

[PROCEDURE\_PARAMETER\_COLUMNS System View](procedure-parameter-columns-system-view-3d02842.md "Lists available columns of table parameters of stored procedures.")

[PROCEDURES System View](procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

[PROCEDURE\_OBJECTS System View](procedure-objects-system-view-20cc4d6.md "Contains the results of the system procedure GET_PROCEDURE_OBJECTS.")

