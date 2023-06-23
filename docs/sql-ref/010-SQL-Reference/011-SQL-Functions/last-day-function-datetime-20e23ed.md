<!-- loio20e23ede75191014a1c2e3271722de36 -->

# LAST\_DAY Function \(Datetime\)

Returns the date of the last day of the month that contains the specified date.



<a name="loio20e23ede75191014a1c2e3271722de36__sql_function_last_day_1sql_function_last_day_syntax"/>

## Syntax

```
LAST_DAY(<date>)
```



<a name="loio20e23ede75191014a1c2e3271722de36__sql_function_last_day_1sql_function_last_day_description"/>

## Description

Returns the date of the last day of the month that contains the date *<date\>*.



<a name="loio20e23ede75191014a1c2e3271722de36__sql_function_last_day_1sql_function_last_day_examples"/>

## Example

The following example returns the value ***2010-01-31*** \(or another format like ***Jan 31, 2010***, depending on your date display settings\):

```
SELECT LAST_DAY (TO_DATE('2010-01-04', 'YYYY-MM-DD')) "last day" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

