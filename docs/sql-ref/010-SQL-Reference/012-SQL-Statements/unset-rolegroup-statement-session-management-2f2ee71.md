<!-- loio2f2ee71a3da04b248216d7915e85cb11 -->

# UNSET ROLEGROUP Statement \(Session Management\)

Disable the automatic assignment of a role group when creating new roles.



<a name="loio2f2ee71a3da04b248216d7915e85cb11__section_vqy_3xh_rrb"/>

## Syntax

```
UNSET ROLEGROUP
```



<a name="loio2f2ee71a3da04b248216d7915e85cb11__section_yqy_3xh_rrb"/>

## Examples

In this example, the automatic assignment of role group RG1 is disabled.

```
UNSET ROLEGROUP;

```

To verify the role group is is no longer set, use the CURRENT\_ROLEGROUP\(\) function. NULL is returned if the role group was successfully unset.

```
SELECT CURRENT_ROLEGROUP () FROM dummy;
```

**Related Information**  


[CURRENT\_ROLEGROUP Function \(Miscellaneous\)](../011-SQL-Functions/current-rolegroup-function-miscellaneous-5132e3b.md "Returns a string containing the current role group name.")

[SET ROLEGROUP Statement \(Session Management\)](set-rolegroup-statement-session-management-6e62e7e.md "Specify a role group to which every subsequently created role is automatically assigned.")

