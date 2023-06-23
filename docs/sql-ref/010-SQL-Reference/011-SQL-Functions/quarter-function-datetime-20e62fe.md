<!-- loio20e62fe875191014b78bd015a16966fb -->

# QUARTER Function \(Datetime\)

Returns the quarter for the specified date.



<a name="loio20e62fe875191014b78bd015a16966fb__sql_function_quarter_1sql_function_quarter_syntax"/>

## Syntax

```
QUARTER(<date>, [, <start_month> ])
```



<a name="loio20e62fe875191014b78bd015a16966fb__sql_function_quarter_1sql_function_quarter_description"/>

## Description

Returns the numerical year and quarter of date *<date\>*. The first quarter starts in the month specified by *<start\_month\>*. If *<start\_month\>* is not specified, then the first quarter is assumed to begin in January.



<a name="loio20e62fe875191014b78bd015a16966fb__sql_function_quarter_1sql_function_quarter_examples"/>

## Example

The following example returns the value ***2011-Q4*** as the year and quarter for the specified date:

```
SELECT QUARTER (TO_DATE('2012-01-01', 'YYYY-MM-DD'), 2) "quarter" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

