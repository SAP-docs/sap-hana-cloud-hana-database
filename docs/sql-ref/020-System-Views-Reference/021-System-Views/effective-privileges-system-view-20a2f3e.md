<!-- loio20a2f3ea75191014a4c1d9b0859b9917 -->

# EFFECTIVE\_PRIVILEGES System View

Provides the privileges of the specified user.



<a name="loio20a2f3ea75191014a4c1d9b0859b9917___e_f_f_e_c_t_i_v_e__p_r_i_v_i_l_e_g_e_s_1struct_EFFECTIVE_PRIVILEGES"/>

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

Displays the name of the user for whom effective privileges are shown.

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

Displays the type of the principal \(user or role\) for whom effective privileges are shown.

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

Displays the user or role that has the privilege.

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

GRANTOR\_SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the schema name of the role that provided the privilege.

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

Displays the user or role that provided the privilege.

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

Displays the grantor type: USER, ROLE or ROLEGROUP.

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

NVARCHAR\(32\)

</td>
<td valign="top">

Displays the type of the granted object, for example, TABLE, SCHEMA, and so on.

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

Displays the schema name the object belongs to.

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

Displays the object name of granted object.

</td>
</tr>
<tr>
<td valign="top">

PRIVILEGE

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the privilege granted.

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

Displays whether the privilege was granted with WITH GRANT OPTION, WITH ADMIN OPTION: TRUE/FALSE.

</td>
</tr>
<tr>
<td valign="top">

IS\_VALID

</td>
<td valign="top">

NVARCHAR\(5\)

</td>
<td valign="top">

Displays whether the privilege is valid or has become invalid due to implicit revoking: TRUE/FALSE.

</td>
</tr>
</table>



<a name="loio20a2f3ea75191014a4c1d9b0859b9917__section_ejg_5dk_h2b"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

To search for effective \(directly or indirectly\) privileges and roles, granted to a given user or role, requires an equal \(=\) predicate on USER\_NAME specifying an existing user name or an equal \(=\) predicate on PRINCIPAL\_NAME specifying an existing user name or role name.

**Related Information**  


[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[PRIVILEGES System View](privileges-system-view-20cc29b.md "Provides information about available privileges.")

[System Views for Verifying Users' Authorization](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/ddae823e3b27477ea4c949607eebc435.html "You can query several system views to get detailed information about exactly which privileges and roles users have and how they come to have them. This can help you to understand why a user is authorized to perform particular actions, access particular data, or not.") :arrow_upper_right:

[ROLEGROUPS System Views](rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

