<!-- loio6fc1bd5e57e04983a61396c37d0362c9 -->

# AUTHORIZATION\_OBJECTS System View

Provides information about authorization objects.



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



<a name="loio6fc1bd5e57e04983a61396c37d0362c9__section_uqy_2lc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AUTHORIZATION\_GRAPH System View](authorization-graph-system-view-209e7c7.md "Provides information about authorization dependencies of complex database objects.")

[AUTHORIZATION\_TYPES System View](authorization-types-system-view-3b7990e.md "Provides information about object types and subtypes used by authorization object IDs.")

[Object Privileges](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

