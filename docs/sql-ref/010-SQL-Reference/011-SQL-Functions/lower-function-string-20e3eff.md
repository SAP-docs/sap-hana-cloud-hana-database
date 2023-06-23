<!-- loio20e3eff7751910148366dfb349020b4c -->

# LOWER Function \(String\)

Converts all characters in a string to lowercase.



<a name="loio20e3eff7751910148366dfb349020b4c__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
LOWER(<string>)
```



<a name="loio20e3eff7751910148366dfb349020b4c__sql_function_lower_1sql_function_lower_description"/>

## Description

Converts all characters in *<string\>* to lowercase.

The LOWER function is identical to the LCASE function.



<a name="loio20e3eff7751910148366dfb349020b4c__sql_function_lower_1sql_function_lower_examples"/>

## Example

This example converts the given string ***AnT*** to lowercase, and returns the value ***ant***:

```
SELECT LOWER ('AnT') "lower" FROM DUMMY;
```

**Related Information**  


[LCASE Function \(String\)](lcase-function-string-20e23ed.md "Converts all characters in a string to lowercase.")

[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

