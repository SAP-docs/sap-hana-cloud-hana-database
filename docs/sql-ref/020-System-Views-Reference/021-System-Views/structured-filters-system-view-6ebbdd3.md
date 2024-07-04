<!-- loio6ebbdd3869044da19ba897540a89d5c7 -->

# STRUCTURED\_FILTERS System View

Provides information about available structured filters.



<a name="loio6ebbdd3869044da19ba897540a89d5c7___s_t_r_u_c_t_u_r_e_d__p_r_i_v_i_l_e_g_e_s_1struct_STRUCTURED_PRIVILEGES"/>

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

STRUCTURED\_FILTER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the object ID of the structured filter.

</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_FILTER\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the structured filter.

</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_FILTER\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the structured filter.

</td>
</tr>
<tr>
<td valign="top">

RESTRICTION\_TYPE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the type of restriction: OBJECTS, ACTIONS, CONDITION, or DEFAULTSCHEMA.

</td>
</tr>
<tr>
<td valign="top">

DIMENSION\_ATTRIBUTE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the dimension attribute.

</td>
</tr>
<tr>
<td valign="top">

FILTER\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the number of filters needed to combine all operators/operands belonging to one filter.

</td>
</tr>
<tr>
<td valign="top">

FILTER\_TYPE

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of filter: STATIC/DYNAMIC.

</td>
</tr>
<tr>
<td valign="top">

NEGATED

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Indicates whether the operator is negated in the filter: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the type of operator: CONTAINS PATTERN, BETWEEN, EQUAL, IN, LESS THAN, LESS EQUAL, GREATER THAN, or GREATER EQUAL.

</td>
</tr>
<tr>
<td valign="top">

OPERAND\_ORDER

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the sequence of the operands per filter ID.

</td>
</tr>
<tr>
<td valign="top">

OPERAND

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the value that the operator is compared to.

</td>
</tr>
</table>



<a name="loio6ebbdd3869044da19ba897540a89d5c7__section_sbp_1wz_2zb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE STRUCTURED FILTER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/create-structured-filter-statement-data-definition-f0238ff.md "Create a structured filter to manage binding between a database object (SQL or parameterized SQL view) and static / dynamic filter condition under it.")

[ALTER STRUCTURED FILTER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/alter-structured-filter-statement-data-definition-07b14e0.md "Alter an existing a structured filter.")

[DROP STRUCUTRED FILTER Statement \(Data Definition\)](../../010-SQL-Reference/012-SQL-Statements/drop-strucutred-filter-statement-data-definition-897bc02.md "Drop an existing structured filter.")

