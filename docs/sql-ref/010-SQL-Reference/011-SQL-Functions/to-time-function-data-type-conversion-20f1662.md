<!-- loio20f1662775191014a6f7cead37a5937a -->

# TO\_TIME Function \(Data Type Conversion\)

Converts a specified time string to a TIME data type.



<a name="loio20f1662775191014a6f7cead37a5937a__sql_function_to_time_1sql_function_to_time_syntax"/>

## Syntax

```
TO_TIME(<time> [, <format>])
```



<a name="loio20f1662775191014a6f7cead37a5937a__sql_function_to_time_1sql_function_to_time_description"/>

## Description

Converts time string *<time\>* to the TIME data type.

If the *<format\>* specifier is omitted, then the conversion is performed using the time format model.



<a name="loio20f1662775191014a6f7cead37a5937a__sql_function_to_time_1sql_function_to_time_examples"/>

## Example

The following example converts the value `08:30 AM` to a TIME value with format `HH:MI AM` and returns the value ***08:30:00***:

```
SELECT TO_TIME ('08:30 AM', 'HH:MI AM') "to time" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

