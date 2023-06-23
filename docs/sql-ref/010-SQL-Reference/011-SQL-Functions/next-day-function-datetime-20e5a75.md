<!-- loio20e5a75e75191014b2539bd2c7772cf2 -->

# NEXT\_DAY Function \(Datetime\)

Returns the date of the day following the specified date.



<a name="loio20e5a75e75191014b2539bd2c7772cf2__sql_function_next_day_1sql_function_next_day_syntax"/>

## Syntax

```
NEXT_DAY(<date>)
```



<a name="loio20e5a75e75191014b2539bd2c7772cf2__sql_function_next_day_1sql_function_next_day_description"/>

## Description

Returns the date of the day following the specified date.



<a name="loio20e5a75e75191014b2539bd2c7772cf2__sql_function_next_day_1sql_function_next_day_examples"/>

## Example

The following example returns ***2010-01-01*** as the day after ***2009-12-31***:

```
SELECT NEXT_DAY (TO_DATE ('2009-12-31', 'YYYY-MM-DD')) "next day" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

