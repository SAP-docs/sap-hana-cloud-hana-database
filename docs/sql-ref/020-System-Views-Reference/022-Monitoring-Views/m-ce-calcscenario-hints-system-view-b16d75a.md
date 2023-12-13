<!-- loiob16d75aff9b04d8b8b491a04050b69d8 -->

# M\_CE\_CALCSCENARIO\_HINTS System View

Exposes all hints that are defined in a calculation scenario.




<table>
<tr>
<th valign="top">

Column

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

Displays the schema name.

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

HINT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the hint name. For example, qo\_pop\_hints.

</td>
</tr>
<tr>
<td valign="top">

HINT\_VALUE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the hint value. For example, USE\_OLAP\_PLAN.

</td>
</tr>
</table>

**Related Information**  


[M\_CE\_CALCSCENARIOS System View](m-ce-calcscenarios-system-view-20a9c2a.md "Provides all available calculation scenarios.")

[M\_CE\_CALCSCENARIOS\_OVERVIEW System View](m-ce-calcscenarios-overview-system-view-d206937.md "Provides an overview of Calcscenarios without JSON representation.")

[M\_CE\_CALCVIEW\_DEPENDENCIES System View](m-ce-calcview-dependencies-system-view-20a9f21.md "Provides all views that are referencing a CalculationScenario.")

