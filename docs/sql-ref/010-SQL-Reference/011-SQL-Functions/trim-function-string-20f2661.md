<!-- loio20f266137519101480abfc0aeb6c9dc3 -->

# TRIM Function \(String\)

Returns a string after removing leading and trailing spaces.



<a name="loio20f266137519101480abfc0aeb6c9dc3__sql_function_trim_1sql_function_trim_syntax"/>

## Syntax

```
TRIM([[LEADING | TRAILING | BOTH] <trim_char> FROM] <string> )
```



## Syntax Elements


<dl>
<dt><b>

*<trim\_char\>*

</b></dt>
<dd>

Specifies the characters to be removed from a string.



</dd>
</dl>



<a name="loio20f266137519101480abfc0aeb6c9dc3__sql_function_trim_1sql_function_trim_description"/>

## Description

Returns string *<string\>* after removing leading and trailing spaces. The trimming operation is carried out either from the start \(`LEADING`\), end \(`TRAILING`\) or both \(`BOTH`\) ends of the string.

-   If either *<string\>* or *<trim\_char\>* are NULL values, then `NULL` is returned.
-   If no options are specified, `TRIM` removes both the leading and trailing substring *<trim\_char\>* from string *<string\>*.
-   If *<trim\_char\>* is not specified, then a single blank space is used.



<a name="loio20f266137519101480abfc0aeb6c9dc3__sql_function_trim_1sql_function_trim_examples"/>

## Example

The following example removes the character `a` both at the beginning and at the end of the specified string, and returns the value ***123456789***:

```
SELECT TRIM ('a' FROM 'aaa123456789aa') "trim both" FROM DUMMY;
```

The following example removes the character `a` at the begin of the specified string, and returns the value ***123456789aa***:

```
SELECT TRIM (LEADING 'a' FROM 'aaa123456789aa') "trim leading" FROM DUMMY;
```

