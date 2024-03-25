<!-- loio20d4a23b75191014a182b123906d5b16 -->

# CREATE ROLE Statement \(Access Control\)

Creates a new role.



<a name="loio20d4a23b75191014a182b123906d5b16__sql_create_role_1sql_create_role_syntax"/>

## Syntax

```
CREATE ROLE <role_name> [ SET ROLEGROUP <rolegroup_name> ]
   [ LDAP GROUP <ldap_group_list> ] [ NO GRANT TO CREATOR ]
```



<a name="loio20d4a23b75191014a182b123906d5b16__sql_create_role_1sql_create_role_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<role\_name\>*

</b></dt>
<dd>

Specifies the name of the role to be created with an optional schema name.

```
<role_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```

The specified role name must not be identical to the name of an existing user, user group, role or role group. If no schema is specified, then a global role is created. If you specify a schema as part of the role name, then the role name is local to that schema only and does not collide with roles with the same name in other schemas or in the global namespace. Dropping a schema drops all roles contained in the namespace of that schema.



</dd><dt><b>

SET ROLEGROUP *<rolegroup\_name\>*

</b></dt>
<dd>

Create and assign a new role to an existing role group. Requires the OPERATOR object privilege on the role group being specified. If you have the OPERATOR object privilege on exactly one role group and you do not have the ROLE ADMIN system privilege, then you can omit the SET ROLEGROUP syntax, and the system automatically assigns the role to the only possible role group.



</dd><dt><b>

*<ldap\_group\_list\>*

</b></dt>
<dd>

Specifies the Distinguished Name \(DN\) of one or more LDAP groups.

```
<ldap_group_list> ::= <ldap_group_name> [,...] 
<ldap_group_name> ::= <string_literal>
```

A local role mapped to an LDAP group can also be granted to another role or a user as before. Note that when dropping an LDAP-mapped role using DROP ROLE, in addition to revoking the role from users to whom it was granted, its mapping to the LDAP group is deleted.



</dd><dt><b>

NO GRANT TO CREATOR

</b></dt>
<dd>

Prevents the automatic granting of the role to the user creating the role.



</dd>
</dl>



<a name="loio20d4a23b75191014a182b123906d5b16__sql_create_role_1sql_create_role_description"/>

## Description

For a list of system roles provided in the SAP HANA database, see the GRANT statement. To see all roles, including custom roles that have been created using the CREATE ROLE statement, query the ROLES system view. To view which roles and privileges have actually been granted, query the GRANTED\_ROLES and GRANTED\_PRIVILEGES system views, respectively.



<a name="loio20d4a23b75191014a182b123906d5b16__section_jj5_hbd_pbb"/>

## Permissions

Users with the ROLE ADMIN system privilege can create roles that are not part of a role group.

Users with the OPERATOR privilege on a role group can create roles within that role group.



<a name="loio20d4a23b75191014a182b123906d5b16__sql_create_role_1sql_create_role_examples"/>

## Examples

Create a role with the name role\_for\_work\_on\_my\_schema:

```
CREATE ROLE role_for_work_on_my_schema NO GRANT TO CREATOR;
```

Create a role with the name role1 that is assigned to role group RG1:

```
CREATE ROLE role1 SET ROLEGROUP RG1;
```

Create a role and associated it with an LDAP group:

```
CREATE ROLE Securities_DBA 
 LDAP GROUP 'cn=Securities_DBA,OU=Application,OU=Groups,ou=DatabaseAdmins,cn=Users,o=largebank.com';
```

**Related Information**  


[DROP ROLE Statement \(Access Control\)](drop-role-statement-access-control-20d74f7.md "Drops a role.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[CREATE ROLEGROUP Statement \(Access Control\)](create-rolegroup-statement-access-control-6cf1932.md "Creates a new role group.")

[DROP ROLEGROUP Statement \(Access Control\)](drop-rolegroup-statement-access-control-9506eaa.md "Drops an existing role group.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](../../020-System-Views-Reference/021-System-Views/effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[ROLEGROUPS System Views](../../020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

[Database Roles](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[Role Groups](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2024_1_QRC/en-US/33dfc7ed4ff648abbbaab4aefb7070d4.html "Role groups support a separation of role management tasks. This is useful if you want different aspects of your authorization setup managed by different administrators. In an SAP HANA Cloud environment, SAP uses role groups to separate the management of customer-owned roles and SAP-owned roles and therefore the authorization on underlying objects.") :arrow_upper_right:

