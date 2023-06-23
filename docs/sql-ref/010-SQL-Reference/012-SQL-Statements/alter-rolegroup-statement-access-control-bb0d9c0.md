<!-- loiobb0d9c0c86f6421cb3c37e48dc513d38 -->

# ALTER ROLEGROUP Statement \(Access Control\)

Creates a new role group.



<a name="loiobb0d9c0c86f6421cb3c37e48dc513d38__sql_create_role_1sql_create_role_syntax"/>

## Syntax

```
ALTER ROLEGROUP <rolegroup_name> [ { ENABLE | DISABLE } ] ROLE ADMIN
```



<a name="loiobb0d9c0c86f6421cb3c37e48dc513d38__sql_create_role_1sql_create_role_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

ENABLE | DISABLE ROLE ADMIN

</b></dt>
<dd>

When enabled, a user with the object privilege GRANTOR is able to rescind the special right on this role group for ROLE ADMINS.



</dd>
</dl>



<a name="loiobb0d9c0c86f6421cb3c37e48dc513d38__sql_create_role_1sql_create_role_description"/>

## Description

OPERATOR, GRANTOR and DROP object privileges are automatically granted on a role group during creation. Even if the NO GRANT TO CREATOR syntax is used when the role group is created, a creator is still granted the GRANTOR privilege, as there is no object ownership concept for this object type.

Use the ROLEGROUPS system view to list existing role groups. The ROLES system view displays in which role group a role is contained, where applicable.



<a name="loiobb0d9c0c86f6421cb3c37e48dc513d38__section_jj5_hbd_pbb"/>

## Permissions

Only users with the CREATE ROLEGROUP system privilege can create role groups.

