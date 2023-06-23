<!-- loio20cbd12e7519101489c7cfcd0f32868d -->

# OBJECT\_DEPENDENCIES System View

Provides information about dependencies between objects, such as which views refer to a specific table.



<a name="loio20cbd12e7519101489c7cfcd0f32868d___o_b_j_e_c_t__d_e_p_e_n_d_e_n_c_i_e_s_1struct_OBJECT_DEPENDENCIES"/>

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

NVARHAR\(256\)



</td>
<td valign="top">

Displays the database name of the base objects.



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

Displays the type of the base object.



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

Displays the type of the base dependency.



</td>
</tr>
<tr>
<td valign="top">

DEPENDENCY\_TYPE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the type of dependency between the base and dependent objects:

1.  Direct dependency \(for example, the view uses a table\)
2.  Indirect dependency that is referenced via direct dependency \(for example, the view references a table via another view\)
3.  SAP internal \(dependency to an implicit created object in SQLScript\)
4.  SAP internal \(dependency to an implicit created object in SQLScript\)
5.  Dependency via a referential constraint



</td>
</tr>
</table>

**Related Information**  


[OBJECTS System View](objects-system-view-20cbede.md "Provides information about available objects.")

[OBJECT\_PRIVILEGES System View](object-privileges-system-view-47764eb.md "Provides information about the types of objects and privileges that can be granted to those types of objects.")

[M\_TEMPORARY\_OBJECT\_DEPENDENCIES System View](../022-Monitoring-Views/m-temporary-object-dependencies-system-view-20c786a.md "Provides information about temporary object dependencies for transient objects.")

[Object Dependencies View Examples](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/38608b6773a6423986785de97d0d1ea8.html "") :arrow_upper_right:

[SYS.OBJECT_DEPENDENCIES](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/5ce9a6584eb84f10afbbf2b133534932.html "Dependencies between objects, for example, views that refer to a specific table") :arrow_upper_right:

[Reduce Dependencies Between Statements](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/afc236f8178546238c96a576c462e0c0.html "One of the most important methods for speeding up processing in the SAP HANA database is through massively parallelized query execution.") :arrow_upper_right:

[Object Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/d6311b15a7e74e01b3f660f7d175b318.html "Object privileges are SQL privileges that are used to allow access to and modification of database objects.") :arrow_upper_right:

