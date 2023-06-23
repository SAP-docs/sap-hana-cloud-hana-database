<!-- loio20eae5e1751910148391d3079da8527e -->

# TO\_BIGINT Function \(Data Type Conversion\)

Converts a value to a BIGINT data type.



<a name="loio20eae5e1751910148391d3079da8527e__sql_function_to_bigint_1sql_function_to_bigint_syntax"/>

## Syntax

```
TO_BIGINT(<value>)
```



<a name="loio20eae5e1751910148391d3079da8527e__sql_function_to_bigint_1sql_function_to_bigint_description"/>

## Description

If the input *<value\>* has a mantissa, then these digits are truncated during the conversion process.



<a name="loio20eae5e1751910148391d3079da8527e__sql_function_to_bigint_1sql_function_to_bigint_examples"/>

## Examples

The following example converts the value ***10*** to a BIGINT value ***10***:

```
SELECT TO_BIGINT ('10') "to bigint" FROM DUMMY;
```

The following example converts the value ***10.5*** to a BIGINT value ***10***, truncating the mantissa:

```
SELECT TO_BIGINT (10.5) "to bigint" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

