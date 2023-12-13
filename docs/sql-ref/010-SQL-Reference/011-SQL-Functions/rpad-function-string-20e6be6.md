<!-- loio20e6be627519101487989fa5c2fceccd -->

# RPAD Function \(String\)

Right-pads a string with spaces or a specified pattern to make a string that is a specified number of characters in length.



<a name="loio20e6be627519101487989fa5c2fceccd__sql_function_rpad_1sql_function_rpad_syntax"/>

## Syntax

```
RPAD(<string>, <number> [, <pattern>])
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the string to be padded.



</dd><dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the length to pad *<string\>*. *<number\>* must be an integer.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

Specifies a string of characters, rather than spaces, to use for padding.



</dd>
</dl>



<a name="loio20e6be627519101487989fa5c2fceccd__sql_function_rpad_1sql_function_rpad_description"/>

## Description

Right-pads the end of *<string\>* with spaces or characters to make a string of *<number\>* characters in length. If *<pattern\>* is specified, then *<string\>* is padded using sequences of the given characters until the required length is met.

If the length of *<string\>* is greater than *<n\>*, then no padding is performed and the resulting value is truncated to the length specified in *<number\>*.

RPAD returns an empty string value if *<number\>* is less than 1.



<a name="loio20e6be627519101487989fa5c2fceccd__sql_function_rpad_1sql_function_rpad_examples"/>

## Example

The following example right-pads the end of string `end` with the pattern `12345` to make a string of `15` characters in length and returns the value ***end123451234512***:

```
SELECT RPAD ('end', 15, '12345') "right padded" FROM DUMMY;
```

In the following example, *<str\>* is longer than *<n\>*, so no padding is performed and the result is *<str\>* truncated to the length of *<n\>* \(that is, ***en***\):

```
SELECT RPAD ('end', 2, '12345') "right padded" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

