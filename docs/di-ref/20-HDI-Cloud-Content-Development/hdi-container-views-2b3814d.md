<!-- loio2b3814d836bb409e87290e70ea8bee7f -->

# HDI Container Views

Display information about calls made with the HDI container API.

In SAP HANA Deployment Infrastructure \(HDI\), an HDI container administrator is responsible for configuring and controlling access to an HDI container; the SQL application-programming interfaces \(APIs\) for content development in an HDI container are in the container's corresponding schema. For example, the SQL APIs for the HDI container `C` are in the schema `C#DI`. The following tables list the views that you can use to display information about calls made with the HDI container API:

**SQL Views for HDI-Container Content-Development API Calls**


<table>
<tr>
<th valign="top">

HDI Container SQL View

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

[`M_CONFIGURATION`](m-configuration-b2b6ed1.md) 

</td>
<td valign="top">

Shows information about the changes made to the configuration of an HDI container

</td>
</tr>
<tr>
<td valign="top">

[`M_CONTAINERS`](m-containers-dcf1c9e.md) 

</td>
<td valign="top">

Shows all HDI containers that are assigned to a container group

</td>
</tr>
<tr>
<td valign="top">

[`M_CONTAINER_VERSIONS`](m-container-versions-22320f7.md)

</td>
<td valign="top">

Shows the version history and status information of all HDI containers that are assigned to a container group. There can be multiple entries per container

</td>
</tr>
<tr>
<td valign="top">

[`M_GRANTED_SCHEMA_PRIVILEGES`](m-granted-schema-privileges-77bf987.md)

</td>
<td valign="top">

Shows the HDI-container-specific, schema privileges that have been granted to users or user roles by means of the procedure `GRANT_CONTAINER_SCHEMA_PRIVILEGES` 

</td>
</tr>
<tr>
<td valign="top">

[`M_GRANTED_SCHEMA_ROLES`](m-granted-schema-roles-6f832a6.md)

</td>
<td valign="top">

Shows the HDI-container-specific, schema-related roles that have been granted to users or user roles by means of the procedure `GRANT_CONTAINER_SCHEMA_ROLES` 

</td>
</tr>
<tr>
<td valign="top">

[`M_JOBS`](m-jobs-d114ced.md)

</td>
<td valign="top">

Shows information about the progress of the individual jobs of a MAKE operation

</td>
</tr>
<tr>
<td valign="top">

[`M_MESSAGES`](m-messages-1696923.md) 

</td>
<td valign="top">

Shows all recent messages for API calls to the specified HDI container

</td>
</tr>
<tr>
<td valign="top">

[`M_OBJECTS`](m-objects-d73be7e.md) 

</td>
<td valign="top">

Shows the database objects in the run-time schema of an HDI container.

</td>
</tr>
<tr>
<td valign="top">

[`M_ROLES`](m-roles-b7f3bee.md) 

</td>
<td valign="top">

Shows all the roles that are deployed in the specified HDI container

</td>
</tr>
</table>

**Related Information**  


[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[SAP HDI Container Content Development with the HDI API](sap-hdi-container-content-development-with-the-hdi-api-bea716c.md "SAP HDI includes an SQL API for the development of content in SAP HDI containers.")

[\_SYS\_DI Monitoring Views](../10-HDI-Cloud-Administration/13-HDI-Cloud-Admin-Maintain-HDI/sys-di-monitoring-views-78e1657.md "Display information about HDI-container-related operations.")

