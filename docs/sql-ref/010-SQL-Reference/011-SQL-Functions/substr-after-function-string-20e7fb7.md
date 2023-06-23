<!-- loio20e7fb71751910148292a53e1b4a9bba -->

# SUBSTR\_AFTER Function \(String\)

Returns a substring from a specified string that follows the first occurrence of the specified pattern.



<a name="loio20e7fb71751910148292a53e1b4a9bba__sql_function_substr_after_1sql_function_substr_after_syntax"/>

## Syntax

```
SUBSTR_AFTER(<string>, <pattern>)
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string containing the substring.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

Specifies the occurrence within the string that marks the place immediately before the returned substring.



</dd>
</dl>



<a name="loio20e7fb71751910148292a53e1b4a9bba__sql_function_substr_after_1sql_function_substr_after_description"/>

## Description

Returns a substring from the specified string that follows the first occurrence of the specified pattern.

-   If *<string\>* does not contain the *<pattern\>* substring, then an empty string is returned.
-   If *<pattern\>* is an empty string, then *<string\>* is returned.
-   If *<string\>* or *<pattern\>* is NULL, then NULL is returned.



<a name="loio20e7fb71751910148292a53e1b4a9bba__sql_function_substr_after_1sql_function_substr_after_examples"/>

## Example

This example returns ***Friend***, the part of the given string that is to the right of the first occurrence of ***My***:

```
SELECT SUBSTR_AFTER ('Hello My Friend','My ') "substr after" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

