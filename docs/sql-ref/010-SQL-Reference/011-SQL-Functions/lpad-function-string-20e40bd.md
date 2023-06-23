<!-- loio20e40bdb75191014bc66f14fa7a3d769 -->

# LPAD Function \(String\)

Left-pads a string with spaces, or a specified pattern, to make a string of a specified number of characters in length.



<a name="loio20e40bdb75191014bc66f14fa7a3d769__sql_function_lpad_1sql_function_lpad_syntax"/>

## Syntax

```
LPAD(<string>, <number> [, <pattern>])
```



## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies a string to be padded.



</dd><dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the length to which to pad *<string\>*. *<number\>* must be an integer.



</dd><dt><b>

*<pattern\>*

</b></dt>
<dd>

Specifies a string of characters to use for padding instead of spaces.



</dd>
</dl>



<a name="loio20e40bdb75191014bc66f14fa7a3d769__sql_function_lpad_1sql_function_lpad_description"/>

## Description

Left-pads the end of *<string\>* with spaces to make a string of *<number\>* characters. If *<pattern\>* is specified, then *<string\>* is padded using sequences of the given characters until the required length is met.

If the length of *<string\>* is greater than *<number\>*, then no padding is performed and the resulting value is truncated from the right side to the length specified in *<number\>*.

LPAD returns an empty string value if *<number\>* is less than 1.



<a name="loio20e40bdb75191014bc66f14fa7a3d769__sql_function_lpad_1sql_function_lpad_examples"/>

## Example

The following example left-pads the start of string ***end*** with the pattern ***12345*** to make a string of ***15*** characters in length, and returns the value ***123451234512end***:

```
SELECT LPAD ('end', 15, '12345') "lpad" FROM DUMMY;
```

In the following example, *<string\>* is longer than *<n\>*, so no padding is performed and the result is *<string\>* truncated to the length of *<number\>* \(that is, ***en***\):

```
SELECT LPAD ('end', 2, '12345') "lpad" FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

