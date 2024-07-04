<!-- loiod2069373d2951014a6c5c06e5c43cf77 -->

# M\_CE\_CALCSCENARIOS\_OVERVIEW System View

Provides an overview of Calcscenarios without JSON representation.



<a name="loiod2069373d2951014a6c5c06e5c43cf77___m__c_e__c_a_l_c_s_c_e_n_a_r_i_o_s__o_v_e_r_v_i_e_w_1struct_M_CE_CALCSCENARIOS_OVERVIEW"/>

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

SCENARIO\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the scenario name.

</td>
</tr>
<tr>
<td valign="top">

IS\_PERSISTENT

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates if the calculation scenario is persistent or transient: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the creation time.

</td>
</tr>
<tr>
<td valign="top">

MEMORY\_SIZE

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the memory size of the loaded calculation scenario model in bytes.

</td>
</tr>
<tr>
<td valign="top">

COMPONENT

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the component that create the calculation scenario.

</td>
</tr>
</table>



<a name="loiod2069373d2951014a6c5c06e5c43cf77__section_kmw_21w_rbc"/>

## Permissions

Unless otherwise specified, monitoring views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all monitoring views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[M\_CE\_CALCSCENARIOS System View](m-ce-calcscenarios-system-view-20a9c2a.md "Provides all available calculation scenarios.")

[M\_CE\_CALCSCENARIO\_HINTS System View](m-ce-calcscenario-hints-system-view-b16d75a.md "Exposes all hints that are defined in a calculation scenario.")

[M\_CE\_CALCVIEW\_DEPENDENCIES System View](m-ce-calcview-dependencies-system-view-20a9f21.md "Provides all views that are referencing a CalculationScenario.")

