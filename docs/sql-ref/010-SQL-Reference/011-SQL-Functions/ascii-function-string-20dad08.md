<!-- loio20dad083751910149584c5724f67488b -->

# ASCII Function \(String\)

Returns the integer ASCII value of the first character in a specified string.



<a name="loio20dad083751910149584c5724f67488b__sql_function_ascii_1sql_function_ascii_syntax"/>

## Syntax

```
ASCII(<string>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string to return the integer ASCII value from.



</dd>
</dl>



<a name="loio20dad083751910149584c5724f67488b__sql_function_ascii_1sql_function_ascii_description"/>

## Description

Returns the integer ASCII value of the first character in a string *<string\>*.



<a name="loio20dad083751910149584c5724f67488b__sql_function_ascii_1sql_function_ascii_examples"/>

## Example

This example converts the first character of the string ***Ant*** into a numeric ASCII value and returns the value ***65***:

```
SELECT ASCII('Ant') "ascii" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

