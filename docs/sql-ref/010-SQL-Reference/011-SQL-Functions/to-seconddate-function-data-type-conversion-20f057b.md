<!-- loio20f057b075191014809a8f010c03d7c2 -->

# TO\_SECONDDATE Function \(Data Type Conversion\)

Converts a specified date string to a SECONDDATE data type.



<a name="loio20f057b075191014809a8f010c03d7c2__sql_function_to_seconddate_1sql_function_to_seconddate_syntax"/>

## Syntax

```
TO_SECONDDATE(<date> [, <format>])
```



<a name="loio20f057b075191014809a8f010c03d7c2__sql_function_to_seconddate_1sql_function_to_seconddate_description"/>

## Description

If the *<format\>* specifier is omitted, then the conversion is performed using the date format model.



<a name="loio20f057b075191014809a8f010c03d7c2__sql_function_to_seconddate_1sql_function_to_seconddate_examples"/>

## Example

The following example converts the value ***2010-01-11 13:30:00*** to a SECONDDATE data type with format ***YYYY-MM-DD HH24:MI:SS*** and returns the value ***2010-01-11 13:30:00.0*** \(or another format like ***Jan 11, 2010 1:30:00.0 PM***, depending on your date display settings\):

```
SELECT TO_SECONDDATE ('2010-01-11 13:30:00', 'YYYY-MM-DD HH24:MI:SS') "to seconddate" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

