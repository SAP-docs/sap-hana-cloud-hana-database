<!-- loio20efce3f751910149e20b0068fd68287 -->

# TO\_NVARCHAR Function \(Data Type Conversion\)

Converts a given value to an NVARCHAR data type, with an option to format the output value.



<a name="loio20efce3f751910149e20b0068fd68287__sql_function_to_nvarchar_1sql_function_to_nvarchar_syntax"/>

## Syntax

```
TO_NVARCHAR( <value> [, <format> ] )
```



<a name="loio20efce3f751910149e20b0068fd68287__section_btr_k2z_pcb"/>

## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

The input value for the function. If *<value\>* is a datetime data type, and *<format\>* is not specified, then the default format is applied to the output value, unless the relevant session variable \(DATE\_FORMAT, TIME\_FORMAT, TIMESTAMP\_FORMAT, or SECONDDATE\_FORMAT\) is set to something different.



</dd><dt><b>

*<format\>*

</b></dt>
<dd>

Specifies the desired formatting to apply to the converted value. For datetime values, use *<format\>* to define the desired datetime output format \(for example, `YYYY/MM/DD`. See the *Datetime Data Types* topic in this guide for more information on possible datetime formats.

To define other types of output formats \(for example numbers with custom symbols, commas, zeros and so on\), specify *<format\>* using the following conventions:

-   9 - Return the number in the specified position; otherwise, return nothing.

-   0 - Return the number in the specified position; otherwise, return a zero \(0\).

-   S - Return the sign symbol \(either + or -\) for the value.

-   E - Divide the number into significant part and exponent part.

-   % - Multiply *<value\>* by 10^2 and adds a percent symbol \(%\) at the end.

-   . \(a period\) - Insert a period in the specified position.

-   All other characters other than the items above: Return the character in the specified position.




</dd>
</dl>



<a name="loio20efce3f751910149e20b0068fd68287__sql_function_to_nvarchar_1sql_function_to_nvarchar_description"/>

## Description

If the *<format\>* specifier is omitted, then the conversion is performed using the date format model.

The following data types can be converted to NVARCHAR using the TO\_NVARCHAR function:

-   BIGINT, DAYDATE, DECIMAL, DOUBLE, FIXED12, FIXED16, FIXED8, INTEGER, REAL, SECONDDATE, SMALLDECIMAL, SMALLINT, TIME, TIMESTAMP, TINYINT, VARBINARY, VARCHAR
-   CLOB, NCLOB
-   REAL\_VECTOR



<a name="loio20efce3f751910149e20b0068fd68287__sql_function_to_nvarchar_1sql_function_to_nvarchar_examples"/>

## Example

The following example converts the value `2009/12/31` to the NVARCHAR value ***09-12-31***.

```
SELECT TO_NVARCHAR(TO_DATE('2009/12/31'), 'YY-MM-DD') "to nvarchar" FROM DUMMY;
```

The following statements demonstrate how to use the *<string\_formatting\>* option to define the format of the output values:

```
SELECT TO_NVARCHAR(1, '00.00') FROM Dummy;   --> 01.00
SELECT TO_NVARCHAR(100, '00.00') FROM Dummy;          --> 100.00
SELECT TO_NVARCHAR(100, '9999.00') FROM Dummy;        --> 100.00
SELECT TO_NVARCHAR(100, '0000.00') FROM Dummy;        --> 0100.00
SELECT TO_NVARCHAR(100, 'S0000.00') FROM Dummy;       --> +0100.00 
SELECT TO_NVARCHAR(-100, 'S0000.00') FROM Dummy;      --> -0100.00
SELECT TO_NVARCHAR(-100, '000.00') FROM Dummy;        --> -100.00
SELECT TO_NVARCHAR(-100, 'S0.0E0') FROM Dummy;        --> -1.0E2
SELECT TO_NVARCHAR(-0.001, 'S0.0E0') FROM Dummy;      --> -1.0E-3
SELECT TO_NVARCHAR(-0.001, 'S0.0E00') FROM Dummy;     --> -1.0E-03
SELECT TO_NVARCHAR(1000, '9,999.00') FROM Dummy;      --> 1,000.00
SELECT TO_NVARCHAR(1000, '$9,999.00') FROM Dummy;     --> $1,000.00
SELECT TO_NVARCHAR(1000, '$9,999.99') FROM Dummy;     --> $1,000.
SELECT TO_NVARCHAR(1,'0.00%') FROM Dummy;             --> 100.00%
SELECT TO_NVARCHAR(1,'100%') FROM Dummy;              --> 1100%
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[TO\_VARCHAR Function \(Data Type Conversion\)](to-varchar-function-data-type-conversion-20f226a.md "In SAP HANA database, VARCHAR is an alias for the NVARCHAR data type. Please use the TO_NVARCHAR function instead.")

[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

