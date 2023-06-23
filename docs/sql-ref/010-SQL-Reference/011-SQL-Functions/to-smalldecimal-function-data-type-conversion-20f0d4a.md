<!-- loio20f0d4aa75191014a96ef18b874d6f2d -->

# TO\_SMALLDECIMAL Function \(Data Type Conversion\)

Converts the specified value to a SMALLDECIMAL data type.



<a name="loio20f0d4aa75191014a96ef18b874d6f2d__sql_function_to_smalldecimal_1sql_function_to_smalldecimal_syntax"/>

## Syntax

```
TO_SMALLDECIMAL(<value>)
```



<a name="loio20f0d4aa75191014a96ef18b874d6f2d__sql_function_to_smalldecimal_1sql_function_to_smalldecimal_description"/>

## Description

Converts the specified value to a SMALLDECIMAL data type.



<a name="loio20f0d4aa75191014a96ef18b874d6f2d__sql_function_to_smalldecimal_1sql_function_to_smalldecimal_examples"/>

## Example

The following example converts the value ***7654321.89*** to the SMALLDECIMAL value ***7,654,321.89***:

```
SELECT TO_SMALLDECIMAL(7654321.89) "to smalldecimal" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

