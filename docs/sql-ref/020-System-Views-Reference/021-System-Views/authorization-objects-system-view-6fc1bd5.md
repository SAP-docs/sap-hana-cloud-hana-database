<!-- loio6fc1bd5e57e04983a61396c37d0362c9 -->

# AUTHORIZATION\_OBJECTS System View

Provides information regarding authorization objects.



<a name="loio6fc1bd5e57e04983a61396c37d0362c9__section_nv3_b4t_rhb"/>

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

TYPE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the authorization object.



</td>
</tr>
<tr>
<td valign="top">

SUBTYPE\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ID of the authorization object subtype.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the object.



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

Displays the name of the schema.



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

Displays the name of the object.



</td>
</tr>
<tr>
<td valign="top">

OWNER\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the owner of the object ID.



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

READONLY



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays whether or not the object is read only.



</td>
</tr>
</table>

**Related Information**  


[AUTHORIZATION\_GRAPH System View](authorization-graph-system-view-209e7c7.md "Provides information about authorization dependencies of complex database objects.")

[AUTHORIZATION\_TYPES System View](authorization-types-system-view-3b7990e.md "Provides information about object types and subtypes used by authorization object IDs.")

[Object Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

