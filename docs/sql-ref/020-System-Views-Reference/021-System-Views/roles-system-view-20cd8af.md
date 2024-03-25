<!-- loio20cd8af175191014a538d0938ced7f6a -->

# ROLES System View

Shows available roles.



<a name="loio20cd8af175191014a538d0938ced7f6a___r_o_l_e_s_1struct_ROLES"/>

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

ROLE\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the schema granted to the role.

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

Displays the role name.

</td>
</tr>
<tr>
<td valign="top">

ROLE\_ID

</td>
<td valign="top">

BIGINT

</td>
<td valign="top">

Displays the role ID.

</td>
</tr>
<tr>
<td valign="top">

ROLE\_MODE

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays the local mode of the role.

</td>
</tr>
<tr>
<td valign="top">

GLOBAL\_IDENTITY

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the identity specified for a role with ROLE\_MODE GLOBAL.

</td>
</tr>
<tr>
<td valign="top">

CREATOR

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the user who created the role.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

Displays the time that the role was created.

</td>
</tr>
<tr>
<td valign="top">

COMMENTS

</td>
<td valign="top">

NVARCHAR\(5000\)

</td>
<td valign="top">

Displays the description for the specified role.

</td>
</tr>
<tr>
<td valign="top">

CONTEXT

</td>
<td valign="top">

NVARCHAR\(2048\)

</td>
<td valign="top">

Displays the context that the role is valid for.

</td>
</tr>
<tr>
<td valign="top">

ROLEGROUP\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the role group where the role belongs. The value is NULL if no assignment exists.

</td>
</tr>
</table>



<a name="loio20cd8af175191014a538d0938ced7f6a__section_b1v_g1p_dzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[CREATE ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/create-role-statement-access-control-20d4a23.md "Creates a new role.")

[REVOKE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/revoke-statement-access-control-20fc91c.md "Revokes roles or privileges for the specified objects from a user or role.")

[DROP ROLE Statement \(Access Control\)](../../010-SQL-Reference/012-SQL-Statements/drop-role-statement-access-control-20d74f7.md "Drops a role.")

[ROLE\_LDAP\_GROUPS System View](role-ldap-groups-system-view-5f1dffe.md "Shows the mapping between SAP HANA roles and LDAP groups.")

[GRANTED\_ROLES System View](granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[EFFECTIVE\_ROLES System View](effective-roles-system-view-20a3229.md "Provides the roles of the current user.")

[EFFECTIVE\_ROLE\_GRANTEES System View](effective-role-grantees-system-view-d2beddd.md "Provides information regarding the users and roles that the role is granted to.")

[Database Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[Granting and Revoking Privileges and Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/c719b2e7d9761014b9d798770c3d0958.html "To be able to grant and revoke privileges and roles to and from users and roles, the granting or revoking user must meet a number of prerequisites.") :arrow_upper_right:

