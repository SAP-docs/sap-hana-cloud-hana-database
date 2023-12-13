<!-- loio77bf987f41824d2ba02ccb055d4461b6 -->

# M\_GRANTED\_SCHEMA\_PRIVILEGES

View information about the schema-related privileges granted to users and roles.



The SAP HDI Container API includes the `M_GRANTED_SCHEMA_PRIVILEGES` view, which shows the HDI-container-specific schema privileges that have been granted to users or user roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.

> ### Note:  
> The `M_GRANTED_SCHEMA_PRIVILEGES` view does not show privileges that are granted to a deployed HDI role.



**M\_GRANTED\_SCHEMA\_PRIVILEGES**


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

The privilege `PRIVILEGE` was granted `'WITH [GRANT | ADMIN] OPTION': ['TRUE' | 'FALSE']` 

</td>
</tr>
</table>

**Related Information**  


[M\_ROLES](m-roles-b7f3bee.md "Show the roles that are deployed in an HDI container.")

[M\_GRANTED\_SCHEMA\_ROLES](m-granted-schema-roles-6f832a6.md "View information about the schema-related roles granted to users and user roles.")

[HDI Container Views](hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

