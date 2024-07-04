<!-- loio20c786a175191014932ea025e0d34ba0 -->

# M\_TEMPORARY\_OBJECT\_DEPENDENCIES System View

Provides information about temporary object dependencies for transient objects.



<a name="loio20c786a175191014932ea025e0d34ba0___m__t_e_m_p_o_r_a_r_y__o_b_j_e_c_t__d_e_p_e_n_d_e_n_c_i_e_s_1struct_M_TEMPORARY_OBJECT_DEPENDENCIES"/>

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

BASE\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database name of the base object.

</td>
</tr>
<tr>
<td valign="top">

BASE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the base object.

</td>
</tr>
<tr>
<td valign="top">

BASE\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name of the base object.

</td>
</tr>
<tr>
<td valign="top">

BASE\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of base object.

</td>
</tr>
<tr>
<td valign="top">

BASE\_OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the base object.

</td>
</tr>
<tr>
<td valign="top">

BASE\_OBJECT\_IS\_TEMPORARY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the temporary property of the base object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the database name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name of the dependent object.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the dependent type.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the dependent.

</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_IS\_TEMPORARY

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the temporary property of the dependent.

</td>
</tr>
</table>

**Related Information**  


[OBJECTS System View](../021-System-Views/objects-system-view-20cbede.md "Provides information about available objects.")

[OBJECT\_DEPENDENCIES System View](../021-System-Views/object-dependencies-system-view-20cbd12.md "Provides information about the dependencies between objects, such as which views refer to a specific table.")

[Object Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

[Object Dependencies View Examples](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/38608b6773a6423986785de97d0d1ea8.html "") :arrow_upper_right:

