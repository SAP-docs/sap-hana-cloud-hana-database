<!-- loio20e8174b751910149796bd4aad28bdca -->

# SUBSTR\_BEFORE Function \(String\)

Returns a substring from a specified string before the first occurrence of the specified pattern.



<a name="loio20e8174b751910149796bd4aad28bdca__sql_function_substr_before_1sql_function_substr_before_syntax"/>

## Syntax

```
SUBSTR_BEFORE(<string>, <pattern>)
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

Specifies the occurrence within the string that marks the place immediately after the returned substring.



</dd>
</dl>



<a name="loio20e8174b751910149796bd4aad28bdca__sql_function_substr_before_1sql_function_substr_before_description"/>

## Description

Returns a substring from the specified string before the first occurrence of the specified pattern.

-   If *<string\>* does not contain the *<pattern\>* substring, then an empty string is returned.
-   If *<pattern\>* is an empty string, then *<string\>* is returned.
-   If *<string\>* or *<pattern\>* is NULL, then NULL is returned.



<a name="loio20e8174b751910149796bd4aad28bdca__sql_function_substr_before_1sql_function_substr_before_examples"/>

## Example

The following example returns ***Hello***, the part of the given string that is to the left of the first occurrence of `My`:

```
SELECT SUBSTR_BEFORE ('Hello My Friend','My') "substr before" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

