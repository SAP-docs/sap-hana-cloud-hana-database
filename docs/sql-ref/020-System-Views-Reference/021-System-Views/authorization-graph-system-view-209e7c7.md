<!-- loio209e7c7f751910149c7ca7185bb6040e -->

# AUTHORIZATION\_GRAPH System View

Provides information about authorization dependencies of complex database objects.



<a name="loio209e7c7f751910149c7ca7185bb6040e___a_u_t_h_o_r_i_z_a_t_i_o_n__g_r_a_p_h_1struct_AUTHORIZATION_GRAPH"/>

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

ROOT\_DEPENDENT\_TYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the object type ID of the root object to show as a graph.



</td>
</tr>
<tr>
<td valign="top">

ROOT\_DEPENDENT\_OBJECT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the root object to show as a graph.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_TYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the object type ID of the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_TYPE\_ID\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object type name of the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_SUBTYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the object subtype ID of the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_SUBTYPE\_ID\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object subtype name of the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OBJECT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the dependent object.



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

Displays the schema name the dependent object belongs to.



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

DEPENDENT\_OWNER\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the user owning the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user owning the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENT\_READONLY



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the read-only property of the dependent object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_TYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the object type ID of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_TYPE\_ID\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object type name of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_SUBTYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the object subtype ID of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_SUBTYPE\_ID\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object subtype name of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OBJECT\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name the underlying object belongs to.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the object name of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OWNER\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the user owning the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_OWNER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user owning the underlying object.



</td>
</tr>
<tr>
<td valign="top">

UNDERLYING\_READONLY



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the read-only property of the underlying object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_USER\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the user required to have a certain privilege on the underlying object in order to validate the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user required to have a certain privilege on the underlying object in order to validate the dependent object.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_TYPE



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the type of dependency that determines the validation semantics for dependencies sharing the same dependent objects.



</td>
</tr>
<tr>
<td valign="top">

PRIVILEGE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the privilege the dependency user is required to have on the underlying object.



</td>
</tr>
<tr>
<td valign="top">

PRIVILEGE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the privilege the dependency user is required to have on the underlying object.



</td>
</tr>
<tr>
<td valign="top">

IS\_VALID



</td>
<td valign="top">

TINYINT



</td>
<td valign="top">

Displays the current state of the dependency \(as integer\). It is set by the object validation logic and reflects missing privileges or invalidated objects: 0 - 3.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_STATUS



</td>
<td valign="top">

NVARCHAR\(40\)



</td>
<td valign="top">

Displays the current state of a privilege for the dependent object: INVALID, NOT AUTHORIZED, AUTHORIZED NON GRANTABLE, or AUTHORIZED GRANTABLE.



</td>
</tr>
<tr>
<td valign="top">

AVAILABLE\_PRIVILEGES



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the current state of a privilege on upper node \(dependent object\): INVALID, NOT GRANTABLE, or GRANTABLE.



</td>
</tr>
</table>



<a name="loio209e7c7f751910149c7ca7185bb6040e__section_xlt_3dk_h2b"/>

## Additional Information

This view requires an equal to predicate on ROOT\_DEPENDENT\_TYPE\_ID and ROOT\_DEPENDENT\_OBJECT\_ID.

**Related Information**  


[AUTHORIZATION\_TYPES System View](authorization-types-system-view-3b7990e.md "Provides information about object types and subtypes used by authorization object IDs.")

