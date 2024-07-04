<!-- loio40faae29522747e3b9548b1f4d296707 -->

# SAP HDI Users

A list of the predefined users which SAP HDI relies on and a description of their respective role.

HDI uses several container-specific technical users to separate the different container-related tasks such as creating the schemas and triggering deployment.

Most of the server agents require a data store in the SAP HANA database and therefore need secure access to schemas. For this reason, a dedicated technical SAP HANA user is generated for each such schema, and the credentials of the technical SAP HANA user are passed to the server agent. As the management of technical users is performed at the infrastructure level, end users typically do not interact with these users.

The technical users listed in the following table are used to connect to the SAP HANA database with a specific set of conditions.


<table>
<tr>
<th valign="top">

User ID

</th>
<th valign="top">

Service

</th>
<th valign="top">

Type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`_SYS_DI`

</td>
<td valign="top">

HDI

</td>
<td valign="top">

Technical database user

</td>
<td valign="top">

Owns all HDI SQL-based APIs, for example all API procedures in the `_SYS_DI` schema and API procedures in containers

</td>
</tr>
<tr>
<td valign="top">

`_SYS_DI_*_CATALOG`

</td>
<td valign="top">

HDI

</td>
<td valign="top">

Technical database user

</td>
<td valign="top">

Technical users used by the HDI to access database system catalog tables and views

</td>
</tr>
<tr>
<td valign="top">

`_SYS_DI_SU`

</td>
<td valign="top">

HDI

</td>
<td valign="top">

Technical database user

</td>
<td valign="top">

Technical superuser of the HDI created at installation time

</td>
</tr>
<tr>
<td valign="top">

`_SYS_DI_TO`

</td>
<td valign="top">

HDI

</td>
<td valign="top">

Technical database user

</td>
<td valign="top">

Owns transaction and connections of all internal HDI transactions

</td>
</tr>
</table>





### Technical Users for HDI Schema-Based Containers

The deployment of database objects with SAP HANA Deployment Infrastructure \(HDI\) is based on a container model where each container corresponds roughly to a database schema. Each schema, and the database objects deployed into the schema, are owned by a dedicated technical database user.

For every container deployed, a new technical database user and schema with the same name as the container are created. Additional schemas and technical users required for metadata and deployment APIs are also created.

For example, for a container named `S`, HDI creates the following users:

-   `S`:

    The user who is the owner of the container schema `S`

-   User `S#DI`:

    The user who is the owner of the schema `S#DI` containing metadata and deployment APIs

-   User `S#OO`:

    The user who is the owner of database objects in schema `S`

-   Users <code>_DI#S#METADATA_COM_SAP_HANA_DI_<i class="varname">&lt;metadata&gt;</i></code>:

    The users who are the owners of schemas containing build plug-in metadata


These technical database users are used internally by HDI only. As a general rule, these users are created as restricted database users who do not have any privileges by default \(not even the role `PUBLIC`\), and cannot be used to log on to the database. The only exception to this rule concerns user `S#OO`, who is granted the role `PUBLIC` by default.

For more information, see *Maintaining HDI Containers* in the *Related Information*.



### HDI Container Users

During service binding, the SAP HANA service broker adds the name of the underlying HDI container as a prefix to the name of the container's corresponding HDI users. These users provide access to the HDI container's design-time and run-time file systems, as follows:

-   Design-time access

    HDI User Name: <code><i class="varname">&lt;HDI_Container_Name&gt;</i>_<i class="varname">&lt;GUID&gt;</i>_DT</code>

-   Run-time access

    HDI User Name: <code><i class="varname">&lt;HDI_Container_Name&gt;</i>_<i class="varname">&lt;GUID&gt;</i>_RT</code>


**Related Information**  


[Predefined Database Roles for SAP HDI](predefined-database-roles-for-sap-hdi-bc08eee.md "Several predefined database roles are necessary for operating the SAP HANA Deployment Infrastructure (HDI).")

[Maintaining SAP HDI Containers](../15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

