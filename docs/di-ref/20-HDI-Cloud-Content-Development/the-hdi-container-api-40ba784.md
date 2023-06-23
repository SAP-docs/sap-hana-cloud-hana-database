<!-- loio40ba784dcaf44989b23f7eda316b4a0b -->

# The HDI Container API

Maintain HDI containers and container content using the HDI container API.

In SAP HANA Deployment Infrastructure \(HDI\), an HDI container administrator is responsible for configuring and controlling access to an HDI container; the SQL application-programming interfaces \(APIs\) for content development in an HDI container are in the container's corresponding schema. For example, the SQL APIs for the HDI container `C` are in the schema `C#DI`. The following tables indicate which SQL APIs are available for use during content development in an HDI container:

**SQL APIs for Content Development in HDI Containers**


<table>
<tr>
<th valign="top">

SQL API



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 [`WRITE`](write-bfd0969.md) 



</td>
<td valign="top">

Writes or creates the specified files or folders in the HDI container's **work** file system.



</td>
</tr>
<tr>
<td valign="top">

 [`DELETE`](delete-d5c50df.md) 



</td>
<td valign="top">

Deletes the given files or folders from the HDI container's **work** file system.



</td>
</tr>
<tr>
<td valign="top">

 [`STATUS`](status-e14a40c.md) 



</td>
<td valign="top">

Shows the status of the specified files or folders in the HDI container's **work** file system.



</td>
</tr>
<tr>
<td valign="top">

 [`MAKE`](make-7a0b4c5.md) 



</td>
<td valign="top">

Triggers a `make` call with the specified set of files or folders; the `make` call returns after the `make` operation has finished



</td>
</tr>
<tr>
<td valign="top">

 [`MAKE ASYNC`](make-async-e871e85.md) 



</td>
<td valign="top">

Triggers a `make` call with the specified set of files or folders; the call returns with a `REQUEST_ID` while the `make` command continues to run in the background



</td>
</tr>
<tr>
<td valign="top">

 [`LIST`](list-8bb0757.md) 



</td>
<td valign="top">

Lists the specified files or folders from the HDI container's **work** file system



</td>
</tr>
<tr>
<td valign="top">

 [`LIST DEPLOYED`](list-deployed-6709ac6.md) 



</td>
<td valign="top">

Lists the specified files or folders from the HDI container's **deployed** file system



</td>
</tr>
<tr>
<td valign="top">

 [ `READ`](read-11ddeb3.md) 



</td>
<td valign="top">

Reads the specified files or folders from the HDI container's **work** file system



</td>
</tr>
<tr>
<td valign="top">

 [`READ DEPLOYED`](read-deployed-5873a56.md) 



</td>
<td valign="top">

Reads the specified files or folders from the HDI container's **deployed** file system



</td>
</tr>
<tr>
<td valign="top">

 [`GET MAKE GROUPS`](get-make-groups-d8b856b.md) 



</td>
<td valign="top">

Calculates groups of objects that are independent of each other and could be passed to a `make` call individually



</td>
</tr>
<tr>
<td valign="top">

 [`GET DEPENDENCIES`](get-dependencies-dc12a28.md) 



</td>
<td valign="top">

Retrieves dependency data; the kind of data that is retrieved depends on the optional *<variant\>* parameter passed via `PARAMETERS` 



</td>
</tr>
<tr>
<td valign="top">

 [`LIST_CONFIGURED_LIBRARIES`](list-configured-libraries-c55fb25.md) 



</td>
<td valign="top">

Displays a list of all the build plug-in libraries available for use in the specified HDI container



</td>
</tr>
<tr>
<td valign="top">

 [`GRANT_CONTAINER_SCHEMA_PRIVILEGES`](grant-container-schema-privileges-d751824.md) 



</td>
<td valign="top">

Grants access privileges to a database object consumer for the entire HDI container schema in which the database objects are located



</td>
</tr>
<tr>
<td valign="top">

 [`REVOKE_CONTAINER_SCHEMA_PRIVILEGES`](revoke-container-schema-privileges-c9c9455.md) 



</td>
<td valign="top">

Revokes access privileges from a database object consumer for the entire container schema in which the database objects are located



</td>
</tr>
<tr>
<td valign="top">

 [`GRANT_CONTAINER_SCHEMA_ROLES`](grant-container-schema-roles-2429050.md) 



</td>
<td valign="top">

Enable access to objects in the container schema by means of a role from the container schema



</td>
</tr>
<tr>
<td valign="top">

 [`REVOKE_CONTAINER_SCHEMA_ROLES`](revoke-container-schema-roles-83541ed.md) 



</td>
<td valign="top">

Disable access to objects in the container schema by means of a role from the container schema



</td>
</tr>
</table>

**Related Information**  


[SAP HDI Container Content Development with the HDI API](sap-hdi-container-content-development-with-the-hdi-api-bea716c.md "SAP HDI includes an SQL API for the development of content in SAP HDI containers.")

[HDI Container Views](hdi-container-views-2b3814d.md "Display information about calls made with the HDI container API.")

