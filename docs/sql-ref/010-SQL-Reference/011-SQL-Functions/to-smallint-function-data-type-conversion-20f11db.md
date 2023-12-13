<!-- loio20f11dbf75191014972cc8c3d639d432 -->

# TO\_SMALLINT Function \(Data Type Conversion\)

Converts a value to a SMALLINT data type.



<a name="loio20f11dbf75191014972cc8c3d639d432__sql_function_to_smallint_1sql_function_to_smallint_syntax"/>

## Syntax

```
TO_SMALLINT(<value>)
```



<a name="loio20f11dbf75191014972cc8c3d639d432__sql_function_to_smallint_1sql_function_to_smallint_description"/>

## Description

If the input *<value\>* has a mantissa, then these digits are truncated during the conversion process.



<a name="loio20f11dbf75191014972cc8c3d639d432__sql_function_to_smallint_1sql_function_to_smallint_examples"/>

## Examples

The following example converts the value `10` to a SMALLINT and returns the value ***10***:

```
SELECT TO_SMALLINT ('10') "to smallint" FROM DUMMY;
```

The following example converts the value `10` to a SMALLINT and returns the value ***10***, truncating the mantissa:

```
SELECT TO_SMALLINT(10.5) "to int" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

