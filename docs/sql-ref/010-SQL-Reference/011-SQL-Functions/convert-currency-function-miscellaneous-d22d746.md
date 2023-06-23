<!-- loiod22d746ed2951014bb7fb0114ffdaf96 -->

# CONVERT\_CURRENCY Function \(Miscellaneous\)

Calculates values in different currencies.



<a name="loiod22d746ed2951014bb7fb0114ffdaf96__sql_function_convert_currency_1sql_function_convert_currency_syntax"/>

## Syntax

```
CONVERT_CURRENCY( <named_parameter_value>[{, <named_parameter_value>}...])
```



<a name="loiod22d746ed2951014bb7fb0114ffdaf96__sql_function_convert_currency_1sql_function_convert_currency_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<named\_parameter\_value\>*

</b></dt>
<dd>

Specifies the parameters for the conversion.

```
<named_parameter_value> ::= 
"<field_reference_parameter>" => <expression> 
 | "<const_string_parameter>" => <const_string>
```

```
<field_reference_parameter> ::= 
 AMOUNT 
 | SOURCE_UNIT 
 | TARGET_UNIT 
 | REFERENCE_DATE 
 | CLIENT
```

You use field reference parameters to refer to table columns for the conversion.


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

AMOUNT



</td>
<td valign="top">

The column identifier containing the values to be converted.



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

Defines a three character string that is used to separate tenants within ERP system tables. This is used in the conversion tables to select the correct rows for each user. A column identifier is also accepted using double quotations.

This parameter is mandatory, as the CLIENT session context variable is not used by this command.



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

REFERENCE\_DATE



</td>
<td valign="top">

The column identifier describing the currency reference date. A constant string is also accepted using single quotations.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

None



</td>
</tr>
</table>

```
<const_string_parameter> ::= 
 SCHEMA 
| DATABASE 
| CONVERSION_TYPE 
| LOOKUP 
| ERROR_HANDLING 
| ACCURACY 
| DATE_FORMAT 
| STEPS 
| CONFIGURATION_TABLE 
| PRECISIONS_TABLE 
| NOTATIONS_TABLE 
| RATES_TABLE 
| PREFACTORS_TABLE
```

*<const\_string\_parameter\>* defines constant parameter values used in the conversion.


<table>
<tr>
<th valign="top">

Constant Parameter Name



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

Defines the tenant where the conversion tables are located \(for example the TCUR\* tables of the ERP currency conversion\). If not specified, the conversion uses the current database.



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

METHOD



</td>
<td valign="top">

Possible values: ERP, Banking



</td>
<td valign="top">

No



</td>
<td valign="top">

ERP



</td>
</tr>
<tr>
<td valign="top">

BID\_ASK\_TYPE



</td>
<td valign="top">

Possible values: bid, ask, mid



</td>
<td valign="top">

No



</td>
<td valign="top">

\(empty string\)



</td>
</tr>
<tr>
<td valign="top">

MARKET\_DATA\_AREA



</td>
<td valign="top">

Defines the market data area as stored in the tables. This is mandatory for banking currency conversion.



</td>
<td valign="top">

No



</td>
<td valign="top">

\(empty\_string\)



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_TIME



</td>
<td valign="top">

Defines the system timestamp for time travel functionality.



</td>
<td valign="top">

No



</td>
<td valign="top">

Current system timestamp in GMT



</td>
</tr>
<tr>
<td valign="top">

CONVERSION\_TYPE



</td>
<td valign="top">

Defines the conversion type as stored in the conversion tables. The conversion types available in your system vary according to the setup of your ERP system. In general, these are either M or EURX. Contact your system administrator for the details of your specific table configuration.



</td>
<td valign="top">

No



</td>
<td valign="top">

M



</td>
</tr>
<tr>
<td valign="top">

LOOKUP



</td>
<td valign="top">

The type of lookup to be performed. Possible values:


<dl>
<dt><b>

Regular

</b></dt>
<dd>

A regular conversion is performed.



</dd><dt><b>

Reverse

</b></dt>
<dd>

Performs a reverse conversion with the input units swapped.



</dd>
</dl>



</td>
<td valign="top">

No



</td>
<td valign="top">

Regular



</td>
</tr>
<tr>
<td valign="top">

ERROR\_HANDLING



</td>
<td valign="top">

Defines how the system handles a situation where a row could not be converted. Possible values:


<dl>
<dt><b>

fail on error

</b></dt>
<dd>

The conversion fails with an error.



</dd><dt><b>

set to null

</b></dt>
<dd>

The output from the row that caused the error is set to NULL.



</dd><dt><b>

keep unconverted

</b></dt>
<dd>

The input value is returned.



</dd>
</dl>



</td>
<td valign="top">

No



</td>
<td valign="top">

Fail on error



</td>
</tr>
<tr>
<td valign="top">

ACCURACY



</td>
<td valign="top">

Defines the rounding behavior of the system. Possible values:


<dl>
<dt><b>

compatibility

</b></dt>
<dd>

Mimics ERP behavior by rounding the result.



</dd><dt><b>

highest

</b></dt>
<dd>

Keeps as many digits as possible in the result.



</dd>
</dl>



</td>
<td valign="top">

No



</td>
<td valign="top">

Compatibility



</td>
</tr>
<tr>
<td valign="top">

DATE\_FORMAT



</td>
<td valign="top">

Defines the format in which the reference date is presented. Possible values


<dl>
<dt><b>

auto detect

</b></dt>
<dd>

Attempt automatic detection of the date format.



</dd><dt><b>

normal

</b></dt>
<dd>

Date is provided in a regular format



</dd><dt><b>

inverted

</b></dt>
<dd>

Date is provided in inverted SAP legacy format.



</dd>
</dl>



</td>
<td valign="top">

No



</td>
<td valign="top">

Auto detect



</td>
</tr>
<tr>
<td valign="top">

STEPS



</td>
<td valign="top">

Defines the steps that should be included in the conversion process. You provide a comma delimited list of the steps to be included, and the order of the steps is irrelevant.


<dl>
<dt><b>

shift

</b></dt>
<dd>

Enables a decimal shift according to the source currency selected. For example, if the source currency has 0 valid digits according to PRECISIONS\_TABLE, each value needs to be multiplied by 100 because in SAP ERP systems, values are stored using two digits. This has to be done to convert ERP values to their correct numerical representation.



</dd><dt><b>

convert

</b></dt>
<dd>

Triggers the actual conversion from the source to the target currency.



</dd><dt><b>

round

</b></dt>
<dd>

Rounds the converted value to the number of digits of the target currency. Use this step carefully if subsequent aggregations take place on the number, as rounding errors could accumulate.



</dd><dt><b>

shift\_back

</b></dt>
<dd>

While shift changes the decimals from two to the configured precision of the source currency, shift\_back changes them back to two, but from the target currency. If error handling is set to ***keep unconverted*** the output currency might be the source instead of the target currency. In case of an error, the rounding and the shift\_back are done with respect to the source currency and the conversion is dropped. This renders all steps redundant, and yields the input value again.



</dd>
</dl>



</td>
<td valign="top">

No



</td>
<td valign="top">

shift, convert



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION\_TABLE



</td>
<td valign="top">

The table identifier of the conversion type configuration. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

TCURV



</td>
</tr>
<tr>
<td valign="top">

PRECISIONS\_TABLE



</td>
<td valign="top">

The table identifier of the precision table. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

TCURX



</td>
</tr>
<tr>
<td valign="top">

NOTATIONS\_TABLE



</td>
<td valign="top">

The table identifier of the table that stores notations. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

TCURN



</td>
</tr>
</table>

Additional Parameters and Defaults for Method ERP


<table>
<tr>
<th valign="top">

Constant Parameter Name



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

CONFIGURATION\_TABLE



</td>
<td valign="top">

The table identifier of the conversion type configuration. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No TCURV



</td>
<td valign="top">

TCURV



</td>
</tr>
<tr>
<td valign="top">

RATES\_TABLE



</td>
<td valign="top">

The table identifier of the conversion rates table. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No TCURR



</td>
<td valign="top">

TCURR



</td>
</tr>
<tr>
<td valign="top">

PREFACTORS\_TABLE



</td>
<td valign="top">

The table identifier of the pre-factors table. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No TCURF



</td>
<td valign="top">

TCURF



</td>
</tr>
</table>

Additional Parameters and Defaults for Method Banking


<table>
<tr>
<th valign="top">

Constant Parameter Name



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

MARKET\_DATA\_AREA



</td>
<td valign="top">

Defines the market data area as stored in the tables. This is mandatory for banking currency conversion.



</td>
<td valign="top">

Yes



</td>
<td valign="top">

\(empty\_string\)



</td>
</tr>
<tr>
<td valign="top">

SYSTEM\_TIME



</td>
<td valign="top">

Defines the system timestamp for time travel functionality. T



</td>
<td valign="top">

No



</td>
<td valign="top">

Current system timestamp in GM



</td>
</tr>
<tr>
<td valign="top">

CONFIGURATION\_TABLE



</td>
<td valign="top">

The table identifier of the conversion type configuration. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

/BA1/TF4\_FXRTTYP



</td>
</tr>
<tr>
<td valign="top">

RATES\_TABLE



</td>
<td valign="top">

The table identifier of the conversion rates table. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

/BA1/F4\_FXRATES



</td>
</tr>
<tr>
<td valign="top">

PREFACTORS\_TABLE



</td>
<td valign="top">

The table identifier of the pre-factors table. If the table resides in a different tenant, provide a fully qualified name for the table or use the DATABASE parameter.



</td>
<td valign="top">

No



</td>
<td valign="top">

/BA1/TF4\_FXCVFCT



</td>
</tr>
</table>



</dd>
</dl>



<a name="loiod22d746ed2951014bb7fb0114ffdaf96__sql_function_convert_currency_1sql_function_convert_currency_description"/>

## Description

The CONVERT\_CURRENCY function provides an efficient method to calculate values in different currencies.

The HANA currency conversion provides two different methods. The ERP method, which stores the cross rates in table TCURR with 9 digits, and the Banking method, which stores the rates in table /BA1/F4\_FXRATES with 15 digits. In both cases, you can alternatively use tables that store the cross rates in a data type with more digits, such as DECIMAL\(25,21\).

To use the CONVERT\_CURRENCY function, the currency conversion tables TCURV, TCURX, TCURN, TCURR, and TCURF must be available in the SAP HANA database for method ERP. Alternatively, the currency conversion tables /BA1/TF4\_FXRTTYP , TCURX, TCURN, /BA1/F4\_FXRATES, and /BA1/TF4\_FXCVFCT must be available for method Banking. If you have stored the rates information in tables with a different layout, you can use views to map the table content to the format used in the ERP or Banking tables.

The CONVERT\_CURRENCY function does not support some conversion functions. It only supports columns XINVR, BWAER, XBWRL and XEURO from customizing table TCURV. An error message appears when one of the unsupported fields BKUZU, GKUZU or XBWRL are maintained in table TCURV. Refer to SAP Note 2792149 - Currency/unit conversion error: conversion type '<conversion type\>' has unsupported 'BKUZU' or 'GKUZU' type set.



<a name="loiod22d746ed2951014bb7fb0114ffdaf96__sql_function_convert_currency_1sql_function_convert_currency_examples"/>

## Example

Create a table and populate it with two example currency amounts.

```
CREATE ROW TABLE sample_input (price DECIMAL(15,2),
                             source_unit NVARCHAR(4),
                             target_unit NVARCHAR(4),
                             ref_date NVARCHAR(10)
                             );

 INSERT INTO sample_input VALUES (1.0, 'SRC', 'TRG', '2011-01-01');
 INSERT INTO sample_input VALUES (1.0, 'SRC', 'TRG', '2011-02-01');
```

Convert the values in the currency table using conversion tables contained in the SYSTEM schema in tenant NDB.

```
SELECT CONVERT_CURRENCY(amount=>price, 
                          "SOURCE_UNIT" =>source_unit,
                          "SCHEMA" => 'SYSTEM',
                          "DATABASE" => 'NDB',
                          "TARGET_UNIT" => target_unit,
                          "REFERENCE_DATE" =>'2013-09-23',
                          "ERROR_HANDLING"=>'set to null',
                          "CLIENT" => '000') as converted
                          FROM sample_input;
```

Convert the values by using the ***Banking*** `method`.

```
SELECT *, CONVERT_CURRENCY(method=>'Banking', -- new

                           market_data_area=>'S000’,  -- new (and mandatory for Banking)

                           amount=>ext_limit,
                           source_unit =>ext_limit_curr,

                           schema => 'SAPCOB',

                           target_unit=> 'EUR',

                           reference_date => business_day,

                           error_handling=> 'set to null',

                           client => '150') as converted from v_fx_input
```

Convert the values by using the ***Banking*** `method` and `system_time`.

```
SELECT *, CONVERT_CURRENCY(method=>'Banking', -- new

                           market_data_area=>'S000', -- mandatory (for Banking)

                           bid_ask_type=>'MID',   -- optional

                           system_time=>to_timestamp('2011-05-11 12:59.999','YYYY-MM-DD HH:SS.FF3') -- optional

                           amount=>ext_limit,

                           source_unit =>ext_limit_curr,

                           schema => 'SAPCOB',

                           target_unit=> 'EUR',

                           reference_date => business_day,

                           error_handling=> 'set to null',

                           client => '150') as converted from v_fx_input
```

**Related Information**  


[SAP Note 2792149](https://launchpad.support.sap.com/#/notes/2792149 "Currency/unit conversion error: conversion type '<conversion type>' has unsupported 'BKUZU' or 'GKUZU' type set")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Currency Translation](https://help.sap.com/viewer/ab2cb3cae60b45dd861f79c60f4cbdcc/1909.000/en-US/4e20dd7e0a6d20cee10000000a42189c.html)

[Associate Measures with Currency](https://help.sap.com/viewer/57a523b496cc4531a3676f5d94644899/latest/en-US/3da1c6b9d735423ba248e30a9bcfeee4.html)

