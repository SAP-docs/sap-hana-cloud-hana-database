<!-- loio20a3229a75191014a9f0893bb1ea23d5 -->

# EFFECTIVE\_ROLES System View

Provides the roles of the current user.



<a name="loio20a3229a75191014a9f0893bb1ea23d5___e_f_f_e_c_t_i_v_e__r_o_l_e_s_1struct_EFFECTIVE_ROLES"/>

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

USER\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the user for whom effective roles are shown.



</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the schema of the role for whom effective privileges are shown.



</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the principal \(user or role\) for whom effective privileges are shown.



</td>
</tr>
<tr>
<td valign="top">

PRINCIPAL\_TYPE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the type of the principal \(user or role\) for whom effective privileges are shown



</td>
</tr>
<tr>
<td valign="top">

GRANTEE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the schema of the grantee.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user or role that has the role.



</td>
</tr>
<tr>
<td valign="top">

GRANTEE\_TYPE



</td>
<td valign="top">

NVARCHAR\(4\)



</td>
<td valign="top">

Displays the grantee type: USER/ROLE.



</td>
</tr>
<tr>
<td valign="top">

GRANTOR



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the user or role group who granted the role.



</td>
</tr>
<tr>
<td valign="top">

GRANTOR\_TYPE



</td>
<td valign="top">

NVARCHAR\(10\)



</td>
<td valign="top">

Displays the grantor type: USER or ROLEGROUP.



</td>
</tr>
<tr>
<td valign="top">

ROLE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the name of the schema of the role granted.



</td>
</tr>
<tr>
<td valign="top">

ROLE\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the role granted.



</td>
</tr>
<tr>
<td valign="top">

IS\_GRANTABLE



</td>
<td valign="top">

NVARCHAR\(5\)



</td>
<td valign="top">

Displays whether the role was granted with WITH ADMIN OPTION: TRUE/FALSE.



</td>
</tr>
</table>



<a name="loio20a3229a75191014a9f0893bb1ea23d5__section_u1x_wdk_h2b"/>

## Additional Information

To search for effective \(directly or indirectly\) granted privileges and roles, respectively for a given user or role requires an equal predicate on USER\_NAME specifying an existing user name or an equal predicate on PRINCIPAL\_NAME specifying an existing user name or role name.

**Related Information**  


[EFFECTIVE\_ROLE\_GRANTEES System View](effective-role-grantees-system-view-d2beddd.md "Provides information regarding the users and roles that the role is granted to.")

[ROLES System View](roles-system-view-20cd8af.md "Shows available roles.")

[CREATE ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-role-statement-access-control-20d4a23.md "Creates a new role.")

[DROP ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-role-statement-access-control-20d74f7.md "Drops a role.")

[REVOKE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md "Revokes roles or privileges for the specified objects from a user or role.")

[GRANTED\_ROLES System View](granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[Database Roles](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[System Views for Verifying Users&apos; Authorization](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

