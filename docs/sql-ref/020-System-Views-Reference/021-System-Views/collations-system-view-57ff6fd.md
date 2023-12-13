<!-- loio57ff6fdde30b40e99193eae9d14831e7 -->

# COLLATIONS System View

Provides the list of collations that can be specified in an ORDER BY clause.



<a name="loio57ff6fdde30b40e99193eae9d14831e7__section_i3j_g5c_yy"/>

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

COLLATION\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the supported collation names.

</td>
</tr>
<tr>
<td valign="top">

DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the language and region description for the collation.

</td>
</tr>
</table>



<a name="loio57ff6fdde30b40e99193eae9d14831e7__section_vvp_h3d_nzb"/>

## Additional Information

The presence of CI or AI at the end of a collation name indicates that the collation is case-insensitive or accent-insensitive, respectively \(for example, FRENCH\_AI\).



<a name="loio57ff6fdde30b40e99193eae9d14831e7__section_yvy_v5z_y2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[AUTO\_CORR Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/auto-corr-function-aggregate-e279ce4.md "Computes all autocorrelation coefficients for a given input expression and returns an array of values.")

[CROSS\_CORR Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/cross-corr-function-aggregate-b2197a4.md "Computes all cross-correlation coefficients between two given expressions.")

[DFT Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/dft-function-aggregate-fcf2041.md "Computes expressions and returns an array with specific elements.")

[FIRST\_VALUE Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/first-value-function-aggregate-034b175.md "Returns the value of the first element of an expression. This function can also be used as a window function.")

[LAST\_VALUE Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/last-value-function-aggregate-32e95b7.md "Returns the value of the last element of an expression. This function can also be used as a window function.")

[NTH\_VALUE Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/nth-value-function-aggregate-6522df9.md "Returns the value of an element at a specific position in an expression. This function can also be used as a window function.")

[SELECT Statement \(Data Manipulation\)](../../010-SQL-Reference/012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[STRING\_AGG Function \(Aggregate\)](../../010-SQL-Reference/011-SQL-Functions/string-agg-function-aggregate-a924ee1.md "Returns the concatenation string of the specified expression.")

[Window Functions and the Window Specification](../../010-SQL-Reference/011-SQL-Functions/window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

