<!-- loio20e6da0175191014a632fe729f839d44 -->

# RTRIM Function \(String\)

Returns a string trimmed of all trailing spaces.



<a name="loio20e6da0175191014a632fe729f839d44__sql_function_rtrim_1sql_function_rtrim_syntax"/>

## Syntax

```
RTRIM(<string> [,<remove_set> ])
```



<a name="loio20e6da0175191014a632fe729f839d44__sql_function_rtrim_1sql_function_rtrim_description"/>

## Description

Returns a string trimmed of all trailing spaces. If *<remove\_set\>* is specified, then `RTRIM` removes all the characters contained in the specified set from the end of the string. This process continues until a character that is not in the *<remove\_set\>* has been reached.

*<remove\_set\>* is treated as a set of characters and not as a search string.



<a name="loio20e6da0175191014a632fe729f839d44__sql_function_rtrim_1sql_function_rtrim_examples"/>

## Example

This example removes all trailing `a` and `b` characters from the given string, and returns the value ***endabA***:

```
SELECT RTRIM ('endabAabbabab','ab') "rtrim" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

