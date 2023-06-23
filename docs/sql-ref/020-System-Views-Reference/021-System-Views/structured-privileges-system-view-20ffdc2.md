<!-- loio20ffdc2575191014b116d1b580f78870 -->

# STRUCTURED\_PRIVILEGES System View

Provides information about available structured \(analytic\) privileges.



<a name="loio20ffdc2575191014b116d1b580f78870___s_t_r_u_c_t_u_r_e_d__p_r_i_v_i_l_e_g_e_s_1struct_STRUCTURED_PRIVILEGES"/>

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

STRUCTURED\_PRIVILEGE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID of the structured privilege.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the schema name of the privilege.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the structured privilege.



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

Displays the type of restriction: CUBERESTRICTION, ACTIVITYRESTRICTION, VALIDITYRESTRICTION, or DIMENSIONRESTRICTION.



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

**Related Information**  


[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

[CREATE STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-structured-privilege-statement-access-control-622b2df.md "Creates a structured (analytic) privilege.")

[ALTER STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-structured-privilege-statement-access-control-fd40165.md "Alters a structured (analytic) privilege, replacing the existing definition of the structured privilege with the new definition.")

[DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-structured-privilege-statement-access-control-4742f57.md "Drops a structured (analytic) privilege.")

[EFFECTIVE\_STRUCTURED\_PRIVILEGES System View](effective-structured-privileges-system-view-d201952.md "Displays the structured privileges applied to an object.")

[Analytic Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/fb0f9b103d6940f28f3479b533c351e9.html "Several privilege types are used in SAP HANA (system, object, and analytic).") :arrow_upper_right:

[Managing User Privileges](https://help.sap.com/viewer/b6c0184b46cc424b9bcce8e6aae02f97/2023_2_QRC/en-US/20fc276e8f22423fb6eba66f03f541e1.html "Various privileges are required to manage remote sources, virtual tables, and linked database.") :arrow_upper_right:

