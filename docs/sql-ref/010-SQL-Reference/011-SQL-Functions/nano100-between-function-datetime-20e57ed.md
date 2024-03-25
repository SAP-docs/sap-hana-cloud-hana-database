<!-- loio20e57ed975191014be39aeb6e5fd3d89 -->

# NANO100\_BETWEEN Function \(Datetime\)

Computes the time difference between two dates to the precision of 0.1 microseconds.



<a name="loio20e57ed975191014be39aeb6e5fd3d89__sql_function_nano100_between_1sql_function_nano100_between_syntax"/>

## Syntax

```
NANO100_BETWEEN(<timestamp_1>, <timestamp_2>)
```



<a name="loio20e57ed975191014be39aeb6e5fd3d89__sql_function_nano100_between_1sql_function_nano100_between_description"/>

## Description

Computes the time difference between date arguments *<timestamp\_1\>* and *<timestamp\_2\>*, to the precision of 0.1 microseconds.



<a name="loio20e57ed975191014be39aeb6e5fd3d89__sql_function_nano100_between_1sql_function_nano100_between_examples"/>

## Example

The following example returns ***477*** as the time difference between the two specified dates:

```
SELECT NANO100_BETWEEN ('2021-01-31 00:00:00.0000176', '2021-01-31 00:00:00.0000653') "nano100 between" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

