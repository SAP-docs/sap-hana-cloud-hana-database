<!-- loiof3e6641e6f5b10149c43f9c510633ee7 -->

# EPM\_QUERY\_SOURCES System View

Provides information about available EPM query sources.



<a name="loiof3e6641e6f5b10149c43f9c510633ee7___e_p_m__q_u_e_r_y__s_o_u_r_c_e_s_1struct_EPM_QUERY_SOURCES"/>

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

Displays the schema name of the EPM query source.

</td>
</tr>
<tr>
<td valign="top">

QUERY\_SOURCE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the EPM query source.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the description of the EPM query source.

</td>
</tr>
<tr>
<td valign="top">

CDATA

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the definition of the EPM query source with JSON representation.

</td>
</tr>
</table>



<a name="loiof3e6641e6f5b10149c43f9c510633ee7__section_amy_vhr_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[EPM\_MODELS System View](epm-models-system-view-f3e5ebc.md "Provides information about available EPM Models.")

[M\_EPM\_SESSIONS System View](../022-Monitoring-Views/m-epm-sessions-system-view-f3f7c78.md "Provides all EPM sessions with detailed information.")

