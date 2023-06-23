<!-- loio20f226a1751910149edd8969c469d54d -->

# TO\_VARCHAR Function \(Data Type Conversion\)

In SAP HANA database, VARCHAR is an alias for the NVARCHAR data type. Please use the TO\_NVARCHAR function instead.



<a name="loio20f226a1751910149edd8969c469d54d__sql_function_to_varchar_1sql_function_to_varchar_syntax"/>

## Syntax

```
TO_VARCHAR(<value> [, <format>])
```



<a name="loio20f226a1751910149edd8969c469d54d__section_btr_k2z_pcb"/>

## Syntax Elements

See the TO\_NVARCHAR function for the descriptions of *<value\>* and *<format\>*.



<a name="loio20f226a1751910149edd8969c469d54d__sql_function_to_varchar_1sql_function_to_varchar_description"/>

## Description

Converts a given value to a VARCHAR data type, with an option to format the output value. While the function is called TO\_VARCHAR, in SAP HANA, VARCHAR is an alias for the NVARCHAR data type. Therefore, please use the TO\_NVARCHAR function instead.

**Related Information**  


[TO\_NVARCHAR Function \(Data Type Conversion\)](to-nvarchar-function-data-type-conversion-20efce3.md "Converts a given value to an NVARCHAR data type, with an option to format the output value.")

[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

