<!-- loio47764ebaccf84b13a3e11924f2abb716 -->

# OBJECT\_PRIVILEGES System View

Provides information about the types of objects and privileges that can be granted to those types of objects.



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

PRIVILEGE



</td>
<td valign="top">

NVARCHAR\(40\)



</td>
<td valign="top">

Displays the privilege that can be granted to this type of object.



</td>
</tr>
</table>

**Related Information**  


[Object Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

[Object Privileges (Reference)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/8978bfdfcf3b45f9acf3fdb0964d3d9c.html "Object privileges are used to allow access to and modification of database objects, such as tables and views.") :arrow_upper_right:

[Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/fb0f9b103d6940f28f3479b533c351e9.html "Several privilege types are used in SAP HANA (system, object, and analytic).") :arrow_upper_right:

[Managing User Privileges](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/20fc276e8f22423fb6eba66f03f541e1.html "Various privileges are required to manage remote sources, virtual tables, and linked database.") :arrow_upper_right:

[OBJECTS System View](objects-system-view-20cbede.md "Provides information about available objects.")

[OBJECT\_DEPENDENCIES System View](object-dependencies-system-view-20cbd12.md "Provides information about dependencies between objects, such as which views refer to a specific table.")

[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

