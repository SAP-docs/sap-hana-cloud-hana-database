<!-- loio20a21e0875191014bb13f70acec8cc5c -->

# DATA\_TYPES System View

Provides information about available SQL data types.



<a name="loio20a21e0875191014bb13f70acec8cc5c___d_a_t_a__t_y_p_e_s_1struct_DATA_TYPES"/>

## Structure


<table>
<tr>
<th valign="top">

Column name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

TYPE\_ID

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the data type ID.

</td>
</tr>
<tr>
<td valign="top">

TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the data type name.

</td>
</tr>
<tr>
<td valign="top">

COLUMN\_SIZE

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the maximum size, in bytes, of the data type that this system can support.

</td>
</tr>
<tr>
<td valign="top">

LITERAL\_PREFIX

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo NVARCHAR. Character or characters used to prefix a literal, for example, a single quotation mark \('\) for character data types or 0x for binary data types; NULL is returned for data types where a literal prefix is not applicable.

</td>
</tr>
<tr>
<td valign="top">

LITERAL\_SUFFIX

</td>
<td valign="top">

CHAR\(1\)

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo NVARCHAR. Character or characters used to terminate a literal, for example, a single quotation mark \('\) for character data types; NULL is returned for data types where a literal suffix is not applicable.

</td>
</tr>
<tr>
<td valign="top">

CREATE\_PARAMS

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo NVARCHAR. A list of keywords, separated by commas, corresponding to each parameter that the application may specify in parentheses when using the name that is returned in the TYPE\_NAME field.

</td>
</tr>
<tr>
<td valign="top">

NULLABLE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the data type can accept NULL or not.

</td>
</tr>
<tr>
<td valign="top">

CASE\_SENSITIVE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo SMALLINT. Whether a character data type is case-sensitive in collations and comparisons.

</td>
</tr>
<tr>
<td valign="top">

SEARCHABLE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays how the data type can be used in the WHERE clause.

</td>
</tr>
<tr>
<td valign="top">

UNSIGNED\_ATTRIBUTE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the attribute is signed or unsigned.

</td>
</tr>
<tr>
<td valign="top">

FIXED\_PREC\_SCALE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the data type has predefined fixed precision and scale \(ODBC\).

</td>
</tr>
<tr>
<td valign="top">

AUTO\_UNIQUE\_VALUE

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Displays whether the data type is auto incrementing \(ODBC\).

</td>
</tr>
<tr>
<td valign="top">

LOCAL\_TYPE\_NAME

</td>
<td valign="top">

NVARCHAR\(16\)

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo NVARCHAR. Localized version of the data source-dependent name of the data type.

</td>
</tr>
<tr>
<td valign="top">

MINIMUM\_SCALE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo SMALLINT. The minimum scale of the data type on the data source.

</td>
</tr>
<tr>
<td valign="top">

MAXIMUM\_SCALE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ODBC 2.0 SQLGetTypeInfo SMALLINT. The maximum scale of the data type on the data source.

</td>
</tr>
<tr>
<td valign="top">

SQL\_DATA\_TYPE

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ODBC 3.0 SQLGetTypeInfo SMALLINT. The value of the SQL data type as it appears in the SQL\_DESC\_TYPE field of the descriptor. This column is the same as the DATATYPE column, except for interval and DATETIME data types.

</td>
</tr>
<tr>
<td valign="top">

SQL\_DATETIME\_SUB

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ODBC 3.0 SQLGetTypeInfo SMALLINT. When the value of SQL\_DATATYPE is SQL\_DATETIME or SQL\_INTERVAL, this column contains the DATETIME/interval subcode.

</td>
</tr>
<tr>
<td valign="top">

NUM\_PREC\_RADIX

</td>
<td valign="top">

INTEGER

</td>
<td valign="top">

Displays the ODBC 3.0 SQLGetTypeInfo INTEGER. In case of an approximate numeric data type, value is 2 to indicate that COLUMN\_SIZE specifies the number of bits. For exact numeric data types value 10 indicates that COLUMN\_SIZE specifies the number of decimal digits.

</td>
</tr>
<tr>
<td valign="top">

INTERVAL\_PRECISION

</td>
<td valign="top">

SMALLINT

</td>
<td valign="top">

Displays the ODBC 3.0 SQLGetTypeInfo SMALLINT. If the data type is an interval data type, then this column contains the value of the interval leading precision. Otherwise, this column is NULL.

</td>
</tr>
</table>



<a name="loio20a21e0875191014bb13f70acec8cc5c__section_yjr_jdq_bzb"/>

## Permissions

Unless otherwise specified, system views are available to all users granted the PUBLIC role. The data returned for each view is filtered according to the granted privileges of the user accessing a view. Users granted the CATALOG READ system privilege have unfiltered access to all system views and their data regardless of the PUBLIC role and privilege grants.

**Related Information**  


[Data Types](../../010-SQL-Reference/data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[Data Type Conversion Functions](../../010-SQL-Reference/011-SQL-Functions/data-type-conversion-functions-209ddef.md "Data type conversion functions convert data from one data type to another data type.")

[Data Type Extension](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/1923f363c0ad4c778dc0e63812b751cd.html "") :arrow_upper_right:

[Scalar Data Types](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/712f01427fac46b586cb08b4c02c4900.html "") :arrow_upper_right:

