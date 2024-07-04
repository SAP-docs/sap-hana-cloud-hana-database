<!-- loio20aaa76a751910148bcd897c5b5827f4 -->

# M\_CE\_PLE\_CALCSCENARIOS System View

Provides all available calculation scenarios created by the PlanningEngine.



<a name="loio20aaa76a751910148bcd897c5b5827f4___m__c_e__p_l_e__c_a_l_c_s_c_e_n_a_r_i_o_s_1struct_M_CE_PLE_CALCSCENARIOS"/>

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

Displays the schema name of calculation scenario.

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

Displays the calculation scenario name.

</td>
</tr>
</table>



<a name="loio20aaa76a751910148bcd897c5b5827f4__section_ynj_jbw_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CE\_CALCSCENARIOS System View](m-ce-calcscenarios-system-view-20a9c2a.md "Provides all available calculation scenarios.")

[M\_CE\_CALCSCENARIOS\_OVERVIEW System View](m-ce-calcscenarios-overview-system-view-d206937.md "Provides an overview of Calcscenarios without JSON representation.")

[M\_CE\_CALCSCENARIO\_HINTS System View](m-ce-calcscenario-hints-system-view-b16d75a.md "Exposes all hints that are defined in a calculation scenario.")

