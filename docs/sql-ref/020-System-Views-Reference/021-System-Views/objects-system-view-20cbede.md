<!-- loio20cbede275191014ba0b8504decb8e21 -->

# OBJECTS System View

Provides information about available objects.



<a name="loio20cbede275191014ba0b8504decb8e21___o_b_j_e_c_t_s_1struct_OBJECTS"/>

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

OBJECT\_CATEGORY

</td>
<td valign="top">

NVARCHAR\(1\)

</td>
<td valign="top">

Displays the object category of the object. The default is NULL.

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

Displays the schema name of the object.

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
</table>



<a name="loio20cbede275191014ba0b8504decb8e21__section_p4w_rtb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[OBJECT\_DEPENDENCIES System View](object-dependencies-system-view-20cbd12.md "Provides information about the dependencies between objects, such as which views refer to a specific table.")

[OBJECT\_PRIVILEGES System View](object-privileges-system-view-47764eb.md "Provides information about the types of objects and privileges that can be granted to those types of objects.")

[M\_OBJECT\_LOCKS System View](../022-Monitoring-Views/m-object-locks-system-view-20b66f9.md "Provides the status of currently acquired locks on objects with detailed information such as lock acquisition time and lock mode.")

[M\_OBJECT\_LOCK\_STATISTICS System View](../022-Monitoring-Views/m-object-lock-statistics-system-view-20b611c.md "Provides lock contention statistics, including lock wait count, wait time, and failed count, for each object.")

[M\_OBJECT\_LOCK\_STATISTICS\_RESET System View](../022-Monitoring-Views/m-object-lock-statistics-reset-system-view-20b644f.md "Provides lock contention statistics, including lock wait count, wait time, and failed count for each object since the last reset.")

[Managing Memory by Object Usage](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/2024_1_QRC/en-US/815fd19868d84c13962852faa3b1ee85.html "You can use the Unused Retention Period feature to automatically unload objects from memory which are not being used.") :arrow_upper_right:

[M\_MEMORY\_OBJECTS System View](../022-Monitoring-Views/m-memory-objects-system-view-20b4e47.md "Returns memory object statistics.")

