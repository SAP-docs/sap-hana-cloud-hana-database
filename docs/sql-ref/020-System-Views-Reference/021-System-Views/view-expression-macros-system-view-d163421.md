<!-- loiod163421608b04276bd64d152905de2e4 -->

# VIEW\_EXPRESSION\_MACROS System View

Describes the expression macros defined for views.



<a name="loiod163421608b04276bd64d152905de2e4__section_vfl_knz_fcb"/>

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

Displays the schema name for the view.

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

Displays the name of the view.

</td>
</tr>
<tr>
<td valign="top">

EXPRESSION\_MACRO\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the macro.

</td>
</tr>
<tr>
<td valign="top">

DEFINITION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the definition \(formula\) for the macro.

</td>
</tr>
</table>



<a name="loiod163421608b04276bd64d152905de2e4__section_s2k_r11_fzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[VIEWS System View](views-system-view-2102bf2.md "Lists available views.")

[VIEW\_COLUMNS System View](view-columns-system-view-21028f1.md "Lists available view columns.")

[VIEW\_PARAMETERS System View](view-parameters-system-view-45b86e8.md "Provides information about view parameters.")

[CREATE VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-view-statement-data-definition-20d5fa9.md "Creates a view on the database.")

[ALTER VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-view-statement-data-definition-3bc8951.md "Alters the definition, restrictions, or options on a view.")

[DROP VIEW Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-view-statement-data-definition-20d9c05.md "Removes a view from the database.")

[EXPRESSION\_MACRO Function \(Miscellaneous\)](../../010-SQL-Reference/011-SQL-Functions/expression-macro-function-miscellaneous-a8d1145.md "Returns aggregated results from a query.")

