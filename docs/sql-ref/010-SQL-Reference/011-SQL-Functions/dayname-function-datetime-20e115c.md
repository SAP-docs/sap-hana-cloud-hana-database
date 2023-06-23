<!-- loio20e115c375191014a259acd3d72e3722 -->

# DAYNAME Function \(Datetime\)

Returns the weekday name for the specified date.



<a name="loio20e115c375191014a259acd3d72e3722__sql_function_dayname_1sql_function_dayname_syntax"/>

## Syntax

```
DAYNAME(<date>)
```



<a name="loio20e115c375191014a259acd3d72e3722__sql_function_dayname_1sql_function_dayname_description"/>

## Description

Returns the weekday in English for the specified date.



<a name="loio20e115c375191014a259acd3d72e3722__sql_function_dayname_1sql_function_dayname_examples"/>

## Example

The following example returns ***Monday*** as the weekday for the specified date:

```
SELECT DAYNAME ('2011-05-30') "dayname" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

