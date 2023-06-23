<!-- loiod1fce26ed2951014985c9106b0460248 -->

# AFL\_FUNCTION\_PARAMETERS System View

Provides information about parameters of AFL functions.



<a name="loiod1fce26ed2951014985c9106b0460248___a_f_l__f_u_n_c_t_i_o_n__p_a_r_a_m_e_t_e_r_s_1struct_AFL_FUNCTION_PARAMETERS"/>

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

Displays the schema name of the AFL function.



</td>
</tr>
<tr>
<td valign="top">

AREA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the area name of the AFL function.



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

Displays the function name of the AFL function.



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

IO\_TYPE



</td>
<td valign="top">

NVARCHAR\(8\)



</td>
<td valign="top">

Displays the direction of the parameter.



</td>
</tr>
<tr>
<td valign="top">

DATA\_TYPE



</td>
<td valign="top">

NVARCHAR\(22\)



</td>
<td valign="top">

Displays the data type.



</td>
</tr>
<tr>
<td valign="top">

SQL\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the SQL name.



</td>
</tr>
<tr>
<td valign="top">

SQL\_DATA\_TYPE



</td>
<td valign="top">

NVARCHAR\(14\)



</td>
<td valign="top">

Displays the SQL data type.



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

RAW\_SIZE



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the parameter raw size in bytes.



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

USAGE



</td>
<td valign="top">

NVARCHAR\(32\)



</td>
<td valign="top">

Displays the usage.



</td>
</tr>
<tr>
<td valign="top">

BUSINESS\_TEXT\_ID



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the business text ID of the parameter.



</td>
</tr>
</table>

**Related Information**  


[AFL\_FUNCTIONS System View](afl-functions-system-view-209d7b2.md "Provides information about available AFL functions.")

[AFL\_PACKAGES System View](afl-packages-system-view-209dae2.md "Provides information about available AFL packages.")

[AFL\_FUNCTION\_PROPERTIES System View](afl-function-properties-system-view-209d4b7.md "Provides information about available AFL function properties.")

[AFL\_TEXTS System View](afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

[M\_AFL\_STATES System View](../022-Monitoring-Views/m-afl-states-system-view-3769f7f.md "Provides information about AFL states.")

