<!-- loio20e23edf7519101490eee3271722de36 -->

# LCASE Function \(String\)

Converts all characters in a string to lowercase.



<a name="loio20e23edf7519101490eee3271722de36__sql_function_lcase_1sql_function_lcase_syntax"/>

## Syntax

```
LCASE(<string>)
```



<a name="loio20e23edf7519101490eee3271722de36__sql_function_lcase_1sql_function_lcase_description"/>

## Description

Converts all characters in string *<string\>* to lowercase.

The LCASE function is identical to the LOWER function.



<a name="loio20e23edf7519101490eee3271722de36__sql_function_lcase_1sql_function_lcase_examples"/>

## Example

This example converts all characters of the given string ***TesT*** to lowercase and returns the value ***test***.

```
SELECT LCASE ('TesT') "lcase" FROM DUMMY;
```

**Related Information**  


[LOWER Function \(String\)](lower-function-string-20e3eff.md "Converts all characters in a string to lowercase.")

[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

