<!-- loio209d4b7c7519101480b1fdd4883b5a3d -->

# AFL\_FUNCTION\_PROPERTIES System View

Provides information about available AFL function properties.



<a name="loio209d4b7c7519101480b1fdd4883b5a3d___a_f_l__f_u_n_c_t_i_o_n__p_r_o_p_e_r_t_i_e_s_1struct_AFL_FUNCTION_PROPERTIES"/>

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

Displays the schema of the AFL function properties.

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

Displays the area name of the AFL function properties.

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

Displays the function name of the AFL function properties.

</td>
</tr>
<tr>
<td valign="top">

KEY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the key of the AFL function properties.

</td>
</tr>
<tr>
<td valign="top">

VALUE

</td>
<td valign="top">

NVARCHAR\(1024\)

</td>
<td valign="top">

Displays the value of the AFL function properties.

</td>
</tr>
</table>



<a name="loio209d4b7c7519101480b1fdd4883b5a3d__section_jbt_rgc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AFL\_AREAS System View](afl-areas-system-view-209d1d1.md "Provides information about available AFL areas.")

[AFL\_FUNCTIONS System View](afl-functions-system-view-209d7b2.md "Provides information about available AFL functions.")

[AFL\_FUNCTION\_PARAMETERS System View](afl-function-parameters-system-view-d1fce26.md "Provides information about parameters of AFL functions.")

[AFL\_PACKAGES System View](afl-packages-system-view-209dae2.md "Provides information about available AFL packages.")

[AFL\_TEXTS System View](afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

