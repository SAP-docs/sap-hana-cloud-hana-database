<!-- loiof59d04cc4cc740ed80fbfd4b422f9842 -->

# ABAP\_LOWER Function \(String\)

Converts all characters in a specified string to lowercase.



<a name="loiof59d04cc4cc740ed80fbfd4b422f9842__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
ABAP_LOWER(<string>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

The string to convert to lowercase.



</dd>
</dl>



<a name="loiof59d04cc4cc740ed80fbfd4b422f9842__sql_function_lower_1sql_function_lower_description"/>

## Description

Converts all characters in the *<string\>* parameter to lowercase.



<a name="loiof59d04cc4cc740ed80fbfd4b422f9842__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example converts the given string to lowercase and returns the value ***ant***:

```
SELECT ABAP_LOWER ('AnT') "lower" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

