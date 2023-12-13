<!-- loio209dae297519101497238188403bea77 -->

# AFL\_PACKAGES System View

Provides information about available AFL packages.



<a name="loio209dae297519101497238188403bea77___a_f_l__p_a_c_k_a_g_e_s_1struct_AFL_PACKAGES"/>

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

PACKAGE\_OID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the AFL package.

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

Displays the schema name of the AFL package.

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

Displays the name of the AFL area that the AFL package belongs to.

</td>
</tr>
<tr>
<td valign="top">

PACKAGE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the AFL package.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp when the AFL package was created.

</td>
</tr>
</table>



<a name="loio209dae297519101497238188403bea77__section_z4z_bhc_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AFL\_AREAS System View](afl-areas-system-view-209d1d1.md "Provides information about available AFL areas.")

[AFL\_FUNCTIONS System View](afl-functions-system-view-209d7b2.md "Provides information about available AFL functions.")

[AFL\_FUNCTION\_PARAMETERS System View](afl-function-parameters-system-view-d1fce26.md "Provides information about parameters of AFL functions.")

[AFL\_FUNCTION\_PROPERTIES System View](afl-function-properties-system-view-209d4b7.md "Provides information about available AFL function properties.")

[AFL\_TEXTS System View](afl-texts-system-view-d1fd8aa.md "Provides information about available AFL texts.")

