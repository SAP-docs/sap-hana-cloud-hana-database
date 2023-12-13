<!-- loio20ef488375191014888a939fbf0acd6b -->

# TO\_INTEGER Function \(Data Type Conversion\)

Converts the *<value\>* to an INTEGER data type.



<a name="loio20ef488375191014888a939fbf0acd6b__sql_function_to_integer_1sql_function_to_integer_syntax"/>

## Syntax

```
TO_INTEGER(<value>)
```



<a name="loio20ef488375191014888a939fbf0acd6b__sql_function_to_integer_1sql_function_to_integer_description"/>

## Description

If the input *<value\>* has a mantissa, then these digits are truncated during the conversion process.



<a name="loio20ef488375191014888a939fbf0acd6b__sql_function_to_integer_1sql_function_to_integer_examples"/>

## Examples

The following example converts the value `10` to the INTEGER value ***10***:

```
SELECT TO_INTEGER ('10') "to int" FROM DUMMY;
```

The following example converts the value `10.5` to the INTEGER value ***10***, truncating the mantissa:

```
SELECT TO_INTEGER(10.5) "to int" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

