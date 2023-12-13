<!-- loio20a9c2a175191014b943cc586ea80d5a -->

# M\_CE\_CALCSCENARIOS System View

Provides all available calculation scenarios.



<a name="loio20a9c2a175191014b943cc586ea80d5a___m__c_e__c_a_l_c_s_c_e_n_a_r_i_o_s_1struct_M_CE_CALCSCENARIOS"/>

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

Displays the internal port number.

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

Indicates if the calculation scenario is persistent or transient: TRUE or FALSE.

</td>
</tr>
<tr>
<td valign="top">

FLAGS

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the calculation scenario flags.

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

Displays the component that created the calculation scenario.

</td>
</tr>
<tr>
<td valign="top">

SCENARIO\_VERSION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the scenario version of the calculation scenario.

</td>
</tr>
<tr>
<td valign="top">

JSON

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the JSON string representing the calculation scenario.

</td>
</tr>
</table>

**Related Information**  


[M\_CE\_CALCSCENARIOS\_OVERVIEW System View](m-ce-calcscenarios-overview-system-view-d206937.md "Provides an overview of Calcscenarios without JSON representation.")

[M\_CE\_CALCSCENARIO\_HINTS System View](m-ce-calcscenario-hints-system-view-b16d75a.md "Exposes all hints that are defined in a calculation scenario.")

[M\_CE\_CALCVIEW\_DEPENDENCIES System View](m-ce-calcview-dependencies-system-view-20a9f21.md "Provides all views that are referencing a CalculationScenario.")

