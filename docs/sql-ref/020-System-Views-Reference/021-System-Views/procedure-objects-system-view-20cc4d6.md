<!-- loio20cc4d67751910149f099dabc6935765 -->

# PROCEDURE\_OBJECTS System View

Contains the results of the system procedure GET\_PROCEDURE\_OBJECTS.



<a name="loio20cc4d67751910149f099dabc6935765___p_r_o_c_e_d_u_r_e__o_b_j_e_c_t_s_1struct_PROCEDURE_OBJECTS"/>

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

NVARCHAR\(128\)

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

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the procedure name of the stored procedure.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the schema name of the object in the stored procedure code.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(128\)

</td>
<td valign="top">

Displays the object name of the object in the stored procedure code.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the type ID of the object in the stored procedure code.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of the object in the stored procedure code.

</td>
</tr>
<tr>
<td valign="top">

START\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the start position of the object in the stored procedure code.

</td>
</tr>
<tr>
<td valign="top">

END\_POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the end position of the object in the stored procedure code.

</td>
</tr>
</table>



<a name="loio20cc4d67751910149f099dabc6935765__section_lfb_ps4_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[PROCEDURES System View](procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

[PROCEDURE\_PARAMETERS System View](procedure-parameters-system-view-20cc6b9.md "Provides information about the stored procedure parameters.")

[PROCEDURE\_PARAMETER\_COLUMNS System View](procedure-parameter-columns-system-view-3d02842.md "Lists available columns of table parameters of stored procedures.")

[PROCEDURE\_ROUTES System View](procedure-routes-system-view-61d897c.md "Provides information about the procedure being routed. This view is for internal use only.")

[SYS.PROCEDURES](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/a7b1261516ae4166883e6bc373733de5.html "Available stored procedures") :arrow_upper_right:

