<!-- loio20cc0b11751910148af983830f3987be -->

# OWNERSHIP System View

Provides owner information for the objects available to the user who is querying the view.



<a name="loio20cc0b11751910148af983830f3987be___o_w_n_e_r_s_h_i_p_1struct_OWNERSHIP"/>

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

Displays the schema name of the object.

</td>
</tr>
<tr>
<td valign="top">

OWNER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the object owner.

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

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the object type.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID.

</td>
</tr>
<tr>
<td valign="top">

APPLICATION\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the application used for object creation.

</td>
</tr>
</table>



<a name="loio20cc0b11751910148af983830f3987be__section_j2q_qtb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[OBJECTS System View](objects-system-view-20cbede.md "Provides information about available objects.")

[Object Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

