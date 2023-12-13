<!-- loio20a1569875191014b507cf392724b7eb -->

# Data Types

A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.



<a name="loio20a1569875191014b507cf392724b7eb___csql_data_types_1sql_data_types_introduction_classification"/>

## Classification of Data Types

In the SAP HANA database, each data type can be classified by its characteristics as follows:

**Classification of data types**


<table>
<tr>
<th valign="top">

Classification

</th>
<th valign="top">

Data Type

</th>
</tr>
<tr>
<td valign="top">

Datetime types

</td>
<td valign="top">

DATE, TIME, SECONDDATE, TIMESTAMP

</td>
</tr>
<tr>
<td valign="top">

Numeric types

</td>
<td valign="top">

TINYINT, SMALLINT, INTEGER, BIGINT, SMALLDECIMAL, DECIMAL, REAL, DOUBLE

</td>
</tr>
<tr>
<td valign="top">

Boolean type

</td>
<td valign="top">

BOOLEAN

</td>
</tr>
<tr>
<td valign="top">

Character string types

</td>
<td valign="top">

VARCHAR, NVARCHAR

</td>
</tr>
<tr>
<td valign="top">

Binary types

</td>
<td valign="top">

VARBINARY

</td>
</tr>
<tr>
<td valign="top">

Large Object types

</td>
<td valign="top">

BLOB, CLOB, NCLOB

</td>
</tr>
<tr>
<td valign="top">

Multi-valued types

</td>
<td valign="top">

ARRAY

</td>
</tr>
<tr>
<td valign="top">

Spatial types

</td>
<td valign="top">

ST\_GEOMETRY, ST\_POINT

</td>
</tr>
</table>



<a name="loio20a1569875191014b507cf392724b7eb___csql_data_types_1sql_data_types_typed_constant"/>

## Typed Constants

A constant is a symbol that represents a specific fixed data value.


<dl>
<dt><b>

Character string constant

</b></dt>
<dd>

A character string constant is enclosed in single quotation marks, for example: 'Brian' or '100'.

Unicode strings have a similar format to character strings but are preceded by an N identifier \(N stands for National Language in the SQL-92 standard\).

```
SELECT 'Brian' "character string 1", '100' "character string 2", N'abc' "unicode string" FROM DUMMY;
```

The example above returns the following results:


<table>
<tr>
<th valign="top">

character String 1

</th>
<th valign="top">

character String 2

</th>
<th valign="top">

unicode string

</th>
</tr>
<tr>
<td valign="top">

Brian

</td>
<td valign="top">

100

</td>
<td valign="top">

abc

</td>
</tr>
</table>



</dd><dt><b>

Number constant

</b></dt>
<dd>

A number constant is represented by a string of numbers that are not enclosed in quotation marks. Numbers may contain a decimal point or a scientific notation. For example, 123, 123.4, or 1.234e2.

A hexadecimal number constant is a string of hexadecimal numbers and has the prefix 0x. For example, 0x0abc.

```
SELECT 123 "integer", 123.4 "decimal1", 1.234e2 "decimal2", 0x0abc "hexadecimal" FROM DUMMY;
```

The example above returns the following results:


<table>
<tr>
<th valign="top">

integer

</th>
<th valign="top">

decimal1

</th>
<th valign="top">

decimal2

</th>
<th valign="top">

hexadecimal

</th>
</tr>
<tr>
<td valign="top">

123

</td>
<td valign="top">

123.4

</td>
<td valign="top">

123.4

</td>
<td valign="top">

2,748

</td>
</tr>
</table>



</dd><dt><b>

Binary string constant

</b></dt>
<dd>

A binary string has the prefix X and is a string of hexadecimal numbers that are enclosed in quotation marks. For example, X'00abcd' or x'dcba00'.

```
SELECT X'00abcd' "binary string 1", x'dcba00' "binary string 2" FROM DUMMY;
```

The example above returns the following results:


<table>
<tr>
<th valign="top">

binary string 1

</th>
<th valign="top">

binary string 2

</th>
</tr>
<tr>
<td valign="top">

00ABCD

</td>
<td valign="top">

DCBA00

</td>
</tr>
</table>



</dd><dt><b>

Date/Time/Timestamp constant

</b></dt>
<dd>

Date, Time, and Timestamp each have the following prefixes:

-   date'2010-01-01'

-   time'11:00:00.001'

-   timestamp'2011-12-31 23:59:59'


```
SELECT date'2010-01-01' "date", time'11:00:00.001' "time", timestamp'2011-12-31 23:59:59' "timestamp" FROM DUMMY;
```

The example above returns the following results:


<table>
<tr>
<th valign="top">

date

</th>
<th valign="top">

time

</th>
<th valign="top">

timestamp

</th>
</tr>
<tr>
<td valign="top">

Jan 1, 2010

</td>
<td valign="top">

11:00:00 AM

</td>
<td valign="top">

Dec 31, 2011 11:59:59.0 PM

</td>
</tr>
</table>



</dd>
</dl>

