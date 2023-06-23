<!-- loio20f5bb79751910148e7198206fbd199f -->

# WEEKDAY Function \(Datetime\)

Returns the day of the week for the specified date.



<a name="loio20f5bb79751910148e7198206fbd199f__sql_function_weekday_1sql_function_weekday_syntax"/>

## Syntax

```
WEEKDAY(<date>)
```



<a name="loio20f5bb79751910148e7198206fbd199f__sql_function_weekday_1sql_function_weekday_description"/>

## Description

Returns an integer representation of the day of the week for date *<date\>*. The return value ranges from 0 to 6, representing Monday\(0\) through to Sunday\(6\).



<a name="loio20f5bb79751910148e7198206fbd199f__sql_function_weekday_1sql_function_weekday_examples"/>

## Example

The following example returns the value ***4*** as the weekday of the specified date:

```
SELECT WEEKDAY (TO_DATE ('2010-12-31', 'YYYY-MM-DD')) "week day" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

