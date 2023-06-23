<!-- loio996f99709bfa4037a9dcce812b6d57d9 -->

# UNSET USERGROUP Statement \(Session Management\)

Disable the automatic assignment of a user group when creating new users.



<a name="loio996f99709bfa4037a9dcce812b6d57d9__section_vqy_3xh_rrb"/>

## Syntax

```
UNSET USERGROUP
```



<a name="loio996f99709bfa4037a9dcce812b6d57d9__section_yqy_3xh_rrb"/>

## Examples

In this example, the automatic assignment of user group UG1 is disabled.

```
UNSET USERGROUP;

```

To verify the user group is is no longer set, use the CURRENT\_USERGROUP\(\) function. NULL is returned if the user group was successfully unset.

```
SELECT CURRENT_USERGROUP () FROM dummy;
```

