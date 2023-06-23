<!-- loio0e34e8f7185e4909a35ed89dc5ee1229 -->

# ABAP\_UPPER Function \(String\)

Converts all characters in the specified string to uppercase.



## Syntax

```
ABAP_UPPER(<string>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

The string to convert to uppercase.



</dd>
</dl>



<a name="loio0e34e8f7185e4909a35ed89dc5ee1229__sql_function_upper_1sql_function_upper_description"/>

## Description

Converts all characters in the *<string\>* parameter to uppercase.



<a name="loio0e34e8f7185e4909a35ed89dc5ee1229__sql_function_upper_1sql_function_upper_examples"/>

## Example

The following example converts the given string to uppercase and returns the value ***ANT***:

```
SELECT ABAP_UPPER ('Ant') "uppercase" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

