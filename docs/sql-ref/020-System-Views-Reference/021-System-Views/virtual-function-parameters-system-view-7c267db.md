<!-- loio7c267db48ec64462a3662cb9cd74e6ae -->

# VIRTUAL\_FUNCTION\_PARAMETERS System View

Provides information about virtual function parameters.



<a name="loio7c267db48ec64462a3662cb9cd74e6ae___m__s_q_l__p_l_a_n__c_a_c_h_e__o_v_e_r_v_i_e_w_1struct_M_SQL_PLAN_CACHE_OVERVIEW"/>

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

Displays the schema name of the function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the function.



</td>
</tr>
<tr>
<td valign="top">

FUNCTION\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the function.



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

Displays the name of the parameter.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE\_ID



</td>
<td valign="top">

INTEGER



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

Displays the length of the parameter.



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

TABLE\_TYPE\_SCHEMA



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of table type if DATA\_TYPE\_NAME is TABLE\_TYPE



</td>
</tr>
<tr>
<td valign="top">

TABLE\_TYPE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of table type if DATA\_TYPE\_NAME is TABLE\_TYPE



</td>
</tr>
<tr>
<td valign="top">

IS\_INPLACE\_TYPE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the parameter type is an inplace type: 'TRUE'/'FALSE'.



</td>
</tr>
<tr>
<td valign="top">

PARAMETER\_TYPE



</td>
<td valign="top">

NVARCHAR\(7\)



</td>
<td valign="top">

Displays the parameter mode: IN, OUT, INOUT.



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

Displays whether the parameter has a default value or not: 'TRUE'/'FALSE'.



</td>
</tr>
<tr>
<td valign="top">

IS\_NULLABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the parameter accepts a null value: 'TRUE'/'FALSE'.



</td>
</tr>
</table>

**Related Information**  


[Virtualizing Table User-Defined Functions](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/2f6c8c47650b4acebe359598b6737e6c.html "In the SAP HANA Cloud, SAP HANA database, you can create virtual table user-defined functions (TUDFs) that point to remote table user-defined functions in another SAP HANA Cloud, SAP HANA database or in an SAP HANA on-premise system.") :arrow_upper_right:

