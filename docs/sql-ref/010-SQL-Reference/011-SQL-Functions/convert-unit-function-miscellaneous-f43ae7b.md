<!-- loiof43ae7bb6f5b1014a345adb9db626de0 -->

# CONVERT\_UNIT Function \(Miscellaneous\)

Converts the specified source units to specified target units.



<a name="loiof43ae7bb6f5b1014a345adb9db626de0__sql_function_convert_unit_1sql_function_convert_unit_syntax"/>

## Syntax

```
CONVERT_UNIT( <named_parameter_value>, ... )
```



<a name="loiof43ae7bb6f5b1014a345adb9db626de0__sql_function_convert_unit_1sql_function_convert_unit_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<named\_parameter\_value\>*

</b></dt>
<dd>

Named value of field reference, or constant string, parameters.

```
<named_parameter_value> := "<field_reference_parameter>" => 
 <expression> | "<const_string_parameter>" => <const_string>
```

```
<field_reference_parameter> ::= 
 QUANTITY 
 | SOURCE_UNIT 
 | TARGET_UNIT 
 | CLIENT
```

```
<const_string_parameter> ::= 
 SCHEMA 
 | DATABASE 
 | ERROR_HANDLING 
 | RATES_TABLE 
 | DIMENSION_TABLE
```



</dd>
</dl>


<table>
<tr>
<th valign="top">

Field Reference Parameter Name

</th>
<th valign="top">

Description

</th>
<th valign="top">

Mandatory

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top">

QUANTITY

</td>
<td valign="top">

The column to be converted.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

SOURCE\_UNIT

</td>
<td valign="top">

The column identifier describing the input unit. A constant string is also accepted using single quotations.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

TARGET\_UNIT

</td>
<td valign="top">

The column identifier describing the target unit. A constant string is also accepted using single quotations.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

CLIENT

</td>
<td valign="top">

Defines a three character string that is used to separate tenants within ERP system tables. This is used in the conversion tables to select the correct rows for each user. A column identifier is also accepted using double quotations. This parameter is mandatory, as the CLIENT session context variable is not used by this command.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

SCHEMA

</td>
<td valign="top">

Defines the schema that contains the conversion tables used for the conversion.

</td>
<td valign="top">

Yes

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

DATABASE

</td>
<td valign="top">

Defines the tenant where the conversion tables are located. If not specified, the conversion uses the current database.

</td>
<td valign="top">

No

</td>
<td valign="top">

None

</td>
</tr>
<tr>
<td valign="top">

ERROR\_HANDLING

</td>
<td valign="top">

Defines how the system handles a situation where a row cannot be converted.


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Purpose

</th>
</tr>
<tr>
<td valign="top">

fail on error

</td>
<td valign="top">

The conversion fails with an error.

</td>
</tr>
<tr>
<td valign="top">

set to null

</td>
<td valign="top">

The output from the row that caused the error is set to NULL.

</td>
</tr>
<tr>
<td valign="top">

keep unconverted

</td>
<td valign="top">

The input value is returned.

</td>
</tr>
</table>



</td>
<td valign="top">

No

</td>
<td valign="top">

fail on error

</td>
</tr>
<tr>
<td valign="top">

RATES\_TABLE

</td>
<td valign="top">

Defines a table that stores the conversion rates. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.

</td>
<td valign="top">

No

</td>
<td valign="top">

T006

</td>
</tr>
<tr>
<td valign="top">

DIMENSION\_TABLE

</td>
<td valign="top">

Defines a table that stores the conversion dimensions. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.

</td>
<td valign="top">

no

</td>
<td valign="top">

T006D

</td>
</tr>
</table>



<a name="loiof43ae7bb6f5b1014a345adb9db626de0__sql_function_convert_unit_1sql_function_convert_unit_description"/>

## Description

The CONVERT\_UNIT function is an SQL representation of the SQL Script built-in function CE\_CONVERSION, and internally uses CE\_CONVERSION for computation.

To use the CONVERT\_UNIT function, the unit conversion tables T006 and T006D must be available in the SAP HANA database. For other SAP HANA databases, replicate the T006 and T006D tables from an SAP ERP system.



<a name="loiof43ae7bb6f5b1014a345adb9db626de0__sql_function_convert_unit_1sql_function_convert_unit_examples"/>

## Example

```
CREATE ROW TABLE sample_input (
 quant DECIMAL(15,2),
 source_unit NVARCHAR(4),
 target_unit NVARCHAR(4)
 );

 INSERT INTO sample_input VALUES (1.0, 'SRC', 'TRG');
 INSERT INTO sample_input VALUES (1.0, 'SRC', 'TRG');
 
 SELECT CONVERT_UNIT("QUANTITY"=>quant
 , "SOURCE_UNIT" =>source_unit
 , "SCHEMA" => 'SYSTEM'
 , "DATABASE" => 'NDB'
 , "TARGET_UNIT" => target_unit
 , "ERROR_HANDLING"=>'set to null'
 , "CLIENT" => '000') AS converted
 FROM sample_input;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

