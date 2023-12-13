<!-- loiod230efaad295101481708a3a9aea9254 -->

# STRTOBIN Function \(String\)

Converts all characters in a string into a binary encoding using the specified codepage.



<a name="loiod230efaad295101481708a3a9aea9254__sql_function_strtobin_1sql_function_strtobin_syntax"/>

## Syntax

```
STRTOBIN(<string>, <codepage>)
```



<a name="loiod230efaad295101481708a3a9aea9254__sql_function_strtobin_1sql_function_strtobin_description"/>

## Description

Converts all characters in string *<string\>* into a binary encoding using the defined *<codepage\>*.



<a name="loiod230efaad295101481708a3a9aea9254__sql_function_strtobin_1sql_function_strtobin_examples"/>

## Example

This example converts all characters in the given string to binary `UTF-16BE` encoding, and returns the value ***0041006E0074***:

```
SELECT STRTOBIN ('Ant', 'UTF-16BE') "strtobin" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

