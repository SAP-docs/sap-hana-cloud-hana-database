<!-- loio95fb067f7c5f43f9aaab61a809547d0b -->

# CURRENT\_USERGROUP Function \(Miscellaneous\)

Returns a string containing the current user group name.



<a name="loio95fb067f7c5f43f9aaab61a809547d0b__sql_function_current_schema_1sql_function_current_schema_syntax"/>

## Syntax

```
CURRENT_USERGROUP()
```



<a name="loio95fb067f7c5f43f9aaab61a809547d0b__sql_function_current_schema_1sql_function_current_schema_description"/>

## Description

Returns a string containing the current user group name. NULL is returned if no user group is set.



<a name="loio95fb067f7c5f43f9aaab61a809547d0b__sql_function_current_schema_1sql_function_current_schema_examples"/>

## Example

The following example returns the current user group name:

```
SELECT CURRENT_USERGROUP () FROM DUMMY;
```

