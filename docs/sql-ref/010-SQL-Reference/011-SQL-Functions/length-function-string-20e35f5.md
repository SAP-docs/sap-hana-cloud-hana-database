<!-- loio20e35f5275191014ba6df6dc5f8bad5b -->

# LENGTH Function \(String\)

Returns the number of characters in a string.



<a name="loio20e35f5275191014ba6df6dc5f8bad5b__sql_function_length_1sql_function_length_syntax"/>

## Syntax

```
LENGTH(<string>)
```



<a name="loio20e35f5275191014ba6df6dc5f8bad5b__sql_function_length_1sql_function_length_description"/>

## Description

Returns the number of characters in string *<string\>*.

Supplementary plane Unicode characters, each of which occupies 6 bytes in CESU-8 encoding, are counted as two characters.



<a name="loio20e35f5275191014ba6df6dc5f8bad5b__sql_function_length_1sql_function_length_examples"/>

## Example

This example returns the number of characters \(***14***\) contained in the given string:

```
SELECT LENGTH ('length of this') "length" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

