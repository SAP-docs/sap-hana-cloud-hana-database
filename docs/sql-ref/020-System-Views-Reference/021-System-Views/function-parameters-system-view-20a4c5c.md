<!-- loio20a4c5c17519101481f89740396d2e7d -->

# FUNCTION\_PARAMETERS System View

Provides information about parameters for functions.



<a name="loio20a4c5c17519101481f89740396d2e7d___f_u_n_c_t_i_o_n__p_a_r_a_m_e_t_e_r_s_1struct_FUNCTION_PARAMETERS"/>

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

Displays the parameter name.

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

Displays the parameter length.

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

Displays the schema name of the table type if the DATA\_TYPE\_NAME is TABLE\_TYPE.

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

Displays the name of the table type if the DATA\_TYPE\_NAME is TABLE\_TYPE.

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

Displays whether the parameter type is an inplace type: TRUE/FALSE.

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

Displays the parameter mode: IN, OUT, or INOUT.

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

Displays whether the parameter has a default value: TRUE/FALSE.

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

Displays whether the parameter accepts a NULL value: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

DEFAULT\_VALUE

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the default value of the parameter.

</td>
</tr>
</table>



<a name="loio20a4c5c17519101481f89740396d2e7d__section_gjn_w4b_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[FUNCTION\_PARAMETER\_COLUMNS System View](function-parameter-columns-system-view-81b0908.md "Provides information about columns that are available for function table parameters.")

[FUNCTIONS System View](functions-system-view-20a5023.md "Provides information about available functions.")

[Function Parameters](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/58106d8f4fb44120b76fc6fb1f4a0bcc.html "") :arrow_upper_right:

[Array Parameters for Procedures and Functions](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/dcffe459010546bd981d3b74b3798962.html "You can create procedures and functions with array parameters so that array variables or constant arrays can be passed to them.") :arrow_upper_right:

