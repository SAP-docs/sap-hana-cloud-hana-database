<!-- loio4ee2f261e9c44003807d08ccc2e249ac -->

# Numeric Data Types

Numeric data types are used to store numeric information.



Each numeric type below has a maximum value and minimum value. A numeric overflow exception is thrown if a value is smaller than the minimum value or greater than the maximum value. In order to comply with IEEE754, NaN and infinity are not supported . -0.0 is stored as +0.0.

Floating-point data types are stored in the system using binary numbers. The fractional part of these numbers is represented using a combination of 1/2, 1/4, 1/8, 1/16, and so on. For this reason, they cannot completely represent rational numbers with fractional digits. For example, 0.1 cannot be represented exactly by combining these binary fractions. In this case, you obtain inaccurate results when using a floating-point data type. This is the correct behavior for these data types. The following example demonstrates the behavior and returns ***4.6999999999*** for DOUBLE\_SUM:

```
SELECT TO_DOUBLE(0.1) + TO_DOUBLE(4.6) AS DOUBLE_SUM FROM DUMMY;
```

For a list of numeric functions, see [Numeric Functions](011-SQL-Functions/numeric-functions-20a190b.md).


<dl>
<dt><b>

TINYINT

</b></dt>
<dd>

The TINYINT data type stores an 8-bit unsigned integer. The minimum value is 0 and the maximum value is 255.



</dd><dt><b>

SMALLINT

</b></dt>
<dd>

The SMALLINT data type stores a 16-bit signed integer. The minimum value is -32,768 and the maximum value is 32,767.



</dd><dt><b>

INTEGER

</b></dt>
<dd>

The INTEGER data type stores a 32-bit signed integer. The minimum value is -2,147,483,648 and the maximum value is 2,147,483,647.



</dd><dt><b>

BIGINT

</b></dt>
<dd>

The BIGINT data type stores a 64-bit signed integer. The minimum value is -9,223,372,036,854,775,808 and the maximum value is 9,223,372,036,854,775,807.



</dd><dt><b>

DECIMAL\[\(*<precision\>*, *<scale\>*\)\] or DEC\[\(*<p\>*,*<s\>*\)\]

</b></dt>
<dd>

DECIMAL\(*<p\>*, *<s\>*\) is the SQL standard notation for fixed-point decimals. *<p\>* specifies precision, or the number of total digits \(the sum of whole digits and fractional digits\). *<s\>* denotes scale, or the number of fractional digits. If a column is defined as DECIMAL\(5, 4\) for example, the numbers 3.14, 3.1415, 3.141592 are stored in the column as 3.1400, 3.1415, 3.1415, retaining the specified precision\(5\) and scale\(4\).

Precision can range from 1 to 38. The scale can range from 0 to *<p\>*. If the scale is not specified, then it defaults to 0.

If precision and scale are not specified, then DECIMAL becomes a floating-point decimal number. In this case, precision and scale can vary within the range of 1 to 34 for precision and -6,111 to 6,176 for scale, depending on the stored value.

For example, 0.0000001234 \(1234E-10\) has precision 4 and scale 10. 1.0000001234 \(10000001234E-10\) has precision 11 and scale 10. The value 1234000000 \(1234E6\) has precision 4 and scale 6.



</dd><dt><b>

SMALLDECIMAL

</b></dt>
<dd>

The SMALLDECIMAL data type is a floating-point decimal number. The precision and scale can vary within the range 1-16 for precision and -369-368 for scale, depending on the stored value. SMALLDECIMAL is supported on row and column store.



</dd><dt><b>

REAL

</b></dt>
<dd>

The REAL data type specifies a single-precision, 32-bit floating-point number.



</dd><dt><b>

DOUBLE

</b></dt>
<dd>

The DOUBLE data type specifies a double-precision, 64-bit floating-point number. The minimum value is -1.7976931348623157E308 and the maximum value is 1.7976931348623157E308 . The smallest positive DOUBLE value is 2.2250738585072014E-308 and the largest negative DOUBLE value is -2.2250738585072014E-308.

The DOUBLE data type is a 64-bit real number, where the maximum number of significant bits is 53.



</dd><dt><b>

FLOAT\(*<n\>*\)

</b></dt>
<dd>

The FLOAT\(*<n\>*\) data type specifies a 32-bit or 64-bit real number, where *<n\>* specifies the number of significant bits and can range between 1 and 53.

If you use the FLOAT\(*<n\>*\) data type, and *<n\>* is smaller than 25, then the 32-bit REAL data type is used instead. If *<n\>* is greater than or equal to 25, or if *<n\>* is not declared, then the 64-bit DOUBLE data type is used.



</dd>
</dl>

