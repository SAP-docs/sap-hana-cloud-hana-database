<!-- loio6e62e7ef3b7949eb83c47115dc47e2c8 -->

# SET ROLEGROUP Statement \(Session Management\)

Specify a role group to which every subsequently created role is automatically assigned.



<a name="loio6e62e7ef3b7949eb83c47115dc47e2c8__section_vqy_3xh_rrb"/>

## Syntax

```
SET ROLEGROUP <rolegroup_name>
```



<a name="loio6e62e7ef3b7949eb83c47115dc47e2c8__section_xqy_3xh_rrb"/>

## Description

Once set, the default applies to any role created in the current session until the UNSET ROLEGROUP statement is run or the session ends. This statement is equivalent to using the SET ROLEGROUP clause within the CREATE ROLE statement with the SET ROLEGROUP clause. Once set, the role group remains in effect as the default for all roles created until it is unset using the UNSET ROLEGROUP syntax.

This statement is equivalent to using the SET ROLEGROUP clause within the CREATE ROLE statement with the SET ROLEGROUP clause.

For example:

```
SET ROLEGROUP <RG1>;
CREATE ROLE R1;
```

Is equivalent to:

```
CREATE ROLE R1 SET ROLEGROUP RG1;
```

Use the CURRENT\_ROLEGROUP function to verify the current role group set.



<a name="loio6e62e7ef3b7949eb83c47115dc47e2c8__section_yqy_3xh_rrb"/>

## Examples

In this example, RG1 is set as the default role group.

```
SET ROLEGROUP RG1;

```

To verify the role group is set to RG1, use the CURRENT\_ROLEGROUP\(\) function.

```
SELECT CURRENT_ROLEGROUP () FROM dummy;
```

The roles R1 and R2 are created. They are automatically assigned to the role group RG1.

```
CREATE ROLE R1;
CREATE ROLE R2;
```

The default RG1 is unset before role R3 is created.

```
UNSET ROLEGROUP;
```

```
CREATE ROLE R3;

```

When finished, role R1 and R2 are assigned to role group RG1. R3 is not assigned to any role group.

**Related Information**  


[CURRENT\_ROLEGROUP Function \(Miscellaneous\)](../011-SQL-Functions/current-rolegroup-function-miscellaneous-5132e3b.md "Returns a string containing the current role group name.")

[UNSET ROLEGROUP Statement \(Session Management\)](unset-rolegroup-statement-session-management-2f2ee71.md "Disable the automatic assignment of a role group when creating new roles.")

[CREATE ROLE Statement \(Access Control\)](create-role-statement-access-control-20d4a23.md "Creates a new role.")

[ALTER ROLE Statement \(Access Control\)](alter-role-statement-access-control-c16ff34.md "Sets or unsets the role group of a role, and adds or drops the mapping of LDAP groups to a role.")

