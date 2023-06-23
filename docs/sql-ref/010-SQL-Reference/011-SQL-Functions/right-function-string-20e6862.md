<!-- loio20e6862e75191014af8d997e620c1ee8 -->

# RIGHT Function \(String\)

Returns the specified number of characters/bytes of a string, starting from the right side.



<a name="loio20e6862e75191014af8d997e620c1ee8__sql_function_right_1sql_function_right_syntax"/>

## Syntax

```
RIGHT(<string>, <number>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string to be operated on.



</dd><dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the length of characters or bytes to return, starting from the right side.



</dd>
</dl>



<a name="loio20e6862e75191014af8d997e620c1ee8__sql_function_right_1sql_function_right_description"/>

## Description

Returns the rightmost *<number\>* characters/bytes of string *<string\>*.

Returns an empty string value if *<number\>* is less than 1.

Returns string specified by *<string\>* \(without blank padding\) if the value of *<number\>* is greater than the length of string specified by *<string\>*.



<a name="loio20e6862e75191014af8d997e620c1ee8__sql_function_right_1sql_function_right_examples"/>

## Example

The following example returns the rightmost ***3*** characters of the given string \(***789***\):

```
SELECT RIGHT('HI0123456789', 3) "right" FROM DUMMY;
```

The following example returns the entire input string because the value ***20*** exceeds the length of the input string:

```
SELECT RIGHT('HI0123456789', 20) "right" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

