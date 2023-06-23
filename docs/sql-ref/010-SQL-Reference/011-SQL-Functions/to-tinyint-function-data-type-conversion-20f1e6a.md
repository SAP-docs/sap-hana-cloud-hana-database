<!-- loio20f1e6a175191014a59583315d023b7f -->

# TO\_TINYINT Function \(Data Type Conversion\)

Converts a value to a TINYINT data type.



<a name="loio20f1e6a175191014a59583315d023b7f__sql_function_to_tinyint_1sql_function_to_tinyint_syntax"/>

## Syntax

```
TO_TINYINT(<value>)
```



<a name="loio20f1e6a175191014a59583315d023b7f__sql_function_to_tinyint_1sql_function_to_tinyint_description"/>

## Description

Converts the *<value\>* to a TINYINT data type.

If the input value has a mantissa, then these digits are truncated during the conversion process.



<a name="loio20f1e6a175191014a59583315d023b7f__sql_function_to_tinyint_1sql_function_to_tinyint_examples"/>

## Examples

The following example converts the value ***10*** to the TINYINT value ***10***:

```
SELECT TO_TINYINT ('10') "to tinyint" FROM DUMMY;
```

The following example converts the value ***10.5*** to the TINYINT value ***10***, truncating the mantissa:

```
SELECT TO_TINYINT(10.5) "to tinyint" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

