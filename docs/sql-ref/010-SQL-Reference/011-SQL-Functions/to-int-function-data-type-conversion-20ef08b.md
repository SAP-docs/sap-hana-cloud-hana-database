<!-- loio20ef08b775191014b8f4f7fad1c7f0f1 -->

# TO\_INT Function \(Data Type Conversion\)

Converts a value to an INT data type.



<a name="loio20ef08b775191014b8f4f7fad1c7f0f1__sql_function_to_int_1sql_function_to_int_syntax"/>

## Syntax

```
TO_INT(<value>)
```



<a name="loio20ef08b775191014b8f4f7fad1c7f0f1__sql_function_to_int_1sql_function_to_int_description"/>

## Description

If the input *<value\>* has a mantissa, then the mantissa is truncated during the conversion process.



<a name="loio20ef08b775191014b8f4f7fad1c7f0f1__sql_function_to_int_1sql_function_to_int_examples"/>

## Examples

The following example converts the value ***10*** to the INT value ***10***:

```
SELECT TO_INT('10') "to int" FROM DUMMY;
```

The following example converts the value ***10.5*** to the INT value ***10***, truncating the mantissa:

```
SELECT TO_INT(10.5) "to int" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

