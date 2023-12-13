<!-- loiob7f3beecce4048949d34b82a523f8ee5 -->

# M\_ROLES

Show the roles that are deployed in an HDI container.



The SAP HDI Container API includes the `M_ROLES` view, which enables you to display information about the individual roles deployed in an HDI container.



**M\_ROLES**


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

ROLE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the role

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

The role ID

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

The mode of the role: '`LOCAL`'

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

The identity specified for role with `ROLE_MODE GLOBAL` 

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

The name of the user who created the role

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

The time at which the role was created

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

The context for which the role is valid

</td>
</tr>
</table>

**Related Information**  


[M\_JOBS](m-jobs-d114ced.md "View information about the progress of jobs belonging to a MAKE operation.")

[M\_MESSAGES](m-messages-1696923.md "Shows all recent messages for API calls to an HDI container.")

[M\_GRANTED\_SCHEMA\_PRIVILEGES](m-granted-schema-privileges-77bf987.md "View information about the schema-related privileges granted to users and roles.")

[M\_GRANTED\_SCHEMA\_ROLES](m-granted-schema-roles-6f832a6.md "View information about the schema-related roles granted to users and user roles.")

