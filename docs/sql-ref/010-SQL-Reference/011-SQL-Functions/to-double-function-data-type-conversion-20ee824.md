<!-- loio20ee824a751910148a149311d1aa0f32 -->

# TO\_DOUBLE Function \(Data Type Conversion\)

Converts a value to a DOUBLE data type.



<a name="loio20ee824a751910148a149311d1aa0f32__sql_function_to_double_1sql_function_to_double_syntax"/>

## Syntax

```
TO_DOUBLE(<value>)
```



<a name="loio20ee824a751910148a149311d1aa0f32__sql_function_to_double_1sql_function_to_double_description"/>

## Description

Converts a specified *<value\>* to a DOUBLE \(double precision\) data type.



<a name="loio20ee824a751910148a149311d1aa0f32__sql_function_to_double_1sql_function_to_double_examples"/>

## Example

The following example converts 15.12 to a DOUBLE, and then multiplies the value by 3, returning the DOUBLE value 45.36.

```
SELECT 3*TO_DOUBLE ('15.12') "to double" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

