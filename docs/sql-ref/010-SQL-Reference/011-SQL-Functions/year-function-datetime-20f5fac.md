<!-- loio20f5fac6751910148dabd3c6821f907d -->

# YEAR Function \(Datetime\)

Returns the year number of a specified date.



<a name="loio20f5fac6751910148dabd3c6821f907d__sql_function_year_1sql_function_year_syntax"/>

## Syntax

```
YEAR(<date>)
```



<a name="loio20f5fac6751910148dabd3c6821f907d__sql_function_year_1sql_function_year_description"/>

## Description

Returns the year number of date *<date\>*.



<a name="loio20f5fac6751910148dabd3c6821f907d__sql_function_year_1sql_function_year_examples"/>

## Example

The following example returns the value ***2011*** for the year of the specified date:

```
SELECT YEAR (TO_DATE ('2011-05-30', 'YYYY-MM-DD')) "year" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

