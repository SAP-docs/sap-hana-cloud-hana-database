<!-- loio20d74f7f75191014a71ee6a2ae78547f -->

# DROP ROLE Statement \(Access Control\)

Drops a role.



<a name="loio20d74f7f75191014a71ee6a2ae78547f__sql_drop_role_1sql_drop_role_syntax"/>

## Syntax

```
DROP ROLE <role_name>
```



<a name="loio20d74f7f75191014a71ee6a2ae78547f__sql_drop_role_1sql_drop_role_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<role\_name\>*

</b></dt>
<dd>

Drops the specified role, with the optional schema name.

```
<role_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```

*<role\_name\>* must specify an existing role.



</dd>
</dl>



<a name="loio20d74f7f75191014a71ee6a2ae78547f__sql_drop_role_1sql_drop_role_description"/>

## Description

If a role has been granted to a user or another role, then it is revoked when the role is dropped. Revoking a role may lead to making some views inaccessible or making procedures not executable, which occurs if a view or procedures depends on any of the privileges of the dropped role.

Roles that are delivered with the SAP HANA database cannot be dropped. For a list of system roles provided in the SAP HANA database, see the GRANT statement. To see all roles, including custom roles that have been created using the CREATE ROLE statement, query the ROLES system view. To view which roles and privileges have actually been granted, query the GRANTED\_ROLES and GRANTED\_PRIVILEGES system views, respectively.

Note that when dropping a role mapped to an LDAP group, in addition to revoking the role from users to whom it was granted, its mapping to LDAP group is deleted.



<a name="loio20d74f7f75191014a71ee6a2ae78547f__section_zln_bnh_qbb"/>

## Permissions

Database users with the ROLE ADMIN system privilege can drop a role that is not in a role group.

Users with the OPERATOR object privilege on a role group can drop roles that belong to that role group.



<a name="loio20d74f7f75191014a71ee6a2ae78547f__sql_drop_role_1sql_drop_role_examples"/>

## Example

Create a role with the name role\_for\_work\_on\_my\_schema.

```
CREATE ROLE role_for_work_on_my_schema;
```

Drop the role\_for\_work\_on\_my\_schema role.

```
DROP ROLE role_for_work_on_my_schema;
```

**Related Information**  


[CREATE ROLE Statement \(Access Control\)](create-role-statement-access-control-20d4a23.md "Creates a new role.")

[ALTER ROLE Statement \(Access Control\)](alter-role-statement-access-control-c16ff34.md "Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[CREATE ROLEGROUP Statement \(Access Control\)](create-rolegroup-statement-access-control-6cf1932.md "Creates a new role group.")

[DROP ROLEGROUP Statement \(Access Control\)](drop-rolegroup-statement-access-control-9506eaa.md "Drops an existing role group.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](../../020-System-Views-Reference/021-System-Views/effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[ROLEGROUPS System Views](../../020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

[Database Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

