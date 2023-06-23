<!-- loio19918539993849888af17415d43382b5 -->

# SET USERGROUP Statement \(Session Management\)

Specify a user group to which every subsequently created user is automatically assigned.



<a name="loio19918539993849888af17415d43382b5__section_vqy_3xh_rrb"/>

## Syntax

```
SET USERGROUP <usergroup_name>
```



<a name="loio19918539993849888af17415d43382b5__section_xqy_3xh_rrb"/>

## Description

Once set, the default applies to any user created in the current session until the UNSET USERGROUP statement is run or the session ends. This statement is equivalent to using the SET USERGROUP clause within the CREATE USER statement with the SET USERGROUP clause. Once set, the user group remains in effect as the default for all users created until it is unset using the UNSET USERGROUP syntax.

This statement is equivalent to using the SET USERGROUP clause within the CREATE USER statement with the SET USERGROUP clause.

For example:

```
SET USERGROUP <UG1>;
CREATE USER USER1 PASSWORD xxx;
```

Is equivalent to:

```
CREATE USER USER1 PASSWORD xxx SET USERGROUP UG1;
```

Use the CURRENT\_USERGROUP function to verify the current user group set.



<a name="loio19918539993849888af17415d43382b5__section_yqy_3xh_rrb"/>

## Examples

In this example, UG1 is set as the default user group.

```
SET USERGROUP UG1 PASSWORD xxx;
```

To verify the user group is set to UG1, use the CURRENT\_USERGROUP\(\) function.

```
SELECT CURRENT_USERGROUP () FROM dummy;
```

The users User1 and User2 are created. They are automatically assigned to the user group UG1.

```
CREATE USER USER1 PASSWORD xxx;
CREATE USER USER2 PASSWORD xxx;
```

The default UG1 is unset before user USER3 is created.

```
UNSET USERGROUP;
```

```
CREATE USER USER3 PASSWORD xxx;
```

When finished, user USER1 and USR2 are assigned to user group UG1. USER3 is not assigned to any role group.

