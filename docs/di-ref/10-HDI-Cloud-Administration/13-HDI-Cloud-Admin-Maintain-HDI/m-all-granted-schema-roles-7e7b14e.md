<!-- loio7e7b14ef04764b9096d36b0c6f0a1996 -->

# M\_ALL\_GRANTED\_SCHEMA\_ROLES

View information about the schema-related roles granted to users and user roles.



The `_SYS_DI` monitoring view `M_ALL_GRANTED_SCHEMA_ROLES` shows all HDI-generated roles \(from any container\), which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES`.

> ### Tip:  
> Container-related information is visible to any user with the `SELECT` permission on either of the corresponding views <code>“<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>”.M_GRANTED_SCHEMA_ROLES</code> or <code>“<i class="varname">&lt;container specific&gt;</i>#DI”.M_GRANTED_SCHEMA_ROLES</code>.



**M\_ALL\_GRANTED\_SCHEMA\_ROLES**


<table>
<tr>
<th valign="top">

Name

</th>
<th valign="top">

Data Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

CONTAINER\_NAME

</td>
<td valign="top">

NVARCHAR\(64\)

</td>
<td valign="top">

The name of the HDI container

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

The name of the granted role

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

The name of the target user or the target role to whom \(or which\) the role `ROLE_NAME` is granted

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

The name of the schema containing the granted role `ROLE_NAME` 

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

Either “USER” or “ROLE” 

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

The role `ROLE_NAME` was granted `‘WITH ADMIN OPTION': ['TRUE' | 'FALSE']` 

</td>
</tr>
</table>

**Related Information**  


[M\_GRANTED\_SCHEMA\_ROLES](../../20-HDI-Cloud-Content-Development/m-granted-schema-roles-6f832a6.md "View information about the schema-related roles granted to users and user roles.")

[\_SYS\_DI Monitoring Views](sys-di-monitoring-views-78e1657.md "Display information about HDI-container-related operations.")

