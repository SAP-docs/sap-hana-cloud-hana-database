<!-- loio20f1a5b075191014b773acf0dc277cae -->

# TO\_TIMESTAMP Function \(Data Type Conversion\)

Converts a date string to a TIMESTAMP data type.



<a name="loio20f1a5b075191014b773acf0dc277cae__sql_function_to_timestamp_1sql_function_to_timestamp_syntax"/>

## Syntax

```
TO_TIMESTAMP(<date> [, <format>])
```



<a name="loio20f1a5b075191014b773acf0dc277cae__sql_function_to_timestamp_1sql_function_to_timestamp_description"/>

## Description

Converts date string *<date\>* to the TIMESTAMP data type.

If the *<format\>* specifier is omitted, then the conversion is performed using the date format model.



<a name="loio20f1a5b075191014b773acf0dc277cae__sql_function_to_timestamp_1sql_function_to_timestamp_examples"/>

## Example

The following example converts the value `11-Jan-2010 01:30 PM` to the TIMESTAMP value ***2010-01-11 13:30:00.0*** using the format `DD-Mon-YYYY HH:MI AM`:

```
SELECT TO_TIMESTAMP ('11-Jan-2010 01:30 PM', 'DD-Mon-YYYY HH:MI AM') AS "to timestamp" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

