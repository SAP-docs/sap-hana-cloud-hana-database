<!-- loio20f017bc7519101490f792fb956eb045 -->

# TO\_REAL Function \(Data Type Conversion\)

Converts a *<value\>* to a REAL data type.



<a name="loio20f017bc7519101490f792fb956eb045__sql_function_to_real_1sql_function_to_real_syntax"/>

## Syntax

```
TO_REAL(<value>)
```



<a name="loio20f017bc7519101490f792fb956eb045__sql_function_to_real_1sql_function_to_real_description"/>

## Description

Converts a *<value\>* to a REAL \(single precision\) data type.



<a name="loio20f017bc7519101490f792fb956eb045__sql_function_to_real_1sql_function_to_real_examples"/>

## Example

The following example converts the value ***15.12*** to a REAL value and multiplies it by ***3*** to return the value ***45.36000061035156***.

```
SELECT 3*TO_REAL ('15.12') "to real" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

