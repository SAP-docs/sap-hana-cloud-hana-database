<!-- loio4f93c233c44f41c3b6a0fd94e2747764 -->

# Display Details of the HDI Configuration

View information about all HDI containers, their configuration, and their status.



<a name="loio4f93c233c44f41c3b6a0fd94e2747764__context_amg_31k_kkb"/>

## Context

The SAP HANA Deployment Infrastructure component includes a selection of `_SYS_DI` views that you can use to monitor the current state of the HDI containers, container groups, and the corresponding configuration details, for example, the roles and privileges granted to users, and any related messages. The following `_SYS_DI` views can be used to display information about the current status of the HDI configuration:


<table>
<tr>
<th valign="top">

\#

</th>
<th valign="top">

`_SYS_DI` HDI View

</th>
<th valign="top">

Information Displayed

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

[`M_ALL_CONTAINERS`](m-all-containers-61ce5ab.md) 

</td>
<td valign="top">

All HDI containers in the database and the container groups to which they are assigned

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

[`M_ALL_CONTAINER_GROUPS`](m-all-container-groups-0f41f81.md)

</td>
<td valign="top">

All HDI container groups in the database

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

[`M_ALL_CONTAINER_VERSIONS`](m-all-container-versions-d4d64f3.md)

</td>
<td valign="top">

The version history and status information of all HDI containers in the database

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

[`M_ALL_JOBS`](m-all-jobs-5e83abe.md)

</td>
<td valign="top">

Progress of the individual jobs linked with container operations

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

[`M_ALL_MESSAGES`](m-all-messages-9a0433a.md)

</td>
<td valign="top">

All messages relating to HDI container groups

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

[`M_ALL_ROLES`](m-all-roles-205b891.md)

</td>
<td valign="top">

All container roles for any HDI container

</td>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

[`M_ALL_GRANTED_SCHEMA_PRIVILEGES`](m-all-granted-schema-privileges-e00400d.md)

</td>
<td valign="top">

The details of all granted schema privileges

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

[`M_ALL_GRANTED_SCHEMA_ROLES`](m-all-granted-schema-roles-7e7b14e.md)

</td>
<td valign="top">

The details of all granted schema roles

</td>
</tr>
</table>

> ### Note:  
> For more details about each of the individual views mentioned in this topic, for example, `M_ALL_CONTAINERS`, as well a description of the information the view can be used to display, see *HDI Monitoring Views* in *Related Information* below.



## Procedure

1.  Show all HDI containers in the database and the container groups to which they are assigned.

    Use the `_SYS_DI` monitoring view `M_ALL_CONTAINERS` to display an overview of the HDI containers in the database.

    For example, this view shows the container's name `CONTAINER_NAME`, the name of the user \(`USER_NAME`\) or application user `APPUSER_NAME` who created the container, and the time at which the container was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

2.  Show all HDI container groups in the database.

    Use the `_SYS_DI` monitoring view `M_ALL_CONTAINER_GROUPS` to display an overview of the HDI container groups in the database.

    For example, this view shows the container group's name `CONTAINER_GROUP_NAME`, the name of the user group associated with the container group \(`CONTAINER_GROUP_USERGROUP_NAME`\), the name of the user \(`USER_NAME`\) or application user `APPUSER_NAME` who created the container, and the time at which the container was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

3.  Show all HDI container versions in the database.

    Use the `_SYS_DI` monitoring view `M_ALL_CONTAINER_VERSIONS` to display an overview of the version history and status information of all HDI containers in the database.

    For example, this view shows the container's name and version \(`CONTAINER_NAME`, `VERSION`\), the current status of the container \(`STATUS`\), and the time at which the container was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

4.  Show the progress of the individual jobs linked with container operations.

    Use the `_SYS_DI` monitoring view `M_ALL_JOBS` to display an overview of the status and progress of the individual jobs linked with container operations.

    For example, this view shows the number of jobs running \(`NUM_JOBS`\), the job's status \(`STATUS`\), the name of the user \(`USER_NAME`\) or application user `APPUSER_NAME` who called the API that triggered the job, the numeric identifier of the currently running job \(`CURRENT_JOB`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

5.  Show all messages relating to HDI container groups.

    Use the `_SYS_DI` monitoring view `M_ALL_MESSAGES` to display an overview of all container-group messages for all container groups.

    For example, this view shows the unique ID of the API call that generated the message \(`REQUEST_ID`\), the type of message \(`TYPE`\), the `MESSAGE` \(text\), the time at which the message was created \(`TIMESTAMP_UTC`\), the message severity \(`SEVERITY`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

6.  Show all container roles for any HDI container.

    Use the `_SYS_DI` monitoring view `M_ALL_ROLES` to display an overview of all container roles for any HDI container where the current user has `SELECT` permission on the view `M_ROLES` \(at either the container or the container-group level\).

    For example, you can use this view to see the `ROLE_NAME`, the `ROLE_ID`, the name of the user who created the role `CREATOR`, the time at which the role was created \(`CREATE_TIME`\), the context for which the role is valid \(`CONTEXT`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

7.  Show all granted schema privileges.

    Use the `_SYS_DI` monitoring view `M_ALL_GRANTED_SCHEMA_PRIVILEGES` to display an overview of all container-specific schema privileges \(for any container\), which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.

    > ### Tip:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>". M_GRANTED_SCHEMA_PRIVILEGES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI". M_GRANTED_SCHEMA_PRIVILEGES</code>.

    For example, you can use this view to see the target of the privilege \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the privilege granted \(`PRIVILEGE`\) and whether or not \(TRUE/FALSE\) the privilege can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

8.  Show all granted schema roles.

    Use the `_SYS_DI` monitoring view `M_ALL_GRANTED_SCHEMA_ROLES` to display an overview of all HDI-generated roles \(for any container\), which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES`.

    > ### Tip:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either of the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>".M_GRANTED_SCHEMA_ROLES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI".M_GRANTED_SCHEMA_ROLES</code>.

    For example, you can use this view to see the target of the role \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the role granted \(`PRIVILEGE`\) and whether or not \(TRUE/FALSE\) the role can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.


**Related Information**  


[\_SYS\_DI Monitoring Views](sys-di-monitoring-views-78e1657.md "Display information about HDI-container-related operations.")

[Display Details of the HDI Container-Group Configuration](../14-HDI-Cloud-Admin-Maintain-Container-Groups/display-details-of-the-hdi-container-gro-450b4a3.md "View information about all HDI container groups, their configuration, and their status.")

[Display Details of the HDI Container Configuration](../15-HDI-Cloud-Admin-Maintain-Containers/display-details-of-the-hdi-container-configura-77d0b8a.md "View information about all HDI containers, their configuration, and their status.")

