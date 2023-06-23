<!-- loio20e66a2c75191014bac6a279955db665 -->

# REPLACE Function \(String\)

Searches within a string for all occurrences of a specified string and replaces them with another specified string.



<a name="loio20e66a2c75191014bac6a279955db665__sql_function_replace_1sql_function_replace_syntax"/>

## Syntax

```
REPLACE(<original_string>, <search_string>, <replace_string>)
```



## Syntax Elements


<dl>
<dt><b>

*<original\_string\>*

</b></dt>
<dd>

Specifies the string to perform the search and replace within. If *<original\_string\>* is empty, then the result is an empty string.



</dd><dt><b>

*<search\_string\>*

</b></dt>
<dd>

Specifies the pattern to search for in *<original\_string\>*.



</dd><dt><b>

*<replace\_string\>*

</b></dt>
<dd>

Specifies the string to replace *<search\_string\>* with.



</dd>
</dl>



<a name="loio20e66a2c75191014bac6a279955db665__sql_function_replace_1sql_function_replace_description"/>

## Description

Searches in *<original\_string\>* for all occurrences of *<search\_string\>* and replaces them with *<replace\_string\>*.

-   If two overlapping substrings match the *<search\_string\>* in the *<original\_string\>*, then only the first occurrence is replaced.
-   If *<original\_string\>* does not contain an occurrence of *<search\_string\>*, then *<original\_string\>* is returned unchanged.
-   If *<original\_string\>*, *<search\_string\>*, or *<replace\_string\>* are NULL, then NULL is returned.



<a name="loio20e66a2c75191014bac6a279955db665__sql_function_replace_1sql_function_replace_examples"/>

## Example

The following example changes all occurrences of ***DOWN*** in the original string to ***UP***, and returns the value ***UPGRADE UPWARD***:

```
SELECT REPLACE ('DOWNGRADE DOWNWARD','DOWN', 'UP') "replace" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

