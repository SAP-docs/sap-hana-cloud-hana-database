<!-- loio20e4ff2275191014825297d563cd0b85 -->

# MINUTE Function \(Datetime\)

Returns an integer representation of the minute for the specified time.



<a name="loio20e4ff2275191014825297d563cd0b85__sql_function_minute_1sql_function_minute_syntax"/>

## Syntax

```
MINUTE(<time>)
```



<a name="loio20e4ff2275191014825297d563cd0b85__sql_function_minute_1sql_function_minute_description"/>

## Description

Returns an integer representation of the minute for time *<time\>*.



<a name="loio20e4ff2275191014825297d563cd0b85__sql_function_minute_1sql_function_minute_examples"/>

## Example

The following example returns the value ***34*** as the minute for the specified time:

```
SELECT MINUTE ('12:34:56') "minute" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

