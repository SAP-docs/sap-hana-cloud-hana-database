<!-- loio20f4a5fb75191014a75be5e25682ea6f -->

# UNICODE Function \(String\)

Returns an integer containing the Unicode code point of the first character in the specified string.



<a name="loio20f4a5fb75191014a75be5e25682ea6f__sql_function_unicode_1sql_function_unicode_syntax"/>

## Syntax

```
UNICODE(<character>)
```



<a name="loio20f4a5fb75191014a75be5e25682ea6f__sql_function_unicode_1sql_function_unicode_description"/>

## Description

Returns an integer containing the Unicode code point of the first character in the string *<character\>*, or `NULL` if the first character is not a valid encoding.



<a name="loio20f4a5fb75191014a75be5e25682ea6f__sql_function_unicode_1sql_function_unicode_examples"/>

## Example

The following example returns the Unicode code point for the given character \(***35***\):

```
SELECT UNICODE ('#') "unicode" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

