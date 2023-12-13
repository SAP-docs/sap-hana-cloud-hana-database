<!-- loio2a2e83453ebf444291a7ccb9f4951017 -->

# SQLSCRIPT\_ANALYZER\_RULES System View

Provides information regarding SQLScript Code Analyzer rules.



<a name="loio2a2e83453ebf444291a7ccb9f4951017__section_kyq_d53_vhb"/>

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

RULE\_NAMESPACE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the namespace for the rule.

</td>
</tr>
<tr>
<td valign="top">

RULE\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

Displays the rule name.

</td>
</tr>
<tr>
<td valign="top">

CATEGORY

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the classification of the rule: security, consistency, performance, and so on.

</td>
</tr>
<tr>
<td valign="top">

SHORT\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the short description of the rule.

</td>
</tr>
<tr>
<td valign="top">

LONG\_DESCRIPTION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the long description containing the rule background.

</td>
</tr>
<tr>
<td valign="top">

RECOMMENDATION

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the recommendation on how to handle the rule.

</td>
</tr>
</table>



<a name="loio2a2e83453ebf444291a7ccb9f4951017__section_u4t_pvz_2zb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[SQLScript Code Analyzer](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/f7e1c7fbce6f4db49e29d7cc58b78384.html "The SQLScript Code Analyzer consists of two built-in procedures that scan CREATE FUNCTION and CREATE PROCEDURE statements and search for patterns indicating problems in code quality, security or performance.") :arrow_upper_right:

[Limitations in the SQLScript Code Analyzer](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/2c230ed67be44187907ddd38dcb61240.html "") :arrow_upper_right:

