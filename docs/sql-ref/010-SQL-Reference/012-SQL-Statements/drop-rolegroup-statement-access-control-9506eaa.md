<!-- loio9506eaa644934372bf5f7d6117e68e55 -->

# DROP ROLEGROUP Statement \(Access Control\)

Drops an existing role group.



<a name="loio9506eaa644934372bf5f7d6117e68e55__sql_create_role_1sql_create_role_syntax"/>

## Syntax

```
DROP ROLEGROUP <rolegroup_name>
```



<a name="loio9506eaa644934372bf5f7d6117e68e55__sql_create_role_1sql_create_role_description"/>

## Description

A role group must be empty \(contain no roles\) before it can be dropped.



<a name="loio9506eaa644934372bf5f7d6117e68e55__section_jj5_hbd_pbb"/>

## Permissions

Only users with the DROP object privilege on the specified role group can drop the role group.

**Related Information**  


[CREATE ROLEGROUP Statement \(Access Control\)](create-rolegroup-statement-access-control-6cf1932.md "Creates a new role group.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](../../020-System-Views-Reference/021-System-Views/effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[ROLEGROUPS System Views](../../020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

[CREATE ROLE Statement \(Access Control\)](create-role-statement-access-control-20d4a23.md "Creates a new role.")

[ALTER ROLE Statement \(Access Control\)](alter-role-statement-access-control-c16ff34.md "Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.")

[DROP ROLE Statement \(Access Control\)](drop-role-statement-access-control-20d74f7.md "Drops a role.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

