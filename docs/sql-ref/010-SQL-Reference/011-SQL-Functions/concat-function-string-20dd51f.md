<!-- loio20dd51f775191014990682ac74bbefe8 -->

# CONCAT Function \(String\)

Returns a combined string consisting of two specified strings.



<a name="loio20dd51f775191014990682ac74bbefe8__sql_function_concat_1sql_function_concat_syntax"/>

## Syntax

```
CONCAT(<string1>, <string2>)
```



## Syntax Elements


<dl>
<dt><b>

*<string1\>*

</b></dt>
<dd>

Specifies the first string to combine.



</dd><dt><b>

*<string2\>*

</b></dt>
<dd>

Specifies the second string to combine.



</dd>
</dl>



<a name="loio20dd51f775191014990682ac74bbefe8__sql_function_concat_1sql_function_concat_description"/>

## Description

Returns a combined string consisting of *<string1\>* followed by *<string2\>*. The concatenation operator \(||\) is identical to this function.

The maximum length of the concatenated string is 8,388,607. If the string length is longer than the maximum length, an exception is thrown. Exceptionally, an implicit truncation is performed when converting an NCLOB typed value with a size greater than the maximum length of an NVARCHAR value.

If one ore both arguments are NULL, the function returns NULL.



<a name="loio20dd51f775191014990682ac74bbefe8__sql_function_concat_1sql_function_concat_examples"/>

## Example

This example concatenates the specified string arguments and returns the value ***Cat***:

```
SELECT CONCAT ('C', 'at') "concat" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

