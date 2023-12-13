<!-- loio77d0b8a9b97e43479cc499420ab4d111 -->

# Display Details of the HDI Container Configuration

View information about all HDI containers, their configuration, and their status.



<a name="loio77d0b8a9b97e43479cc499420ab4d111__context_amg_31k_kkb"/>

## Context

The SAP HANA Deployment Infrastructure \(HDI\) component includes a selection of views that you can use to monitor HDI containers, for example, by displaying the corresponding configuration details, which roles and privileges have been granted to users, and any related messages. The following monitoring views can be used to display information about the status and configuration of an HDI container:


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

[`M_CONFIGURATION`](../../20-HDI-Cloud-Content-Development/m-configuration-b2b6ed1.md)

</td>
<td valign="top">

The HDI container configuration

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

[`M_JOBS`](../../20-HDI-Cloud-Content-Development/m-jobs-d114ced.md)

</td>
<td valign="top">

The progress of the individual jobs in a `MAKE` operation

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

[`M_OBJECTS`](../../20-HDI-Cloud-Content-Development/m-objects-d73be7e.md)

</td>
<td valign="top">

The database objects in the run-time schema of an HDI container

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

The container roles deployed to an HDI container

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
> For more details about each of the individual views mentioned in this topic, for example, `M_CONFIGURATION`, as well a description of the information the view can be used to display, see *HDI Container Views* in *Related Information* below.



<a name="loio77d0b8a9b97e43479cc499420ab4d111__steps_cpr_2fk_kkb"/>

## Procedure

1.  Show details of the HDI container configuration.

    Use the container-specific monitoring view `M_CONFIGURATION` to display an overview of the configurations of an HDI container, which were made with the procedure `CONFIGURE_CONTAINER_PARAMETERS`.

2.  Show details of the progress of the individual **jobs** in a `MAKE` operation.

    Use the monitoring view `M_JOBS` to display an overview of the individual jobs included in a `MAKE` operation, for example: the job's `REQUEST_ID`, the name of the user \(`USER_NAME`\) or application user \(`APPUSER_NAME`\) who started the `MAKE` operation, the `STATUS` of the make operation, etc.

3.  Show all **messages** relating to HDI container groups.

    Use the container-specific monitoring view `M_MESSAGES` to display an overview of all messages for a container group, for example: the `MESSAGE` \(text\), the `TIMESTAMP_UTC`, the message `TYPE`, the message `SEVERITY`, etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

4.  Show the container **roles** deployed to an HDI container.

    Use the container-specific monitoring view `M_ROLES` to display an overview of the roles deployed to an HDI container. For example, you can use this view to see the `ROLE_NAME`, the `ROLE_ID`, the name of the user who created the role `CREATOR`, the context for which the role is valid \(`CONTEXT`\), etc.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

5.  Show the database **objects** that are present in the run-time schema of an HDI container.

    Use the container-specific monitoring view `M_OBJECTS` to display an overview of the database objects deployed to HDI container's run-time schema. This includes all objects that have been deployed as well as any objects that have been created manually. For example, you can use this view to see the object's name \(`OBJECT_NAME`\) and type \(`OBJECT_TYPE`\) as well as information about the object's validity \(`IS_VALID`\) and the object's owner \(`OWNER_NAME`\).

    The `M_OBJECTS` view is intended to help troubleshoot issues that may arise from objects becoming invalid, being deleted, or created with the wrong user.

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

6.  Show details of all granted **schema privileges**.

    Use the container-specific monitoring view `M_GRANTED_SCHEMA_PRIVILEGES` to display an overview of all container-specific schema privileges for any container in the selected container group, which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES`.

    > ### Note:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either of the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>".M_GRANTED_SCHEMA_PRIVILEGES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI".M_GRANTED_SCHEMA_PRIVILEGES</code>.

    For example, you can use this view to see the target of the privilege \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the privilege granted \(`PRIVILEGE`\) and whether or not \(TRUE/FALSE\) the privilege can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.

7.  Show details of all granted schema roles.

    Use the container-specific monitoring view `M_GRANTED_SCHEMA_ROLES` to display an overview of all HDI-generated roles for any container in the selected container group, which have been granted to users or roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES`.

    > ### Note:  
    > The permission check is done for any HDI container where the current user has `SELECT` permission on either of the corresponding views <code>"<i class="varname">&lt;CONTAINER_GROUP_SCHEMA&gt;</i>".M_GRANTED_SCHEMA_ROLES</code> or <code>"<i class="varname">&lt;container specific&gt;</i>#DI".M_GRANTED_SCHEMA_ROLES</code>.

    For example, you can use this view to see the target of the role \(`GRANTEE`\), the type of target \(`GRANTEE_TYPE`\) which can be either a user or a role, as well as details of the role granted \(`PRIVILEGE`\) and whether or not \(TRUE/FALSE\) the role can be granted further \(`IS_GRANTABLE`\).

    > ### Tip:  
    > For a comprehensive list of the information that this view can be used to display, see *HDI Monitoring Views* in *Related Information* below.


**Related Information**  


[HDI Container Views](../../20-HDI-Cloud-Content-Development/hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

[\_SYS\_DI Monitoring Views](../13-HDI-Cloud-Admin-Maintain-HDI/sys-di-monitoring-views-78e1657.md "Display information about HDI-container-related operations.")

[Display Details of the HDI Configuration](../13-HDI-Cloud-Admin-Maintain-HDI/display-details-of-the-hdi-configuration-4f93c23.md "View information about all HDI containers, their configuration, and their status.")

[Display Details of the HDI Container-Group Configuration](../14-HDI-Cloud-Admin-Maintain-Container-Groups/display-details-of-the-hdi-container-gro-450b4a3.md "View information about all HDI container groups, their configuration, and their status.")

