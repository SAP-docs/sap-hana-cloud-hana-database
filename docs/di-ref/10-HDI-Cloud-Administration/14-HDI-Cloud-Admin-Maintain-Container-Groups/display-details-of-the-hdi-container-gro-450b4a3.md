<!-- loio450b4a3dd9974dd99a3fffb779e6dd5d -->

# Display Details of the HDI Container-Group Configuration

View information about all HDI container groups, their configuration, and their status.



<a name="loio450b4a3dd9974dd99a3fffb779e6dd5d__context_amg_31k_kkb"/>

## Context

The SAP HANA Deployment Infrastructure \(HDI\) component includes a selection of views that you can use to monitor HDI containers assigned to container groups and display the corresponding configuration details, for example, which roles and privileges have been granted to users, and any related messages. The following monitoring views can be used to display information about the status and configuration of an HDI container group:


<table>
<tr>
<th valign="top">

\#



</th>
<th valign="top">

HDI Container View



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

[`M_CONTAINERS`](../../20-HDI-Cloud-Content-Development/m-containers-dcf1c9e.md)



</td>
<td valign="top">

The HDI containers assigned to a container group



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

[`M_CONTAINER_VERSIONS`](../../20-HDI-Cloud-Content-Development/m-container-versions-22320f7.md)



</td>
<td valign="top">

The version history and status information of all HDI containers in a container group



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

[`M_MESSAGES`](../../20-HDI-Cloud-Content-Development/m-messages-1696923.md)



</td>
<td valign="top">

The messages relating to HDI container groups



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

[`M_JOBS`](../../20-HDI-Cloud-Content-Development/m-jobs-d114ced.md)



</td>
<td valign="top">

Shows information about the progress of the individual jobs of a MAKE operation



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

[`M_ROLES`](../../20-HDI-Cloud-Content-Development/m-roles-b7f3bee.md)



</td>
<td valign="top">

The container roles for all HDI containers in a container group



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

[`M_GRANTED_SCHEMA_PRIVILEGES`](../../20-HDI-Cloud-Content-Development/m-granted-schema-privileges-77bf987.md)



</td>
<td valign="top">

The details of all granted schema privileges



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

[`M_GRANTED_SCHEMA_ROLES`](../../20-HDI-Cloud-Content-Development/m-granted-schema-roles-6f832a6.md)



</td>
<td valign="top">

The details of all granted schema roles



</td>
</tr>
</table>

> ### Note:  
> For more details about each of the individual views mentioned in this topic, for example, `M_CONTAINERS`, as well a description of the information the view can be used to display, see *HDI Monitoring Views* in *Related Information* below.



<a name="loio450b4a3dd9974dd99a3fffb779e6dd5d__steps_cpr_2fk_kkb"/>

## Procedure

1.  Show all HDI containers assigned to a container group.

    Use the container-specific monitoring view `M_CONTAINERS` to display an overview of the HDI containers assigned to a container group. For example, this view shows the container's name `CONTAINER_NAME`, the name of the user \(`USER_NAME`\) or application user `APPUSER_NAME` who created the container, and the time at which the container was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

2.  Show the version history and status information of all HDI containers in a container group.

    Use the monitoring view `M_CONTAINER_VERSIONS` to display an overview of the version history and status information of all HDI containers in a container group. For example, this view shows the container's name `CONTAINER_NAME`, the container version number \(`VERSION`\), the current status \(`STATUS`\), and the time at which the container was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

3.  Show all messages relating to HDI container groups.

    Use the container-specific monitoring view `M_MESSAGES` to display an overview of all messages for a container group. For example, this view shows the `MESSAGE` \(text\), the `TIMESTAMP_UTC`, the message `TYPE`, the message `SEVERITY`, the time at which the message was created `CREATE_TIMESTAMP_UTC`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

4.  Show the progress of the individual jobs linked with selected container operations.

    Use the container view `M_JOBS` to display an overview of the status and progress of the individual jobs linked with container operations. Information is filtered according to the corresponding container group.

    For example, this view shows the number of jobs running \(`NUM_JOBS`\), the job's status \(`STATUS`\), the name of the user \(`USER_NAME`\) or application user `APPUSER_NAME` who called the API that triggered the job, the numeric identifier of the currently running job \(`CURRENT_JOB`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

5.  Show all container roles for all HDI containers in a container group.

    Use the container-specific monitoring view `M_ROLES` to display an overview of all container roles for all HDI containers in a container group where the current user has `SELECT` permission on the view `M_ROLES` at either the container or the container-group level. For example, you can use this view to see the `ROLE_NAME`, the `ROLE_ID`, the name of the user who created the role `CREATOR`, the time at which the role was created `CREATE_TIME`, the context for which the role is valid \(`CONTEXT`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

6.  Show all granted schema privileges.

    Use the container-specific monitoring view `M_GRANTED_SCHEMA_PRIVILEGES` to display an overview of all container-specific schema privileges for any container in the selected container group, which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.

    > ### Tip:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>". M_GRANTED_SCHEMA_PRIVILEGES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI". M_GRANTED_SCHEMA_PRIVILEGES</code>.

    For example, you can use this view to see the target of the privilege \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the privilege granted \(`PRIVILEGE`\) and whether or not \(TRUE/FALSE\) the privilege can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.

7.  Show all granted schema roles.

    Use the container-specific monitoring view `M_GRANTED_SCHEMA_ROLES` to display an overview of all HDI-generated roles for any container in the selected container group, which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES`.

    > ### Tip:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either of the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>".M_GRANTED_SCHEMA_ROLES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI".M_GRANTED_SCHEMA_ROLES</code>.

    For example, you can use this view to see the target of the role \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the role granted \(`ROLE_NAME`\) and whether or not \(TRUE/FALSE\) the role can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Container Views* in *Related Information* below.


**Related Information**  


[HDI Container Views](../../20-HDI-Cloud-Content-Development/hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

[\_SYS\_DI Monitoring Views](../13-HDI-Cloud-Admin-Maintain-HDI/sys-di-monitoring-views-78e1657.md "Display information about HDI-container-related operations.")

