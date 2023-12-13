<!-- loio6cf193279bb4481faf8f2c77f137250c -->

# CREATE ROLEGROUP Statement \(Access Control\)

Creates a new role group.



<a name="loio6cf193279bb4481faf8f2c77f137250c__sql_create_role_1sql_create_role_syntax"/>

## Syntax

```
CREATE ROLEGROUP <rolegroup_name> [ NO GRANT TO CREATOR ] [ ENABLE ROLE ADMIN ]
```



<a name="loio6cf193279bb4481faf8f2c77f137250c__sql_create_role_1sql_create_role_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

NO GRANT TO CREATOR

</b></dt>
<dd>

Prevents the automatic granting of the OPERATOR and DROP object privileges on the role group to the user creating the role group. The GRANTOR privilege is still be granted to the creator.



</dd>
</dl>


<dl>
<dt><b>

ENABLE ROLE ADMIN

</b></dt>
<dd>

Allows a user with the object privilege GRANTOR on a role group to allow any user with the system privilege ROLE ADMIN to act as if they have the object privilege OPERATOR on the role group.



</dd>
</dl>



<a name="loio6cf193279bb4481faf8f2c77f137250c__sql_create_role_1sql_create_role_description"/>

## Description

When a user creates a role group they are granted the OPERATOR, GRANTOR and DROP object privileges on the role group. Even when the NO GRANT TO CREATOR syntax is used, a creator is still granted the GRANTOR privilege, as there is no object ownership concept for this object type.

Use the ROLEGROUPS system view to list existing role groups. The ROLES system view displays in which role group a role is contained, where applicable.



<a name="loio6cf193279bb4481faf8f2c77f137250c__section_jj5_hbd_pbb"/>

## Permissions

Only users with the CREATE ROLEGROUP system privilege can create role groups.

**Related Information**  


[DROP ROLEGROUP Statement \(Access Control\)](drop-rolegroup-statement-access-control-9506eaa.md "Drops an existing role group.")

[EFFECTIVE\_PRIVILEGE\_GRANTEES System View](../../020-System-Views-Reference/021-System-Views/effective-privilege-grantees-system-view-2a8987c.md "Provides information about who was granted (explicitly or implicitly via roles) a specified privilege.")

[EFFECTIVE\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/effective-privileges-system-view-20a2f3e.md "Provides the privileges of the specified user.")

[ROLEGROUPS System Views](../../020-System-Views-Reference/021-System-Views/rolegroups-system-views-5e2b4b9.md "Shows available role groups.")

[CREATE ROLE Statement \(Access Control\)](create-role-statement-access-control-20d4a23.md "Creates a new role.")

[ALTER ROLE Statement \(Access Control\)](alter-role-statement-access-control-c16ff34.md "Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.")

[DROP ROLE Statement \(Access Control\)](drop-role-statement-access-control-20d74f7.md "Drops a role.")

[ROLES System View](../../020-System-Views-Reference/021-System-Views/roles-system-view-20cd8af.md "Shows available roles.")

[GRANTED\_ROLES System View](../../020-System-Views-Reference/021-System-Views/granted-roles-system-view-20a5c3b.md "Provides information about roles granted to users or other roles.")

[GRANTED\_PRIVILEGES System View](../../020-System-Views-Reference/021-System-Views/granted-privileges-system-view-20a5958.md "Provides information about privileges and roles granted to users.")

[Role Groups](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/33dfc7ed4ff648abbbaab4aefb7070d4.html "Role groups support a separation of role management tasks. This is useful if you want different aspects of your authorization setup managed by different administrators. In an SAP HANA Cloud environment, SAP uses role groups to separate the management of customer-owned roles and SAP-owned roles and therefore the authorization on underlying objects.") :arrow_upper_right:

