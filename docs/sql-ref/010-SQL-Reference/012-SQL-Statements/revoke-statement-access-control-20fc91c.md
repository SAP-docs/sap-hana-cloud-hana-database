<!-- loio20fc91cb75191014ac15eb4d6f2d7dde -->

# REVOKE Statement \(Access Control\)

Revokes roles or privileges for the specified objects from a user or role.



<a name="loio20fc91cb75191014ac15eb4d6f2d7dde__sql_revoke_1sql_revoke_syntax"/>

## Syntax

```
REVOKE <system_privilege>,... FROM <grantee>
 | REVOKE <source_privilege>[,.<source_privilege>.. ON REMOTE SOURCE <source_name> FROM <grantee> 
 | REVOKE <schema_privilege>,... ON SCHEMA <schema_name> FROM <grantee> 
 | REVOKE <object_privilege>,... ON <object_name> FROM <grantee> 
 | REVOKE <role_name>,... FROM <grantee> [ GRANTED BY <grantor> ] 
 | REVOKE <role_in_a_rolegroup>,... FROM <grantee> [ GRANTED BY <grantee> ]
 | REVOKE { ALTER | DROP | REFERENCES } ON { JWT | SAML | X509 } PROVIDER <provider_name> FROM <grantee>
 | REVOKE { ALTER | DROP | REFERENCES } ON PSE <pse_name> FROM <grantee>
 | REVOKE <user_role_group_privilege>,...] ON { USERGROUP usergroup_name | ROLEGROUP rolegroup_name } FROM grantee [ GRANTED BY <grantee> ]
 | REVOKE { ALTER | DROP | REFERENCES } ON ADAPTER <adapter_name> FROM <grantee>
 | REVOKE STRUCTURED PRIVILEGE <privilege_name> FROM <grantee>
```



<a name="loio20fc91cb75191014ac15eb4d6f2d7dde__sql_revoke_1sql_revoke_syntax_elements"/>

## Syntax Elements

For the definition of all of the other syntax elements not listed here, see the [GRANT Statement \(Access Control\)](grant-statement-access-control-20f674e.md) statement.


<dl>
<dt><b>

GRANTED BY *<grantor\>*

</b></dt>
<dd>

Allows a user with the ROLE ADMIN privilege to revoke a role that they did not grant. *<grantor\>* specifies the user who granted *<role\_name\>* to *<grantee\>*.



</dd><dt><b>

GRANTED BY *<grantee\>*

</b></dt>
<dd>

Allows you to revoke the object privileges on a role group that was originally granted by a specific user. The *<grantee\>* could be a user or a role group.



</dd>
</dl>



<a name="loio20fc91cb75191014ac15eb4d6f2d7dde__section_jb3_ktc_pbb"/>

## Permissions

Only the user that granted a specific privilege can revoke it.

For users without ROLE ADMIN privileges, only the user that granted a specific role can revoke it.

The OPERATOR object privilege on the role group is required to revoke a role granted by a role group.



<a name="loio20fc91cb75191014ac15eb4d6f2d7dde__section_tmt_qvy_ddb"/>

## Description

If a user has been granted a role, then you cannot revoke a subset of the privileges belonging to that role. To grant a subset of privileges contained within a role, revoke the entire role and grant the required privileges separately.

Revoking a privilege or a role can lead to some views becoming inaccessible or procedures that the user can no longer execute. This situation occurs if a view or a procedure depends on a revoked privilege or on one of the privileges the role had.

Revoking a privilege that had been granted with WITH GRANT OPTION or with WITH ADMIN OPTION results in recursive revocation of privileges. Privileges are not only revoked from the user specified in the command, but also from all the users and roles that were granted that privilege directly or indirectly by the specified user.

Privileges can be granted to a user or role by more than one grantor; revocation of a privilege by one grantor user does not necessarily mean that the privilege is revoked from the user or role.



<a name="loio20fc91cb75191014ac15eb4d6f2d7dde__sql_revoke_1sql_revoke_examples"/>

## Example

Create a new user named `worker`.

```
CREATE USER worker PASSWORD His_Password_1;
```

Create a new role named `role_for_work_on_my_schema`.

```
CREATE ROLE role_for_work_on_my_schema;
```

Create a new schema named `my_schema`.

```
CREATE SCHEMA my_schema OWNED BY system;
```

Create a new table named `work_done` in the schema.

```
CREATE ROW TABLE my_schema.work_done (t TIMESTAMP, user NVARCHAR (256), work_done NVARCHAR (256));
```

Grant the SELECT privilege on any object privilege in `my_schema` to the role `role_for_work_on_my_schema`.

```
GRANT SELECT ON SCHEMA my_schema TO role_for_work_on_my_schema;
```

Grant the INSERT privilege for the `work_done` table to the role `role_for_work_on_my_schema`.

```
GRANT INSERT ON my_schema.work_done TO role_for_work_on_my_schema;
```

Grant the `role_for_work_on_my_schema` role to the `worker` user.

```
GRANT role_for_work_on_my_schema TO worker;
```

Grant TRACE ADMIN privilege for the `worker` user.

```
GRANT TRACE ADMIN TO worker WITH ADMIN OPTION;
```

Grant the DELETE privilege from the `work_done` table to the `worker` user.

```
GRANT DELETE ON my_schema.work_done TO worker WITH GRANT OPTION;
```

Revoke from the role `role_for_work_on_my_schema` the privilege to select from `my_schema`.

```
REVOKE SELECT ON SCHEMA my_schema FROM role_for_work_on_my_schema;
```

Revoke TRACE ADMIN privilege from the `worker` user.

```
REVOKE TRACE ADMIN FROM worker;
```

Revoke the LINKED DATABASE privilege from user `myuser1` using remote source `myremotesys`.

```
REVOKE LINKED DATABASE ON REMOTE SOURCE myremotesys FROM myuser1;
```

**Related Information**  


[GRANT Statement \(Access Control\)](grant-statement-access-control-20f674e.md "Grants various types of privileges to users and roles.")

[CREATE USER Statement \(Access Control\)](create-user-statement-access-control-20d5ddb.md "Creates a new database user.")

[ALTER USER Statement \(Access Control\)](alter-user-statement-access-control-20d3459.md "Modifies the database user.")

[USERS System View](../../020-System-Views-Reference/021-System-Views/users-system-view-2102609.md "Lists all users.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[Granting and Revoking Privileges and Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_3_QRC/en-US/c719b2e7d9761014b9d798770c3d0958.html "To be able to grant and revoke privileges and roles to and from users and roles, the granting or revoking user must meet a number of prerequisites.") :arrow_upper_right:

