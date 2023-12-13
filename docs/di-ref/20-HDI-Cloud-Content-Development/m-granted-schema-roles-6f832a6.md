<!-- loio6f832a6205af476492b1b36f8a19e733 -->

# M\_GRANTED\_SCHEMA\_ROLES

View information about the schema-related roles granted to users and user roles.



The SAP HDI Container API includes the `M_GRANTED_SCHEMA_ROLES` view, which shows the HDI-container-specific, schema-related roles that have been granted to users or user roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES`.



**M\_GRANTED\_SCHEMA\_ROLES**


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

The role `ROLE_NAME` was granted `'WITH ADMIN OPTION': ['TRUE' | 'FALSE']` 

</td>
</tr>
</table>

**Related Information**  


[HDI Container Views](hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

[M\_ROLES](m-roles-b7f3bee.md "Show the roles that are deployed in an HDI container.")

[M\_GRANTED\_SCHEMA\_PRIVILEGES](m-granted-schema-privileges-77bf987.md "View information about the schema-related privileges granted to users and roles.")

[M\_ALL\_GRANTED\_SCHEMA\_ROLES](../10-HDI-Cloud-Administration/13-HDI-Cloud-Admin-Maintain-HDI/m-all-granted-schema-roles-7e7b14e.md "View information about the schema-related roles granted to users and user roles.")

