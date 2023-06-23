<!-- loio20e7152675191014bb54fed5d26b9e6f -->

# SECOND Function \(Datetime\)

Returns the second portion of a specified time.



<a name="loio20e7152675191014bb54fed5d26b9e6f__sql_function_second_1sql_function_second_syntax"/>

## Syntax

```
SECOND(<time>)
```



<a name="loio20e7152675191014bb54fed5d26b9e6f__sql_function_second_1sql_function_second_description"/>

## Description

Returns a value of seconds for a given time.

Subseconds are included for TIMESTAMP datatypes.



<a name="loio20e7152675191014bb54fed5d26b9e6f__sql_function_second_1sql_function_second_examples"/>

## Examples

The following example returns the value ***56*** for the seconds of the specified time:

```
SELECT SECOND ('12:34:56') "second" FROM DUMMY;
```

The following example returns the value ***56.789*** for the subseconds of the specified time:

```
SELECT SECOND ('2014-03-25 12:34:56.789') "subseconds" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

