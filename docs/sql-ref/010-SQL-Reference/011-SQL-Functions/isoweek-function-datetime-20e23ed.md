<!-- loio20e23edc7519101482eae3271722de36 -->

# ISOWEEK Function \(Datetime\)

Returns the ISO year and week number for a specified date.



<a name="loio20e23edc7519101482eae3271722de36__sql_function_isoweek_1sql_function_isoweek_syntax"/>

## Syntax

```
ISOWEEK(<date>)
```



<a name="loio20e23edc7519101482eae3271722de36__sql_function_isoweek_1sql_function_isoweek_description"/>

## Description

Returns the ISO year and week numbers of the date specified by *<date\>*. The week number is prefixed by the letter W.

Both the WEEK and ISOWEEK functions return the week number for a specified date but the format of the result is quite different, and the two functions may handle the first week of the new year differently. For example, when supplied the date 2017-01-01, the WEEK function considers the date to be part of the *first week of 2017* and returns 1, whereas ISOWEEK considers the date to be part of the *last week of 2016* and returns 2016-W52.

ISOWEEK has either 52 or 53 full weeks, with the extra week considered to be a leap week



<a name="loio20e23edc7519101482eae3271722de36__sql_function_isoweek_1sql_function_isoweek_examples"/>

## Example

The following example returns the value ***2011-W22*** for the ISO year and week numbers of the specified date:

```
SELECT ISOWEEK (TO_DATE('2011-05-30', 'YYYY-MM-DD')) "isoweek" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

