<!-- loio20e59b1d751910149321c5c68efb5905 -->

# NCHAR Function \(String\)

Returns the Unicode character with the specified code number.



<a name="loio20e59b1d751910149321c5c68efb5905__sql_function_nchar_1sql_function_nchar_syntax"/>

## Syntax

```
NCHAR(<number>)
```



<a name="loio20e59b1d751910149321c5c68efb5905__sql_function_nchar_1sql_function_nchar_description"/>

## Description

Returns the Unicode character with the specified code number *<number\>*.



<a name="loio20e59b1d751910149321c5c68efb5905__sql_function_nchar_1sql_function_nchar_examples"/>

## Example

This example returns the Unicode character \(***A***\) with the code number `65`:

```
SELECT NCHAR (65) "nchar" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

