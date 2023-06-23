<!-- loioe00400d917a5467f938fce909da28ea4 -->

# M\_ALL\_GRANTED\_SCHEMA\_PRIVILEGES

View information about all schema-related privileges granted to users and roles.



The `_SYS_DI` monitoring view `M_ALL_GRANTED_SCHEMA_PRIVILEGES` shows all HDI-container-specific schema privileges for any container, which are granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.

> ### Tip:  
> Container-related information is visible to any user with the `SELECT` permission on either the corresponding views <code>“<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>”. M_GRANTED_SCHEMA_PRIVILEGES</code> or <code>“<i class="varname">&lt;container specific&gt;</i>#DI”. M_GRANTED_SCHEMA_PRIVILEGES</code>.



**M\_ALL\_GRANTED\_SCHEMA\_PRIVILEGES**


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

GRANTEE\_SCHEMA\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the schema containing the target role to which the privilege is granted



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

The name of the target user or user role to whom/which the privilege `PRIVILEGE` is granted



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

PRIVILEGE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The name of the privilege to be granted to a user or user role



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

The privilege `PRIVILEGE` was granted `‘WITH [GRANT | ADMIN] OPTION': ['TRUE' | 'FALSE']` 



</td>
</tr>
</table>

**Related Information**  


[M\_GRANTED\_SCHEMA\_PRIVILEGES](../../20-HDI-Cloud-Content-Development/m-granted-schema-privileges-77bf987.md "View information about the schema-related privileges granted to users and roles.")

