<!-- loiobc08eee29a0c4edd9393968f91d0228f -->

# Predefined Database Roles for SAP HDI

Several predefined database roles are necessary for operating the SAP HANA Deployment Infrastructure \(HDI\).

> ### Note:  
> The following roles are SQL-based roles that are available in the catalog of the SAP HANA database.


<table>
<tr>
<th valign="top">

Role



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

`_SYS_DI_OO_DEFAULTS` 



</td>
<td valign="top">

This role contains the set of default privileges that are granted to all HDI container object-owner users \(<code><i class="varname">&lt;container&gt;</i></code>\#OO users\). SAP HANA Deployment Infrastructure \(HDI\) uses this role internally to grant default privileges instead of using the `PUBLIC` role. It contains only privileges to `SYS` views where additional security checks apply.

The role contains `SELECT` privileges on the views: `SYS.DUMMY`, `SYS.PROCEDURES`, `SYS.PROCEDURE_PARAMETERS`, `SYS.TABLES`, `SYS.TABLE_COLUMNS`.

This role is not intended to be granted to database users.

> ### Note:  
> Do **not** extend this role in a production system.



</td>
</tr>
<tr>
<td valign="top">

<code>_SYS_DI#<i class="varname">&lt;container_group&gt;</i>._SYS_DI_OO_DEFAULTS</code>



</td>
<td valign="top">

This role contains the set of default privileges that are granted to all HDI container object-owner users \(<code><i class="varname">&lt;container&gt;</i></code>\#OO users\) who are part of the container group <code><i class="varname">&lt;container_group&gt;</i></code>.

The role does not contain any privileges by default. Privileges granted to a container group-specific role will automatically be available to all HDI container object-owner users of the specified container group.

> ### Note:  
> This role is not intended to be granted to database users.



</td>
</tr>
</table>

**Related Information**  


[SAP HDI Security](sap-hdi-security-d9e5051.md "An overview of the tools used to configure and ensure security in the SAP HANA Deployment Infrastructure (HDI).")

[SAP HDI Users](sap-hdi-users-40faae2.md "A list of the predefined users which SAP HDI relies on and a description of their respective role.")

