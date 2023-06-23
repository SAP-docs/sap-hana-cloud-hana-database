<!-- loio20db6dd675191014a4fd978452f92bbd -->

# CHAR Function \(String\)

Returns the character that has the ASCII value of the specified number.



<a name="loio20db6dd675191014a4fd978452f92bbd__sql_function_char_1sql_function_char_syntax"/>

## Syntax

```
CHAR(<number>)
```



## Syntax Elements


<dl>
<dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the number with the ASCII value that the function converts into a character.



</dd>
</dl>



<a name="loio20db6dd675191014a4fd978452f92bbd__sql_function_char_1sql_function_char_description"/>

## Description

Returns the character that has the ASCII value of the specified number.



<a name="loio20db6dd675191014a4fd978452f92bbd__sql_function_char_1sql_function_char_examples"/>

## Example

This example converts three ASCII values into characters and concatenates the results, returning the string ***Ant***:

```
SELECT CHAR (65) || CHAR (110) || CHAR (116) "character" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

