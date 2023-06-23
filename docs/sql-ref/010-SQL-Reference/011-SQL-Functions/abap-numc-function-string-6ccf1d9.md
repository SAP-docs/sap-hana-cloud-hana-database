<!-- loio6ccf1d971bca4bb6bb59f19fe6e1e6c9 -->

# ABAP\_NUMC Function \(String\)

Converts an input string to a string of a specified length, that contains only digits.



<a name="loio6ccf1d971bca4bb6bb59f19fe6e1e6c9__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
ABAP_NUMC( <string>, <chars> )
```



<a name="loio6ccf1d971bca4bb6bb59f19fe6e1e6c9__section_uh2_yww_1z"/>

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

Specifies the length that the returned string should be.



</dd>
</dl>



<a name="loio6ccf1d971bca4bb6bb59f19fe6e1e6c9__sql_function_lower_1sql_function_lower_description"/>

## Description

String and numeric values are left-padded with 0s if *<string\>* is shorter than *<chars\>*. If *<string\>* is longer than *<chars\>*, then characters are truncated from the left.

Numeric values are rounded to their integer part and the sign is discarded.

TIMESTAMP, SECONDDATE, DATE, and TIME values are padded and truncated from the right side, as necessary.

DECIMAL and SMALLDECIMAL inputs are never truncated but create an overflow error if they are found to be too long.



<a name="loio6ccf1d971bca4bb6bb59f19fe6e1e6c9__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example returns ***012***.

```
SELECT ABAP_NUMC(12, 3) FROM DUMMY;
```

The following example returns ***234***.

```
SELECT ABAP_NUMC(1234, 3) FROM DUMMY;
```

The following example returns ***01230000000000000000***.

```
SELECT ABAP_NUMC(1.23e18, 20) FROM DUMMY;
```

The following example returns ***001235***.

```
SELECT ABAP_NUMC(-1234.5, 6) FROM DUMMY;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

