<!-- loio61d897c679e54fc38e6bd59cfa3d23dc -->

# PROCEDURE\_ROUTES System View

Provides information about the procedure being routed. This view is for internal use only.



<a name="loio61d897c679e54fc38e6bd59cfa3d23dc___p_r_o_c_e_d_u_r_e__r_o_u_t_e_s_1struct_PROCEDURE_ROUTES"/>

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

PROCEDURE\_SCHEMA



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

OBJECT\_TYPE



</td>
<td valign="top">

NVARCHAR\(13\)



</td>
<td valign="top">

Displays the object type: REMOTE\_SOURCE, VOLUME, or TABLE.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_SCHEMA



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema of the object, if applicable.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object name.



</td>
</tr>
<tr>
<td valign="top">

VOLUME\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the volume ID.



</td>
</tr>
</table>

**Related Information**  


[PROCEDURES System View](procedures-system-view-20cc87c.md "Provides information about available stored procedures.")

[PROCEDURE\_OBJECTS System View](procedure-objects-system-view-20cc4d6.md "Contains the results of the system procedure GET_PROCEDURE_OBJECTS.")

[PROCEDURE\_PARAMETERS System View](procedure-parameters-system-view-20cc6b9.md "Provides information about the stored procedure parameters.")

[PROCEDURE\_PARAMETER\_COLUMNS System View](procedure-parameter-columns-system-view-3d02842.md "Lists available columns of table parameters of stored procedures.")

[Procedures](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/d43d91578c3b42b3bacfd89aacf0d62f.html "") :arrow_upper_right:

