<!-- loio20e43dd175191014bee9ed5ab9ae44f7 -->

# LTRIM Function \(String\)

Returns a string, trimmed of all leading spaces.



<a name="loio20e43dd175191014bee9ed5ab9ae44f7__sql_function_ltrim_1sql_function_ltrim_syntax"/>

## Syntax

```
LTRIM(<string> [, <remove_set>])
```



<a name="loio20e43dd175191014bee9ed5ab9ae44f7__sql_function_ltrim_1sql_function_ltrim_description"/>

## Description

Returns string *<string\>*, trimmed of all leading spaces. If *<remove\_set\>* is specified, LTRIM removes all the characters contained in this set from the start of string *<string\>*. This process continues until a character that is not in *<remove\_set\>* is reached.

*<remove\_set\>* is treated as a set of characters and not as a search string.



<a name="loio20e43dd175191014bee9ed5ab9ae44f7__sql_function_ltrim_1sql_function_ltrim_examples"/>

## Example

This example removes all leading `a` and `b` characters from the given string and returns the value Aabend:

```
SELECT LTRIM ('babababAabend','ab') "ltrim" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

