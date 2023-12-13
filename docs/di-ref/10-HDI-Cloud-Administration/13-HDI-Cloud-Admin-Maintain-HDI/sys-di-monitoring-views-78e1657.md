<!-- loio78e1657f43f04741b9c2b161632e4fe5 -->

# \_SYS\_DI Monitoring Views

Display information about HDI-container-related operations.

The following tables list the `_SYS_DI` monitoring views that the HDI administrator can use to display information about the status and configuration of containers or container groups and their components:

**\_SYS\_DI Monitoring Views**


<table>
<tr>
<th valign="top">

HDI View

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[`M_ALL_CONTAINERS`](m-all-containers-61ce5ab.md)

</td>
<td valign="top">

Shows all HDI containers in the database and the container groups to which they are assigned

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_CONTAINER_VERSIONS`](m-all-container-versions-d4d64f3.md)

</td>
<td valign="top">

Shows the version history and status information of all HDI containers in the database. There can be multiple entries per container

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_CONTAINER_CONFIGURATIONS`](m-all-container-configurations-e68a6e7.md)

</td>
<td valign="top">

Shows all HDI container-specific configuration changes in the database, which are visible to the user. The view is public.

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_CONTAINER_GROUPS`](m-all-container-groups-0f41f81.md)

</td>
<td valign="top">

Shows all HDI container groups in the database and any container groups to which they are assigned

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_GROUP_CONFIGURATIONS`](m-all-group-configurations-e9ec687.md)

</td>
<td valign="top">

Shows all HDI container-group-specific configuration changes in the database, which are visible to the user. The view is public.

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_GRANTED_SCHEMA_PRIVILEGES`](m-all-granted-schema-privileges-e00400d.md)

</td>
<td valign="top">

Shows all HDI-container-specific, schema-related privileges for any container, which have been granted to users or roles by means of the `GRANT_CONTAINER_SCHEMA_PRIVILEGES` 

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_GRANTED_SCHEMA_ROLES`](m-all-granted-schema-roles-7e7b14e.md)

</td>
<td valign="top">

Shows all HDI-generated roles for any container, which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES` 

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_JOBS`](m-all-jobs-5e83abe.md)

</td>
<td valign="top">

Shows information about the progress of the individual jobs linked with container operations

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_MESSAGES`](m-all-messages-9a0433a.md) 

</td>
<td valign="top">

Shows all container group messages of all container groups

</td>
</tr>
<tr>
<td valign="top">

[`M_ALL_ROLES`](m-all-roles-205b891.md)

</td>
<td valign="top">

Shows all container roles for any HDI container

</td>
</tr>
<tr>
<td valign="top">

[`M_VISIBLE_CONTAINERS`](m-visible-containers-7972902.md)

</td>
<td valign="top">

Shows all HDI containers in the database which the user is allowed to see and the container groups to which the visible containers are assigned

</td>
</tr>
<tr>
<td valign="top">

[`M_VISIBLE_CONTAINER_GROUPS`](m-visible-container-groups-5ed997a.md)

</td>
<td valign="top">

Shows all HDI container groups in the database which the user has the privileges to view.

</td>
</tr>
</table>

**Related Information**  


[Display Details of the HDI Configuration](display-details-of-the-hdi-configuration-4f93c23.md "View information about all HDI containers, their configuration, and their status.")

[HDI Container Views](../../20-HDI-Cloud-Content-Development/hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

