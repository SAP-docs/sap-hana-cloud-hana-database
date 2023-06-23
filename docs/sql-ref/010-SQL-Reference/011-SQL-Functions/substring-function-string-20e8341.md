<!-- loio20e8341275191014a4cfdcd3c830fc98 -->

# SUBSTRING Function \(String\)

Returns a substring from an input value, starting from a specified position within the input value.



<a name="loio20e8341275191014a4cfdcd3c830fc98__sql_function_substring_1sql_function_substring_syntax"/>

## Syntax

```
SUBSTRING(<string>, <start_position> [, <string_length>])
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string containing the substring. *<string\>* can also be a binary type BLOB or VARBINARY.



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Specifies where the substring starts within the string.



</dd><dt><b>

*<string\_length\>*

</b></dt>
<dd>

Specifies the substring length.



</dd>
</dl>



<a name="loio20e8341275191014a4cfdcd3c830fc98__sql_function_substring_1sql_function_substring_description"/>

## Description

Returns a substring from the specified string starting from *<start\_position\>* within the string. SUBSTRING can return the remaining part of a string from the *<start\_position\>*, or optionally, a number of characters set by the *<string\_length\>* parameter.

-   If *<start\_position\>* is less than 1, then it is considered to be 1.
-   If *<string\_length\>* is less than 1, then an empty string is returned.
-   If *<string\_length\>* is greater than the length of remaining part of *<str\>*, then the remaining part is returned without blank padding.

When used on binary types, SUBSTRING factors in byte length and interprets the offsets, *<start\_position\>* and *<string\_length\>*, as byte positions.



<a name="loio20e8341275191014a4cfdcd3c830fc98__sql_function_substring_1sql_function_substring_examples"/>

## Example

The following example selects two characters from the string ***1234567890*** starting at position ***4***, and returns the value ***45***:

```
SELECT SUBSTRING ('1234567890',4,2) "substring" FROM DUMMY;
```

The following example returns ***'ABCD'*** from the binary value ***x'ABCDEF'***:

```
SELECT SUBSTRING(x'ABCDEF',1,2) "substring" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

