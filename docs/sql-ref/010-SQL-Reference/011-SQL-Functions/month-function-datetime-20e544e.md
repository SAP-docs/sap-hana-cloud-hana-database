<!-- loio20e544ea75191014b8209a9fc217ce0e -->

# MONTH Function \(Datetime\)

Returns the number of the month from the specified date.



<a name="loio20e544ea75191014b8209a9fc217ce0e__sql_function_month_1sql_function_month_syntax"/>

## Syntax

```
MONTH(<date>)
```



<a name="loio20e544ea75191014b8209a9fc217ce0e__sql_function_month_1sql_function_month_description"/>

## Description

Returns the number of the month from date *<date\>*.



<a name="loio20e544ea75191014b8209a9fc217ce0e__sql_function_month_1sql_function_month_examples"/>

## Example

The following example returns the value ***5***, the month for the date specified:

```
SELECT MONTH ('2011-05-30') "month" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

