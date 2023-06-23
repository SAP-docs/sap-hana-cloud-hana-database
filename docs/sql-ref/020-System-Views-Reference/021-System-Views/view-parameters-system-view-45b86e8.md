<!-- loio45b86e8cfcbb4045942d30c9c8ec8812 -->

# VIEW\_PARAMETERS System View

Provides information about view parameters.



<a name="loio45b86e8cfcbb4045942d30c9c8ec8812__section_ltp_2d1_qz"/>

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

Displays the schema name of the view.



</td>
</tr>
<tr>
<td valign="top">

VIEW\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the view.



</td>
</tr>
<tr>
<td valign="top">

VIEW\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the view.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the parameter name.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID



</td>
<td valign="top">

SMALLINT



</td>
<td valign="top">

Displays the data type ID.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the data type name.



</td>
</tr>
<tr>
<td valign="top">

LENGTH



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the parameter length in bytes.



</td>
</tr>
<tr>
<td valign="top">

SCALE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the scale of the parameter.



</td>
</tr>
<tr>
<td valign="top">

POSITION



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the ordinal position of the parameter.



</td>
</tr>
<tr>
<td valign="top">

HAS\_DEFAULT\_VALUE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the parameter has a default value or not: TRUE/FALSE.



</td>
</tr>
</table>

**Related Information**  


[VIEWS System View](views-system-view-2102bf2.md "Lists available views.")

[VIEW\_COLUMNS System View](view-columns-system-view-21028f1.md "Lists available view columns.")

[VIEW\_EXPRESSION\_MACROS System View](view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

[USER\_PARAMETERS System View](user-parameters-system-view-2102244.md "Lists all parameters and their values, which have been assigned to users in the system (using CREATE USER ... SET PARAMETER or ALTER USER ... SET PARAMETER).")

[CS\_VIEW\_PARAMETERS System View](cs-view-parameters-system-view-3abb271.md "Provides a list of parameters of the objects in the SAP HANA database. Only calculation views are considered. The parameters of a view are parsed from the definition of the underlying scenario.")

[Column View Parameter Binding](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/f1c17eb3a5b04f8b82d5908218e3fa68.html "") :arrow_upper_right:

