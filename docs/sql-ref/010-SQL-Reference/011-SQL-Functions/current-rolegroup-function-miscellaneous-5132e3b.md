<!-- loio5132e3b06f8a45e9917269e1366e1602 -->

# CURRENT\_ROLEGROUP Function \(Miscellaneous\)

Returns a string containing the current role group name.



<a name="loio5132e3b06f8a45e9917269e1366e1602__sql_function_current_schema_1sql_function_current_schema_syntax"/>

## Syntax

```
CURRENT_ROLEGROUP()
```



<a name="loio5132e3b06f8a45e9917269e1366e1602__sql_function_current_schema_1sql_function_current_schema_description"/>

## Description

Returns a string containing the current role group name. NULL is returned if no role group is set.



<a name="loio5132e3b06f8a45e9917269e1366e1602__sql_function_current_schema_1sql_function_current_schema_examples"/>

## Example

The following example returns the current role group name:

```
SELECT CURRENT_ROLEGROUP () FROM DUMMY;
```

**Related Information**  


[SET ROLEGROUP Statement \(Session Management\)](../012-SQL-Statements/set-rolegroup-statement-session-management-6e62e7e.md "Specify a role group to which every subsequently created role is automatically assigned.")

[UNSET ROLEGROUP Statement \(Session Management\)](../012-SQL-Statements/unset-rolegroup-statement-session-management-2f2ee71.md "Disable the automatic assignment of a role group when creating new roles.")

