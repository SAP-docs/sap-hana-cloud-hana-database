<!-- loiof49c1f5c72ee453788bf79f113d83bf9 -->

# Syntax Options in the hdbgrants File

Assign the privileges required by users to access objects in the target schema.



The `.hdbgrants` configuration file enables you to assign privileges to the owner of the synonym object and the application users \(consumers\) of the synonym's target objects in the same way as you would with the SQL `grant` statement.

> ### Note:  
> For information about configuring a corresponding `.hdbrevokes` file that you can use to revoke granted privileges, see *Permissions for Objects in HDI Containers* in *Related Information* below. If both files exist, the `.hdbrevokes` file is processed before the `.hdbgrants` file. Since neither the `.hdbgrants` file nor the `.hdbrevokes` file is an HDI artifact, no HDI plug-in configuration is required.

> ### Sample Code:  
> `external-access.hdbgrants` 
> 
> ```
> {
>   "external-access": {
>     "object_owner": {
>       "system_privileges" : [ 
>         {
>          "privileges" : [ "SYSTEM_PRIVILEGE_1" ],
>          "privileges_with_admin_option" : [ "SYSTEM_PRIVILEGE_2", "SYSTEM_PRIVILEGE_3" ]
>         }
>       ]
>       "global_roles" : [
>         {
>           "roles" : [ "GLOBAL_ROLE_1", "GLOBAL_ROLE_2" ]
>           "roles_with_admin_option" : [ "GLOBAL_ROLE_3", "GLOBAL_ROLE_4" ]
>         }
>       ],
>       "schema_privileges" : [
>         {
>           "schema" : "<schema_name>"   // optional; override schema defined in grantor service
>           "privileges" : [ "INSERT", "UPDATE" ],
>           "privileges_with_grant_option" : [ "SELECT" ]
>         }
>       ],
>       "schema_roles" : [
>         {
>           "schema" : "<schema_name>"   // optional; override schema defined in grantor service
>           "roles" : [ "SCHEMA_ROLE_1", "SCHEMA_ROLE_2" ],
>           "roles_with_admin_option" : [ "SCHEMA_ROLE_3", "SCHEMA_ROLE_4" ]
>         }
>       ],
>       "object_privileges" : [
>         {
>           "schema" : "<schema_name>"   // optional; override schema defined in grantor service
>           "name": "AN_OBJECT",
>           "privileges": [ "INSERT", "UPDATE" ],
>           "privileges_with_grant_option" : [ "SELECT" ]
>         }
>       ],
>       "global_object_privileges" : [
>         {
>           "name" : "A_REMOTE_SOURCE",
>           "type" : "REMOTE SOURCE",
>           "privileges" : [ "CREATE VIRTUAL TABLE" ],
>           "privileges_with_grant_option" : [ "CREATE VIRTUAL PROCEDURE" ]
>         }
>       ]
>     },
>     "application_user": {
>       "system_privileges": [{...}], 
>       "global_roles": [{...}],
>       "schema_privileges": [{...}],
>       "schema_roles": [{...}],
>       "object_privileges": [{...}],
>       "global_object_privileges": [{...}]
>     }
>   }
> }
> ```

In the code example above, the top-level key <code>“external-access”</code> defines the grantors: the names of the bound services which **grant** the privileges required by the various users. One level down, the keys <code>“object_owner”</code> and <code>“application_user”</code> define the grantees: the users to whom the privileges are granted. The <code>“object_owner”</code> key is used to specify the HDI container's object owner; the <code>“application_user”</code> key defines the application users who are bound to the application modules, for example, the Node.js module in a multitarget application. The keys at the third level define the set of roles and privileges to grant, using a structure that is similar to the format used in a `.hdbrole` role-definition file.



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_chg_ctf_cy"/>

## object\_owner

Defines the roles and privileges to be assigned to the owner of the specified container's **object**. In the <code>“object_owner”</code> section, you can also set the following parameters:

-   `system_privileges`
-   `global_roles`

    > ### Note:  
    > `global_roles` supercedes `roles`, which is still supported for backward compatibility or compatibility with `.hdbrole`.

-   `schema_privileges`
-   `schema_roles`

    > ### Note:  
    > `schema_roles` supercedes `container_roles`, which is still supported for backward compatibility.

-   `object_privileges`
-   `global_object_privileges`

The name of the role differs according to whether the target object is in an application schema \(HDI container\) or a classic SAP schema \(for example, ERP\). The names of the privileges can include `system`, `schema`, and `object` \(and `global_oject`\) privileges, as illustrated in the following example:

> ### Sample Code:  
> `.hdbgrants` File for Role Assignment in a Classic Schema
> 
> ```json
> {
>   "external_access": {
>     "object_owner": {
>       "system_privileges": [...], 
>       "global_roles": [{...}],
>       "schema_privileges": [{...}],
>       "schema_roles": [{...}],
>       "object_privileges": [{...}],
>       "global_object_privileges": [{...}]
>     }
>   }
> }
> ```



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_rc5_1ls_xy"/>

## system\_privileges

You can use the <code>“system_privileges”</code> parameter to assign one or more system permissions to the object owner as illustrated in the following example:

> ### Sample Code:  
> System Privileges for the Object Owner in the `hdbgrants` File
> 
> ```json
> {
>   "external_access": {
>     "object_owner" : {
>       "system_privileges" : [
>         {
>          "privileges" : [ "SYSTEM_PRIVILEGE_1" ],
>          "privileges_with_admin_option" : [ "SYSTEM_PRIVILEGE_2", "SYSTEM_PRIVILEGE_3" ]
>         }
>       ]
>     }
>   }
> }
> ```



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_typ_w1r_2y"/>

## global\_roles

Use the <code>“global_roles”</code> property to specify the role \(or roles\) to be assigned to the object owner \(one per HDI container\) and application user by the grantor service, as illustrated in the following example:

> ### Note:  
> `global_roles` supercedes `roles`, which is still supported for backward compatibility or compatibility with `.hdbrole`. Global roles are not supported when referencing an HDI container service; use a **container-local** role where possible, instead.

> ### Sample Code:  
> `SNWD-table.hdbgrants` for Global Roles
> 
> ```json
> {
>   "EPM_XXX-table-grantor": {
>    "object_owner": { 
>       "global_roles": [
>         {
>           "roles" : ["Global_Role1", "Global_Role2"],
>           "roles_with_admin_option" : ["Global_Role3", "Global_Role4"]
>         }
>       ]
>     },
>     "application_user": { 
>       "global_roles": [
>         {
>           "roles" : ["Global_Role1", "Global_Role2"],
>           "roles_with_admin_option" : ["Global_Role3", "Global_Role4"]
>         }
>       ]
>     },
>   }
> }
> 
> ```

The property <code>“roles”</code> is used to specify the name of the role that defines the privileges to assign to users. The role name must be a non-empty string that contains only permitted characters.

In the `.hdbgrants` file, the following types of role names are possible:

-   <code><i class="varname">&lt;RoleName&gt;</i></code>

    If a role name does **not** end with the hash character \(`#`\), for example, `MyRole`, then only privileges without grant options can be included in the role as well as references to any only other roles whose names also do not end with “`#`”.

-   <code><i class="varname">&lt;RoleName&gt;</i>#</code>

    If a role name ends with the hash character \(`#`\), for example, `MyRole#`, it's corresponding role definition can include “with-grant-option” privileges as well as references to other roles whose names also end with `#`. A role whose name ends with `#` can only be granted by means of the HDI APIs to a container’s object owner, for example, <code><i class="varname">&lt;container&gt;</i>#OO</code>.


The roles specified in the `hdbgrants` file must already exist as objects in the database catalog. The corresponding role-definition must define the various privileges required for access to database objects, for example: system, schema, object, and analytic privileges. You can define a user role with an `.hdbrole` artifact. In addition, you will also have to grant the `SELECT` privilege manually to each base objects referenced by the synonym.

> ### Caution:  
> To prevent unnecessary access to the schema via “definer-mode” objects \(procedures, views\), it is recommended to assign different roles to the object owner and the application user. The role for the object owner should provide `GRANT` options; the role for the application user should provide privileges for “invoker-mode” objects \(for example, invoker-mode procedures\). The roles themselves are defined in `.hdbrole` artifacts.



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_ghj_5fs_xy"/>

## schema\_privileges

You can use the <code>“schema_privileges”</code> parameter to assign permissions for the object owner in the target schema, for example, `INSERT` or `UPDATE` for <code>“privileges”</code>. You can also add the grant option to the system privilege, for example, `privileges_with_grant_option` on `SELECT`.

> ### Tip:  
> For `schema_privileges`, you can specify a fixed schema name by using the optional `schema` property in the privilege\(s\) defined in the `.hdbgrants` file.

The `schema` defined in the `schema_privileges` property overrides the schema defined in the grantor service. If no `schema` is defined in `schema_privileges` in the `.hdbgrants` file, then the schema defined in the grantor **service** is used instead.

> ### Sample Code:  
> Schema Privileges for the Object Owner in the `hdbgrants` File
> 
> ```json
> {
>   "external_access": {
>     "object_owner" : {
>       "schema_privileges" : [
>         {
>           "schema" : "<schema_name>"          // optional
>           "privileges" : [ "INSERT", "UPDATE" ],
>           "privileges_with_grant_option" : [ "SELECT" ]
>         }
>       ],
>       ...
>     }
>   }
> }
> ```



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_ey4_r1r_2y"/>

## schema\_roles

Use <code>“schema_roles”</code> to grant schema-local roles to users by means of a grantor service. Multiple roles can be specified in an array, for example, <code>“roles” : ["Schema_Role_1", "Schema_Role_1"]</code>. You can also specify additional roles that include administrator options, for example, <code>“roles_with_admin_option” : ["Schema_Role_3", "Schema_Role_4"]</code>.

> ### Note:  
> `schema_roles` supercedes `container_roles` and works for both normal schemas and HDI containers. The `container_roles` property is still supported for backward compatibility or compatibility with `.hdbrole`.

If the grantor service is bound to a normal database user, you can assign roles with or without administrator options, as illustrated in the following example:

> ### Sample Code:  
> `SNWD-table.hdbgrants` for HDI Schema \(Container\) Roles
> 
> ```json
> {
>   "EPM_XXX-table-grantor": {
>    "object_owner": { 
>       "schema_roles": [
>         {
>           "schema" : "<schema_name>"          // optional
>           "roles" : ["Schema_RoleR1", "Schema_RoleR2"],
>           "roles_with_admin_option" : ["Schema_RoleR3", "Schema_RoleR4"]
>         }
>       ]
>     }
>   }
> }
> 
> ```

For `schema_roles`, you can specify a fixed schema name by using the optional `schema` property in the privilege\(s\) defined in the `.hdbgrants` file. The `schema` defined in the `schema_roles` property overrides the schema defined in the grantor service. If no `schema` is defined in `schema_roles` in the `.hdbgrants` file, then the schema defined in the grantor service is used instead.

> ### Restriction:  
> For container roles, the `roles-with-admin-option` is not supported.

If the grantor service is bound to an HDI container, then it is not possible to use the <code>“roles_with_admin_option”</code>. In the following example, the role assignment works for both normal database-user bindings and bindings to an HDI container, too:

> ### Sample Code:  
> `SNWD-table.hdbgrants` for HDI Schema \(Container\) Roles
> 
> ```json
> {
>   "EPM_XXX-table-grantor": {
>    "object_owner": { 
>       "schema_roles": [
>         {
>           "roles" : ["Schema_RoleR1", "Schema_RoleR2"]
>         }
>       ]
>     }
>   }
> }
> 
> ```

> ### Note:  
> Although the parameter `schema_roles` replaces `container_roles`, `container_roles` will continue to be supported for backward compatibility.



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_n22_bgs_xy"/>

## object\_privileges

For each individual object, you can assign privileges to the object owner: either with the grant option \(for example, `SELECT`\) or **without** \(for example, `INSERT`, `UPDATE`\), as illustrated in the following example:

> ### Sample Code:  
> Object Privileges in the `hdbgrants` File
> 
> ```json
> {
>   "external_access": {
>     "object_owner" : {
>       "object_privileges" : [
>         {
>           "schema" : "<schema_name>"          // optional
>           "name": "AN_OBJECT",
>           "privileges": [ "INSERT", "UPDATE" ],
>           "privileges_with_grant_option" : [ "SELECT" ]
>         }
>       ],
>     }
>   }
> }
> ```

> ### Tip:  
> For `object_privileges`, it is possible to specify a fixed schema name by using the optional `schema` property in the privilege\(s\) defined in the `.hdbgrants` file.

The `schema` defined in the `object_privileges` property overrides the schema defined in the grantor service. If no fixed `schema` is defined in the object privilege, then the schema defined in the grantor service is used instead.

Object privileges are not supported when referencing an HDI container service. Instead, deploy a role with the desired object privileges to the referenced HDI container and then grant the deployed role in the `.hdbgrants` file using the `"schema_roles"` property.



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_ezx_zfs_xy"/>

## global\_object\_privileges

For each individual object, you can assign global privileges to the object owner: either with the grant option \(for example, `SELECT`\) or **without** \(for example, `INSERT`, `UPDATE`\), as illustrated in the following example:

> ### Sample Code:  
> Global Object Privileges in the `hdbgrants` File
> 
> ```json
> {
>   "external_access": {
>     "object_owner" : {
>       "global_object_privileges" : [
>         {
>           "name" : "A_REMOTE_SOURCE",
>           "type" : "REMOTE SOURCE",
>           "privileges" : [ "CREATE VIRTUAL TABLE" ],
>           "privileges_with_grant_option" : [ "CREATE VIRTUAL PROCEDURE" ]
>         }
>       ]
>     }
>   }
> }
> ```



<a name="loiof49c1f5c72ee453788bf79f113d83bf9__section_a2m_ctf_cy"/>

## application\_user

Defines the roles and permissions to be assigned to the user of the multitarget application that consumes the defined synonym and requires access to the corresponding schemas containing the target objects referenced by the synonyms. The following example shows how to assign `application_user` to the privileges defined in the externally created role `"EPM_XXX::RoleR1"`.

> ### Tip:  
> <code>“application_user”</code>” does not refer to a real user; it refers to the technical user associated with the global “`access_role`” required for access to the corresponding run-time container. The “`access_role`” is assigned a set of default permissions for the run-time schema, for example: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `EXECUTE`, `CREATE TEMPORARY TABLE`, and `SELECT CDS METADATA`.

-   `system_privileges`
-   `global_roles`

    > ### Note:  
    > `global_roles` supercedes `roles`, which is still supported for backward compatibility or compatibility with `.hdbrole`.

-   `schema_privileges`
-   `schema_roles`

    > ### Note:  
    > `schema_roles` supercedes `container_roles`, which is still supported for backward compatibility or compatibility with `.hdbrole`.

-   `object_privileges`
-   `global_object_privileges`

> ### Sample Code:  
> `.hdbgrants` File for Role Assignment in a Classic Schema
> 
> ```json
> "application_user": {
>   "system_privileges": [...], 
>   "global_roles": [{...}],
>   "schema_privileges": [{...}],
>   "schema_roles": [{...}],
>   "object_privileges": [{...}],
>   "global_object_privileges": [{...}]
> },
> ```

**Related Information**  


[Using Synonyms to Access External Schemas and Objects](using-synonyms-to-access-external-schemas-and-objects-bdc9f7a.md "Deploy synonyms to enable cross-container access to external objects.")

[Database Synonyms in SAP HANA Cloud](database-synonyms-in-sap-hana-cloud-556452c.md "You can use synonyms in SAP HANA Cloud to enable access to objects that are not in the same schema or application container.")

[Roles (.hdbrole and .hdbroleconfig)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/625d7733c30b4666b4a522d7fa68a550.html "Transform a design-time role resource (.hdbrole) into a run-time role object.") :arrow_upper_right:

[Permissions for Objects in HDI Containers](permissions-for-objects-in-hdi-containers-79e8664.md "The owner of a container object needs additional privileges to the ones assigned by default.")

[SAP HDI Security in the Context of Cloud Foundry (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/4457f759107d4985bd80532c9e023227.html "An overview of the security considerations to bear in mind when enabling SAP HDI for use in the context of Cloud Foundry.") :arrow_upper_right:

