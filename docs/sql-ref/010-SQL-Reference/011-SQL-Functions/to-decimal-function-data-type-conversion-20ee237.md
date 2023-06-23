<!-- loio20ee237775191014924e81b18c73c831 -->

# TO\_DECIMAL Function \(Data Type Conversion\)

Converts a value to a DECIMAL data type.



<a name="loio20ee237775191014924e81b18c73c831__sql_function_to_decimal_1sql_function_to_decimal_syntax"/>

## Syntax

```
TO_DECIMAL(<value> [, <precision>, <scale>])
```



## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

Specifies the value to convert to a DECIMAL data type. *<value\>* can be a variable.



</dd><dt><b>

*<precision\>*

</b></dt>
<dd>

Specifies the total number of significant digits. *<precision\>* can range from 1 to 38, specified as a string constant. If *<precision\>* is not specified, 34 is the default.



</dd><dt><b>

*<scale\>*

</b></dt>
<dd>

Specifies the number of digits from the decimal point to the least significant digit. *<scale\>*. *<scale\>* must be between 0 and the value for *<precision\>*. The scale is positive when the number has significant digits to the right of the decimal point, and negative when the number has significant digits to the left of the decimal point.



</dd>
</dl>



<a name="loio20ee237775191014924e81b18c73c831__sql_function_to_decimal_1sql_function_to_decimal_description"/>

## Description

If scale is not specified, then the default is 0. If both *<precision\>* and *<scale\>* are not specified, then DECIMAL becomes a floating-point decimal number, covering 1 to 34 for precision, and -6,111 to 6,176 for scale, depending on *<value\>*.

Unnecessary least significant digits in the mantissa of the input value are truncated during the conversion process.



<a name="loio20ee237775191014924e81b18c73c831__sql_function_to_decimal_1sql_function_to_decimal_examples"/>

## Example

The following example converts the value ***7654321.888888*** to DECIMAL with ***10*** digits precision and a scale of ***3***, and returns the value ***7654321.888***:

```
SELECT TO_DECIMAL(7654321.888888, 10, 3) "to decimal" FROM DUMMY;
```

The following example converts the value ***1234.789*** to DECIMAL with ***10*** for precision and ***0*** for scale, and returns the value ***1234*** \(scale is defined as 0, so everything is truncated after precision\).

```
SELECT TO_DECIMAL(1234.789,10,0) AS "to decimal" FROM DUMMY;
```

The following example, converts the value ***1234567890123456789012345678901256.78*** to a DECIMAL data type, with 34 as precision \(the default\) and 0 as the scale \(the default\), and returns ***1234567890123456789012345678901256*** \(the last two digits are truncated because the default precision is 34\).

```
SELECT TO_DECIMAL(1234567890123456789012345678901256.78) "to decimal" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

