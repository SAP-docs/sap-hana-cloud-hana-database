<!-- loiof3e5ebce6f5b1014af7389a6aa764fb8 -->

# EPM\_MODELS System View

Provides information about available EPM Models.



<a name="loiof3e5ebce6f5b1014af7389a6aa764fb8___e_p_m__m_o_d_e_l_s_1struct_EPM_MODELS"/>

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

Displays the schema name of the EPM Model.

</td>
</tr>
<tr>
<td valign="top">

MODEL\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the EPM Model.

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

Displays the description of the EPM Model.

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

Displays the definition of the EPM Model with JSON representation.

</td>
</tr>
</table>



<a name="loiof3e5ebce6f5b1014af7389a6aa764fb8__section_q5t_thr_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[EPM\_QUERY\_SOURCES System View](epm-query-sources-system-view-f3e6641.md "Provides information about available EPM query sources.")

[M\_EPM\_SESSIONS System View](../022-Monitoring-Views/m-epm-sessions-system-view-f3f7c78.md "Provides all EPM sessions with detailed information.")

