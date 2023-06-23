<!-- loio20e562537519101499c6a760e719afbd -->

# MONTHNAME Function \(Datetime\)

Returns the name of the month for the specified date.



<a name="loio20e562537519101499c6a760e719afbd__sql_function_monthname_1sql_function_monthname_syntax"/>

## Syntax

```
MONTHNAME(<date>)
```



<a name="loio20e562537519101499c6a760e719afbd__sql_function_monthname_1sql_function_monthname_description"/>

## Description

Returns the name of the month for date *<date\>*.



<a name="loio20e562537519101499c6a760e719afbd__sql_function_monthname_1sql_function_monthname_examples"/>

## Example

The following example returns the value ***MAY***, the month name of the specified date:

```
SELECT MONTHNAME ('2011-05-30') "monthname" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

