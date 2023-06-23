<!-- loio6dc0adae9f4c4ebaa46cbe6b5f636ee7 -->

# DROP USERGROUP Statement \(Access Control\)

Removes a user group from the database.



<a name="loio6dc0adae9f4c4ebaa46cbe6b5f636ee7__section_dd5_qhm_nz"/>

## Syntax

```
DROP USERGROUP <usergroup_name>
```



<a name="loio6dc0adae9f4c4ebaa46cbe6b5f636ee7__section_nrq_3hm_nz"/>

## Syntax Elements


<dl>
<dt><b>

*<usergroup\_name\>*

</b></dt>
<dd>

The name of the user group.



</dd>
</dl>



<a name="loio6dc0adae9f4c4ebaa46cbe6b5f636ee7__section_ydr_jhm_nz"/>

## Description

You must remove all users from the user group before you can drop it. An error is returned if you attempt to drop a user group that still has users.



<a name="loio6dc0adae9f4c4ebaa46cbe6b5f636ee7__section_ezd_vd2_pbb"/>

## Permissions

You must have the CREATE USERGROUP system privilege.



<a name="loio6dc0adae9f4c4ebaa46cbe6b5f636ee7__section_kwk_mhm_nz"/>

## Example

The following statement drops a \(fictitious\) user group named ***MyUserGroup***;

```
DROP USERGROUP MyUserGroup;
```

**Related Information**  


[ALTER USER Statement \(Access Control\)](alter-user-statement-access-control-20d3459.md "Modifies the database user.")

[CREATE USERGROUP Statement \(Access Control\)](create-usergroup-statement-access-control-9869125.md "Creates a usergroup.")

[ALTER USERGROUP Statement \(Access Control\)](alter-usergroup-statement-access-control-aa94ca8.md "Alters a usergroup.")

[USERGROUPS System View](../../020-System-Views-Reference/021-System-Views/usergroups-system-view-ac342d0.md "Provides details on all user groups.")

