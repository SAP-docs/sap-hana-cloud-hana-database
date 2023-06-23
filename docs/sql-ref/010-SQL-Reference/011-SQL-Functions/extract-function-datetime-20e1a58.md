<!-- loio20e1a58475191014a343f6fe96c9846c -->

# EXTRACT Function \(Datetime\)

Returns the requested portion of a specified date.



<a name="loio20e1a58475191014a343f6fe96c9846c__sql_function_extract_1sql_function_extract_syntax"/>

## Syntax

```
EXTRACT( {YEAR | MONTH | DAY | HOUR | MINUTE | SECOND} FROM <date> )
```



<a name="loio20e1a58475191014a343f6fe96c9846c__sql_function_extract_1sql_function_extract_description"/>

## Description

Returns the requested portion from the specified date.



<a name="loio20e1a58475191014a343f6fe96c9846c__sql_function_extract_1sql_function_extract_examples"/>

## Example

The following example returns the value ***2010*** for the year extracted from the specified date:

```
SELECT EXTRACT (YEAR FROM TO_DATE ('2010-01-04', 'YYYY-MM-DD')) "extract" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

