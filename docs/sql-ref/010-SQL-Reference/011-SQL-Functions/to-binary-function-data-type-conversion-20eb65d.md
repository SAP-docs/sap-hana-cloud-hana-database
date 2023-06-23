<!-- loio20eb65d4751910149a7dc10f93a24a75 -->

# TO\_BINARY Function \(Data Type Conversion\)

Converts a value to a BINARY data type.



<a name="loio20eb65d4751910149a7dc10f93a24a75__sql_function_to_binary_1sql_function_to_binary_syntax"/>

## Syntax

```
TO_BINARY(<value>)
```



<a name="loio20eb65d4751910149a7dc10f93a24a75__sql_function_to_binary_1sql_function_to_binary_description"/>

## Description

Converts a *<value\>* to a BINARY data type.



<a name="loio20eb65d4751910149a7dc10f93a24a75__sql_function_to_binary_1sql_function_to_binary_examples"/>

## Example

The following example converts the value ***abc*** to the BINARY value ***616263***.

```
SELECT TO_BINARY ('abc') "to binary" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

