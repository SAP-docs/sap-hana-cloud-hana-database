<!-- loio46ff9650c7f44461a6146269c1e2a4c6 -->

# Data Type Conversion

Both implicit and explicit data type conversions are allowed in the SAP HANA database.




<dl>
<dt><b>

Explicit type conversion

</b></dt>
<dd>

The data type of an expression result – for example, a field reference, a function on fields, or literals – can be converted using the CAST function, or using functions that start with TO\_, such as TO\_NVARCHAR. However, SAP HANA does not support conversions between LOB data types.



</dd><dt><b>

Implicit type conversion

</b></dt>
<dd>

When a given set of operand/argument types does not match what an operator/function expects, a type conversion is carried out by the SAP HANA database. This conversion only occurs if a relevant conversion is available and if it makes the operation/function executable. For example, a comparison of BIGINT and NVARCHAR is performed by implicitly converting NVARCHAR to BIGINT. With the exception of TIME and TIMESTAMP data types, explicit conversions can be used for implicit conversions. TIME and TIMESTAMP data types can be converted reciprocally by using the TO\_TIME\(TIMESTAMP\) and TO\_TIMESTAMP\(TIME\) functions.

**Implicit Type Conversion Examples**


<table>
<tr>
<th valign="top">

Input Expression

</th>
<th valign="top">

Transformed Expression with Implicit Conversion

</th>
</tr>
<tr>
<td valign="top">

BIGINT \> NVARCHAR

</td>
<td valign="top">

BIGINT \> BIGINT\(NVARCHAR\)

</td>
</tr>
<tr>
<td valign="top">

BIGINT \> DECIMAL

</td>
<td valign="top">

DECIMAL\(BIGINT\) \> DECIMAL

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP \> DATE

</td>
<td valign="top">

TIMESTAMP \> TIMESTAMP\(DATE\)

</td>
</tr>
<tr>
<td valign="top">

DATE \> TIME

</td>
<td valign="top">

Returns an error because conversion cannot occur between DATE and TIME

</td>
</tr>
</table>



</dd>
</dl>

The rules shown in the tables below are applicable to both implicit and explicit conversion except for TIME to TIMESTAMP conversion. Only explicit conversions are allowed for converting the TIME data type to the TIMESTAMP data type using the TO\_TIMESTAMP or CAST functions.

In the tables below, **OK** means that data type conversions are allowed without any checks; **CHK** means that the data type can be converted if the data is valid for the target type; and **\-** means that data type conversion is not allowed.

**Numeric Data Type Conversion table**


<table>
<tr>
<th valign="top">

Target/Source

</th>
<th valign="top">

TINYINT

</th>
<th valign="top">

SMALLINT

</th>
<th valign="top">

INTEGER

</th>
<th valign="top">

BIGINT

</th>
<th valign="top">

DECIMAL

</th>
<th valign="top">

DECIMAL\(*<p\>*,*<s\>*\)

</th>
<th valign="top">

SMALLDECIMAL

</th>
<th valign="top">

REAL

</th>
<th valign="top">

DOUBLE

</th>
<th valign="top">

NVARCHAR

</th>
</tr>
<tr>
<td valign="top">

TINYINT

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

SMALLINT

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

INTEGER

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

BIGINT

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

DECIMAL

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

DECIMAL\(*<p\>*,*<s\>*\)

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

SMALLDECIMAL

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

REAL

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

OK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

DOUBLE

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
</tr>
</table>

**Datetime Data Type Conversion Table**


<table>
<tr>
<th valign="top">

Target/ Source

</th>
<th valign="top">

TIME

</th>
<th valign="top">

DATE

</th>
<th valign="top">

SECONDDATE

</th>
<th valign="top">

TIMESTAMP

</th>
<th valign="top">

NVARCHAR

</th>
</tr>
<tr>
<td valign="top">

TIME

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

DATE

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

SECONDDATE

</td>
<td valign="top">

TIME

</td>
<td valign="top">

DATE

</td>
<td valign="top">

\-

</td>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

TIMESTAMP

</td>
<td valign="top">

TIME

</td>
<td valign="top">

DATE

</td>
<td valign="top">

SECONDDATE

</td>
<td valign="top">

\-

</td>
<td valign="top">

OK

</td>
</tr>
<tr>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

CHK

</td>
<td valign="top">

\-

</td>
</tr>
</table>

**Character String Data Type Conversion Table**


<table>
<tr>
<th valign="top">

Target/ Source

</th>
<th valign="top">

VARBINARY

</th>
<th valign="top">

NVARCHAR

</th>
</tr>
<tr>
<td valign="top">

VARBINARY

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

NVARCHAR

</td>
<td valign="top">

OK

</td>
<td valign="top">

\-

</td>
</tr>
</table>



## Data Type Precedence

Data type precedence specifies that the data type with the lower precedence is converted to the data type with the higher precedence.

The following list specifies the precedence of data types, with TIMESTAMP being the highest \(first\) and VARBINARY being the lowest \(last\) in precedence:

-   TIMESTAMP

-   SECONDDATE

-   DATE

-   TIME

-   DOUBLE

-   REAL

-   DECIMAL

-   DECIMAL\(*<precision\>*, *<scale\>*\)

-   SMALLDECIMAL

-   BIGINT

-   INTEGER

-   SMALLINT

-   TINYINT

-   NCLOB

-   NVARCHAR

-   BLOB

-   VARBINARY




## Example

-   When converting numeric types to DECIMAL or SMALLDECIMAL types, the least significant digits are rounded. For example, converting a BIGINT value such as 1234567890123456789 to SMALLDECIMAL becomes 1234567890123457000.

-   When converting numeric types to any other numeric types, the least significant digits are truncated toward 0. The most significant digits cannot be truncated. Overflow errors occur if the converted value is incompatible with the target format. For example, converting a DECIMAL\(10,2\) value such as 12345.67 to BIGINT becomes 12345.

-   When converting datetime data types to other datetime data types, the results are truncated to the target type when the source type is larger; otherwise, the default value is added. For example, you can converting the TIMESTAMP 2013-07-03 01:23:45.123456789 to a DATE data type returns 2013-07-03. Converting the DATE 2013-07-03 to a TIMESTAMP returns 2013-07-03 00:00:00.000000000. Converting the TIMESTAMP 2013-07-03 23:59:59.7777777 to a SECONDDATE returns 2013-07-03 23:59:59.


