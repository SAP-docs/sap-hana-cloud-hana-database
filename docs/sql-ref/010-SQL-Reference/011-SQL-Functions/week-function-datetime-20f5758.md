<!-- loio20f5758b7519101498b28e41757fe664 -->

# WEEK Function \(Datetime\)

Returns a week number between 1 and 54 for the specified date.



<a name="loio20f5758b7519101498b28e41757fe664__sql_function_week_1sql_function_week_syntax"/>

## Syntax

```
WEEK(<date>)
```



<a name="loio20f5758b7519101498b28e41757fe664__sql_function_week_1sql_function_week_description"/>

## Description

Returns the week number of the year as an integer. Weeks start Monday and end Sunday. The first days of the year up to the first Sunday are week 1; the seven days that begin with the day after the first Sunday are week 2, and so on.

Both the WEEK and ISOWEEK functions return the week number for a specified date but the format of the result is quite different, and the two functions may handle the first week of the new year differently. For example, when supplied the date `2017-01-01`, the WEEK function considers the date to be part of the *first week of 2017* and returns ***1***, whereas `ISOWEEK` considers the date to be part of the *last week of 2016* and returns ***2016-W52***.



<a name="loio20f5758b7519101498b28e41757fe664__sql_function_week_1sql_function_week_examples"/>

## Example

The following example returns the value ***23*** for the week number of the specified date:

```
SELECT  WEEK (TO_DATE('2011-05-30', 'YYYY-MM-DD')) "week" FROM DUMMY;
```

The following example returns the value ***53*** for the week number of the specified date:

```
SELECT  WEEK ('2016-12-31') FROM DUMMY;
```

The following example returns the value ***1*** for the week number of the specified date:

```
SELECT  WEEK ('2017-01-01') FROM DUMMY;
```

The following example returns the value ***2*** for the week number of the specified date:

```
SELECT  WEEK ('2017-01-02') FROM DUMMY;
```

**Related Information**  


[ISOWEEK Function \(Datetime\)](isoweek-function-datetime-20e23ed.md "Returns the ISO year and week number for a specified date.")

[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

