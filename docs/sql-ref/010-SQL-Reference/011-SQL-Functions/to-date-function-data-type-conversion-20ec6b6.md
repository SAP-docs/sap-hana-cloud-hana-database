<!-- loio20ec6b6975191014b835eb436e4827df -->

# TO\_DATE Function \(Data Type Conversion\)

Converts a date string into a DAYDATE data type.



<a name="loio20ec6b6975191014b835eb436e4827df__sql_function_to_date_1sql_function_to_date_syntax"/>

## Syntax

```
TO_DATE(<date> [, <format>])
```



<a name="loio20ec6b6975191014b835eb436e4827df__sql_function_to_date_1sql_function_to_date_description"/>

## Description

Converts the date string *<date\>* into a DAYDATE data type.

If the *<format\>* specifier is omitted, the conversion is performed using the date format model.



<a name="loio20ec6b6975191014b835eb436e4827df__sql_function_to_date_1sql_function_to_date_examples"/>

## Example

The following example converts the string ***2010-01-12*** to a DAYDATE value with the format ***YYYY-MM-DD***, and returns the value ***2010-01-12*** \(or another format like ***Jan 12, 2010***, depending on your date display settings\):

```
SELECT TO_DATE('2010-01-12', 'YYYY-MM-DD') "to date" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

