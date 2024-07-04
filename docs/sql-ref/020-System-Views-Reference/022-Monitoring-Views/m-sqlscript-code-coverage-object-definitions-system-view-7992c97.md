<!-- loio7992c975ec9d4462bff3d46df3b30942 -->

# M\_SQLSCRIPT\_CODE\_COVERAGE\_OBJECT\_DEFINITIONS System View

Provides definitions for the objects referenced in SQLScript code coverage results.



<a name="loio7992c975ec9d4462bff3d46df3b30942___q_u_e_r_y__p_l_a_n_s_1struct_QUERY_PLANS"/>

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

OBJECT\_DEFINITION\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the ID of the object definition.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_DEFINITION

</td>
<td valign="top">

NCLOB

</td>
<td valign="top">

Displays the definition of the object.

</td>
</tr>
</table>

**Related Information**  


[M\_SQLSCRIPT\_CODE\_COVERAGE\_RESULTS System View](m-sqlscript-code-coverage-results-system-view-9628091.md "Provides per-session SQLScript code coverage results.")

[SQLScript Code Coverage](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/d00c173403154434affc3ace52efd611.html "") :arrow_upper_right:

[Object Dependencies View Examples](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/38608b6773a6423986785de97d0d1ea8.html "") :arrow_upper_right:

[ALTER SYSTEM \{START | STOP\} SQLSCRIPT CODE COVERAGE Statement \(System Management\)](../../010-SQL-Reference/012-SQL-Statements/alter-system-start-stop-sqlscript-code-coverage-statement-system-management-1a40f07.md "Starts and stops a SQLScript code coverage session for functions and procedures.")

