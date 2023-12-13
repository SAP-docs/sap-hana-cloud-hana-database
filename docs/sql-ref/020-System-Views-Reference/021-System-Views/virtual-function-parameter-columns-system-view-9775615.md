<!-- loio9775615cbd3b4fa7bb4b3f21cc70f7ac -->

# VIRTUAL\_FUNCTION\_PARAMETER\_COLUMNS System View

Provides information about virtual function parameter columns.



<a name="loio9775615cbd3b4fa7bb4b3f21cc70f7ac___m__s_q_l__p_l_a_n__c_a_c_h_e__o_v_e_r_v_i_e_w_1struct_M_SQL_PLAN_CACHE_OVERVIEW"/>

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

PARAMETER\_POSITION

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

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column in the table parameter.

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

Displays the ordinal position of the column in the table parameter.

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

Displays the data type name of the column.

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

Displays the number of chars for char types, number of max digits for numeric types, number of chars for datetime types, number of bytes for LOB types.

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

Displays the maximum number of digits to the right of the decimal point. For TIME and TIMESTAMP, displays the number of digits to the right of the decimal point in the seconds component of the value.

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



<a name="loio9775615cbd3b4fa7bb4b3f21cc70f7ac__section_rmf_1b1_fzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Virtualizing Table User-Defined Functions](https://help.sap.com/viewer/477aa413a36c4a95878460696fcc8896/2023_4_QRC/en-US/2f6c8c47650b4acebe359598b6737e6c.html "In the SAP HANA Cloud, SAP HANA database, you can create virtual table user-defined functions (TUDFs) that point to remote table user-defined functions in another SAP HANA Cloud, SAP HANA database or in an SAP HANA on-premise system.") :arrow_upper_right:

