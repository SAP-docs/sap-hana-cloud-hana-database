<!-- loio75262ff0734c40cdb9fe2f2d15b6e750 -->

# CURRENT\_USER\_ID Function \(Miscellaneous\)

Returns the current user's user ID at the current statement context.



<a name="loio75262ff0734c40cdb9fe2f2d15b6e750__sql_function_current_user_1sql_function_current_user_syntax"/>

## Syntax

```
CURRENT_USER_ID()
```



<a name="loio75262ff0734c40cdb9fe2f2d15b6e750__sql_function_current_user_1sql_function_current_user_description"/>

## Description

Returns the current user's user ID at the current statement context. This is the user's ID that is currently at the top of the authorization stack.



<a name="loio75262ff0734c40cdb9fe2f2d15b6e750__section_okj_hkc_jhb"/>

## Example

```
SELECT CURRENT_USER_ID() from DUMMY;
```

