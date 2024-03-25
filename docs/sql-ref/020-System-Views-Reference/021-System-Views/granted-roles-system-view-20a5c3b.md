<!-- loio20a5c3b675191014b696cc4ea6ed8362 -->

# GRANTED\_ROLES System View

Provides information about roles granted to users or other roles.



<a name="loio20a5c3b675191014b696cc4ea6ed8362___g_r_a_n_t_e_d__r_o_l_e_s_1struct_GRANTED_ROLES"/>

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

Displays the user or role the role is granted to.

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

Displays the name of the granted role.

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



<a name="loio20a5c3b675191014b696cc4ea6ed8362__section_rw3_dpb_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[GRANT Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/grant-statement-access-control-20f674e.md "Grants various types of privileges to users and roles.")

[CREATE ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-role-statement-access-control-20d4a23.md "Creates a new role.")

[DROP ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-role-statement-access-control-20d74f7.md "Drops a role.")

[REVOKE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md "Revokes roles or privileges for the specified objects from a user or role.")

[ROLES System View](roles-system-view-20cd8af.md "Shows available roles.")

[EFFECTIVE\_ROLE\_GRANTEES System View](effective-role-grantees-system-view-d2beddd.md "Provides information regarding the users and roles that the role is granted to.")

[EFFECTIVE\_ROLES System View](effective-roles-system-view-20a3229.md "Provides the roles of the current user.")

[GRANTED\_PRIVILEGES System View](granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[Granting and Revoking Privileges and Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/c719b2e7d9761014b9d798770c3d0958.html "To be able to grant and revoke privileges and roles to and from users and roles, the granting or revoking user must meet a number of prerequisites.") :arrow_upper_right:

[System Views for Verifying Users' Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

[Database Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

