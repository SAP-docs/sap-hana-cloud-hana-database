<!-- loioc16ff341be00433f862b2c064431ec0c -->

# ALTER ROLE Statement \(Access Control\)

Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.



## Syntax

```
ALTER ROLE <role_name>
   { SET ROLEGROUP <rolegroup_name>
   | UNSET ROLEGROUP
   | ADD LDAP GROUP <ldap_group_list>
   | DROP LDAP GROUP <ldap_group_list>
   }
```



## Syntax Elements


<dl>
<dt><b>

*<role\_name\>*

</b></dt>
<dd>

Specifies the name of the role to be altered with optional schema name.

```
<role_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

SET ROLEGROUP *<rolegroup\_name\>*

</b></dt>
<dd>

Grant a role to a role group. If a role was previously assigned to another role group, the new role group replaces the previous role group.



</dd><dt><b>

UNSET ROLEGROUP

</b></dt>
<dd>

Remove a role from its current role group.



</dd><dt><b>

*<ldap\_group\_list\>*

</b></dt>
<dd>

Specifies the Distinguished Name \(DN\) of one or more LDAP groups.

```
<ldap_group_list> ::= <ldap_group_name> [,...] 
<ldap_group_name> ::= <string_literal>
```



</dd>
</dl>



## Description

A local role mapped to an LDAP group can also be granted to another role or a user.

For a list of system roles provided in the SAP HANA database, see the assigned statement. To see all roles, including custom roles that have been created using the CREATE ROLE statement, query the ROLES system view. To view which roles and privileges have actually been granted, query the GRANTED\_ROLES and GRANTED\_PRIVILEGES system views, respectively.



<a name="loioc16ff341be00433f862b2c064431ec0c__section_nck_5hg_qbb"/>

## Permissions

You must have the OPERATOR object privilege on the role group to which the role belongs. To alter roles that have not been assigned to a role group, you must have the ROLE ADMIN system privilege.

To set the role group:

-   If the role is not already assigned to a role group, then the ROLE ADMIN system privilege and the OPERATOR object privilege on the role group the role is being assigned to is required.
-   If the role is already assigned to a role group and you want to change the assigned role group, then the OPERATOR privilege on both the original role group and the replacement role group is required.


To unset the role group, you must have the ROLE ADMIN system privilege and the OPERATOR object privilege on the role group the role is being removed from.



## Examples

Alter a role associated with an LDAP group:

```
ALTER ROLE Securities_DBA 
   ADD LDAP GROUP 'cn=Securities_DBA,OU=Application,OU=Groups,ou=DatabaseAdmins,cn=Users,o=verylargebank.com';
```

Assign the role role1 to the role group RG1:

```
ALTER ROLE role SET ROLEGROUP RG1;
```

**Related Information**  


[Database Roles](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/e7f358b6e85b4610a2b62c5a25755fc0.html "A database role is a collection of privileges that can be granted to either a database user or another role in runtime.") :arrow_upper_right:

[LDAP Group Authorization](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/f494db9664ba45af9bcdd88c7b342405.html "The Lightweight Directory Access Protocol (LDAP) is an application protocol for accessing directory services. If you use an LDAP-compliant directory server to manage users and their access to resources, you can leverage LDAP group membership to authorize SAP HANA database users.") :arrow_upper_right:

[CREATE ROLE Statement \(Access Control\)](create-role-statement-access-control-20d4a23.md "Creates a new role.")

[DROP ROLE Statement \(Access Control\)](drop-role-statement-access-control-20d74f7.md "Drops a role.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[CREATE ROLEGROUP Statement \(Access Control\)](create-rolegroup-statement-access-control-6cf1932.md "Creates a new role group.")

[DROP ROLEGROUP Statement \(Access Control\)](drop-rolegroup-statement-access-control-9506eaa.md "Drops an existing role group.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](../../020-System-Views-Reference/021-System-Views/effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[ROLEGROUPS System Views](../../020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

[SET ROLEGROUP Statement \(Session Management\)](set-rolegroup-statement-session-management-6e62e7e.md "Specify a role group to which every subsequently created role is automatically assigned.")

[UNSET ROLEGROUP Statement \(Session Management\)](unset-rolegroup-statement-session-management-2f2ee71.md "Disable the automatic assignment of a role group when creating new roles.")

