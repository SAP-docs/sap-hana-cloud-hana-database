<!-- loio20cca38775191014bf46bc83f328ee5c -->

# QUERY\_PLANS System View

Plans how to handle query execution.



<a name="loio20cca38775191014bf46bc83f328ee5c___q_u_e_r_y__p_l_a_n_s_1struct_QUERY_PLANS"/>

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

PLAN\_ID

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the plan ID.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_NAME

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the operator name.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_DETAILS

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the detailed information on operators in the query plan.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the object name.

</td>
</tr>
<tr>
<td valign="top">

SUBTREE\_COST

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the subtree cost.

</td>
</tr>
<tr>
<td valign="top">

INPUT\_CARDINALITY

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the input cardinality.

</td>
</tr>
<tr>
<td valign="top">

OUTPUT\_CARDINALITY

</td>
<td valign="top">

DOUBLE

</td>
<td valign="top">

Displays the output cardinality.

</td>
</tr>
<tr>
<td valign="top">

OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the operator ID.

</td>
</tr>
<tr>
<td valign="top">

PARENT\_OPERATOR\_ID

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the parent operator ID.

</td>
</tr>
<tr>
<td valign="top">

LEVEL

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the level.

</td>
</tr>
<tr>
<td valign="top">

POSITION

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the position.

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the timestamp.

</td>
</tr>
<tr>
<td valign="top">

HOST

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the host where the plan operator is executed.

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

Displays the port where the plan operator is executed.

</td>
</tr>
</table>



<a name="loio20cca38775191014bf46bc83f328ee5c__section_gk3_yw4_dzb"/>

## Additional Information

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Query Parameterization: BIND_AS_PARAMETER and BIND_AS_VALUE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/0b2958ee0426496f9c084c92b14993f1.html "All scalar variables used in queries of procedures, functions or anonymous blocks, are represented either as query parameters, or as constant values during query compilation. Which option shall be chosen is a decision of the optimizer.") :arrow_upper_right:

