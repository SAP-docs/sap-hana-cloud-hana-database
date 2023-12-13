<!-- loio20db6dd475191014aa7b978452f92bbd -->

# CAST Function \(Data Type Conversion\)

Returns the value of an expression converted to a supplied data type.



<a name="loio20db6dd475191014aa7b978452f92bbd__sql_function_cast_1sql_function_cast_syntax"/>

## Syntax

```
CAST( <expression> AS <data_type>[ ( <length> ) ] )
```



<a name="loio20db6dd475191014aa7b978452f92bbd__sql_function_cast_1sql_function_cast_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression to be converted. If you use a parameter, the parameter is bound as *<data\_type\>*, or as a String if *<data\_type\>* is LOB or GEOMETRY.



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the target data type.

```
<data_type >::= 
 BOOLEAN
 |TINYINT 
 | SMALLINT 
 | INTEGER 
 | BIGINT 
 | DECIMAL 
 | SMALLDECIMAL 
 | REAL 
 | DOUBLE
 | NVARCHAR 
 | DAYDATE 
 | DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP
 | LOB
 | BINARY
 | GEOMETRY
```



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

Specifies the maximum length of the string in characters.



</dd>
</dl>



<a name="loio20db6dd475191014aa7b978452f92bbd__sql_function_cast_1sql_function_cast_description"/>

## Description

Returns the value of an expression converted to a supplied data type.



<a name="loio20db6dd475191014aa7b978452f92bbd__sql_function_cast_1sql_function_cast_examples"/>

## Examples

Convert the value `7` to the NVARCHAR value ***7***:

```
SELECT CAST (7 AS NVARCHAR) "cast" FROM DUMMY;
```

Converts the value `10.5` to the INTEGER value ***10***, truncating the mantissa.

```
SELECT CAST (10.5 AS INTEGER) "cast" FROM DUMMY;
```

Bind a parameter as BIGINT. Without the CAST function, the data type of the parameter is ambiguous.

```
CREATE COLLECTION C1;
INSERT INTO C1 VALUES({A:1,B:2});
INSERT INTO C1 VALUES({A:'ABC'});
SELECT * FROM C1 WHERE A = CAST (? AS BIGINT);
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

