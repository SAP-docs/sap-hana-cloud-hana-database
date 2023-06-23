<!-- loiod2019526d2951014b8e1af76cdd74f8e -->

# EFFECTIVE\_STRUCTURED\_PRIVILEGES System View

Displays the structured privileges applied to an object.



<a name="loiod2019526d2951014b8e1af76cdd74f8e___e_f_f_e_c_t_i_v_e__s_t_r_u_c_t_u_r_e_d__p_r_i_v_i_l_e_g_e_s_1struct_EFFECTIVE_STRUCTURED_PRIVILEGES"/>

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

ROOT\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the root schema name.



</td>
</tr>
<tr>
<td valign="top">

ROOT\_OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the object.



</td>
</tr>
<tr>
<td valign="top">

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user name.



</td>
</tr>
<tr>
<td valign="top">

USER\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the user ID.



</td>
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

OBJECT\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the object.



</td>
</tr>
<tr>
<td valign="top">

OBJECT\_OID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the object ID.



</td>
</tr>
<tr>
<td valign="top">

EFFECTIVE\_FILTER



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the filter condition applied from all structured privileges.



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

Displays the schema name of a structured privilege created for an object.



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

Displays the name of a structured privilege created for an object.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_ID



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the ID of the structured privilege.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_FILTER



</td>
<td valign="top">

NCLOB



</td>
<td valign="top">

Displays the filter condition provided by the structured privilege.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_DEFAULT\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the default schema name of the structured privilege. This schema name is used for unqualified tables and views in a complex filter.



</td>
</tr>
<tr>
<td valign="top">

STRUCTURED\_PRIVILEGE\_STATUS



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the status of a particular structured privilege: APPLIED, NOT GRANTED, NO MATCHING ATTRIBUTE, or NO FILTER VALUES FOUND.



</td>
</tr>
</table>



<a name="loiod2019526d2951014b8e1af76cdd74f8e__section_syl_zdk_h2b"/>

## Additional Information

This view requires an equal predicate on ROOT\_SCHEMA\_NAME, ROOT\_OBJECT\_NAME, and USER\_NAME.

**Related Information**  


[STRUCTURED\_PRIVILEGES System View](structured-privileges-system-view-20ffdc2.md "Provides information about available structured (analytic) privileges.")

[CREATE STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-structured-privilege-statement-access-control-622b2df.md "Creates a structured (analytic) privilege.")

[ALTER STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/alter-structured-privilege-statement-access-control-fd40165.md "Alters a structured (analytic) privilege, replacing the existing definition of the structured privilege with the new definition.")

[DROP STRUCTURED PRIVILEGE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-structured-privilege-statement-access-control-4742f57.md "Drops a structured (analytic) privilege.")

[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

[EFFECTIVE\_PRIVILEGES System View](effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[OBJECT\_PRIVILEGES System View](object-privileges-system-view-47764eb.md "Provides information about the types of objects and privileges that can be granted to those types of objects.")

[Analytic Privileges](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/db08ea0cbb571014a386f851122958b2.html "Analytic privileges grant different users access to different portions of data in the same view based on their business role. Within the definition of an analytic privilege, the conditions that control which data users see is defined using SQL.") :arrow_upper_right:

[Object Privileges (Reference)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/8978bfdfcf3b45f9acf3fdb0964d3d9c.html "Object privileges are used to allow access to and modification of database objects, such as tables and views.") :arrow_upper_right:

[System Views for Verifying Users&apos; Authorization](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

