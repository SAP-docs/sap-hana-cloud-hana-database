<!-- loio20a9f21275191014a932f25e0022f43e -->

# M\_CE\_CALCVIEW\_DEPENDENCIES System View

Provides all views that are referencing a CalculationScenario.



<a name="loio20a9f21275191014a932f25e0022f43e___m__c_e__c_a_l_c_v_i_e_w__d_e_p_e_n_d_e_n_c_i_e_s_1struct_M_CE_CALCVIEW_DEPENDENCIES"/>

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

HOST

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the host name.

</td>
</tr>
<tr>
<td valign="top">

PORT

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the internal port.

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

Displays the schema name of the column view.

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

Displays the column view name.

</td>
</tr>
<tr>
<td valign="top">

CALCNODE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the referenced calculation node name.

</td>
</tr>
<tr>
<td valign="top">

SCENARIO\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the scenario name.

</td>
</tr>
</table>



<a name="loio20a9f21275191014a932f25e0022f43e__section_knh_k1w_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CE\_CALCSCENARIOS System View](m-ce-calcscenarios-system-view-20a9c2a.md "Provides all available calculation scenarios.")

[M\_CE\_CALCSCENARIOS\_OVERVIEW System View](m-ce-calcscenarios-overview-system-view-d206937.md "Provides an overview of Calcscenarios without JSON representation.")

[M\_CE\_CALCSCENARIO\_HINTS System View](m-ce-calcscenario-hints-system-view-b16d75a.md "Exposes all hints that are defined in a calculation scenario.")

