<!-- loioe4887a42a3eb4d5d88bf84da66c07668 -->

# ABAP\_ALPHANUM Function \(String\)

Converts a string to what would result if the string was transformed into an ALPHANUM type and then converted back to a string.



<a name="loioe4887a42a3eb4d5d88bf84da66c07668__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
ABAP_ALPHANUM( <string>, <chars> )
```



<a name="loioe4887a42a3eb4d5d88bf84da66c07668__section_uh2_yww_1z"/>

## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the input string to convert.



</dd><dt><b>

*<chars\>*

</b></dt>
<dd>

Specifies the length to left-pad *<string\>* with \(using 0s\) if *<string\>* is shorter than the length specified by *<chars\>*.



</dd>
</dl>



<a name="loioe4887a42a3eb4d5d88bf84da66c07668__sql_function_lower_1sql_function_lower_description"/>

## Description

The input value, *<string\>*, is checked to find out if it is numeric or a mixture of numeric and non-numeric. If *<string\>* is numeric, then it is left-padded with zeroes up to the length specified by *<chars\>*, if necessary. If *<string\>* is a mixture or numeric and non-numeric, or is empty, then it is returned unchanged.

Strings that start with spaces and contain only digits after the whitespace prefix are regarded as numeric.



<a name="loioe4887a42a3eb4d5d88bf84da66c07668__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example returns ***012***. Since *<chars\>* is set to 3, the left-most digit is padded with a 0.

```
SELECT ABAP_ALPHANUM('12', 3) FROM DUMMY;
```

The following example returns ***1234***. The input value was numeric and was not shorter than *<chars\>*, so no left-padding was required.

```
SELECT ABAP_ALPHANUM('1234', 3) FROM DUMMY;
```

The following example returns ***12x***. Because the input value contained a mixture of numeric and non-numeric, it is returned unchanged.

```
SELECT ABAP_ALPHANUM('12x', 13) FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

