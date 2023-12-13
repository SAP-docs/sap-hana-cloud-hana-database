<!-- loio7fea6509b11c49df955d2790dd2094fb -->

# SAP HDI Administrator Roles

The administration of SAP HANA Deployment Infrastructure \(HDI\) involves a number of tasks that must be performed by different administrator roles.



The following table describes the scope of the various SAP HDI administrator roles and lists the most common tasks the administrators are expected to perform.

**SAP HDI Administrator Scope, Roles, and Tasks**


<table>
<tr>
<th valign="top">

SAP HDI Role

</th>
<th valign="top">

Description

</th>
<th valign="top">

Common Tasks

</th>
</tr>
<tr>
<td valign="top">

Database administrator

</td>
<td valign="top">

The database administrator DBADMIN is needed for creating an HDI administrator.

> ### Note:  
> DBADMIN user privileges are required to create the first HDI administrator, who can then create other HDI administrators. After creation of the first HDI administrator, the DBADMIN user can be deactivated.



</td>
<td valign="top">

Create an HDI administrator

Grant and revoke HDI administrator privileges

</td>
</tr>
<tr>
<td valign="top">

HDI administrator

</td>
<td valign="top">

Configures general SAP HDI parameters, container groups, and manages container group administrator privileges.

</td>
<td valign="top">

Configure SAP HDI

Create and drop container groups

Grant and revoke required access privileges

Maintain container groups

Move containers between container groups

</td>
</tr>
<tr>
<td valign="top">

HDI container-group administrator

</td>
<td valign="top">

Manages the container groups assigned by the SAP HDI administrator. The APIs of a container group “G” are in the `_SYS_DI#G` schema.

</td>
<td valign="top">

Grant and revoke container \(and container-group\) **administrator** access privileges

Import and export containers \(for support purposes\)

Grant and revoke container **user** access privileges \(for support purposes\)

Maintain container groups

</td>
</tr>
<tr>
<td valign="top">

HDI container administrator

</td>
<td valign="top">

Configures and controls access to a container and manages run-time objects in the assigned containers. The APIs of a container “C” are in the `C#DI` schema.

</td>
<td valign="top">

Grant and revoke container **administrator** access privileges

Configure libraries and parameters

Grant and revoke roles from schemas to users

Grant and revoke user access to container schemas

Cancel an asynchronous make operation

</td>
</tr>
</table>

**Related Information**  


[SAP HANA Deployment Infrastructure \(Administration Guide\)](../sap-hana-deployment-infrastructure-in-the-cloud-3ef0ee9.md "Understand the benefits of using the SAP HANA Deployment Infrastructure (HDI).")

