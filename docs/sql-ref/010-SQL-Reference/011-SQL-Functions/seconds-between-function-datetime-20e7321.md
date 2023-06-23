<!-- loio20e73218751910148528de57be340475 -->

# SECONDS\_BETWEEN Function \(Datetime\)

Computes the number of seconds between two specified dates.



<a name="loio20e73218751910148528de57be340475__sql_function_seconds_between_1sql_function_seconds_between_syntax"/>

## Syntax

```
SECONDS_BETWEEN(<date_1>, <date_2>)
```



<a name="loio20e73218751910148528de57be340475__sql_function_seconds_between_1sql_function_seconds_between_description"/>

## Description

Computes the number of seconds between date arguments *<date\_1\>* and *<date\_2\>*, which is semantically equal to \(*<date\_2\>* - *<date\_1\>*\).



<a name="loio20e73218751910148528de57be340475__sql_function_seconds_between_1sql_function_seconds_between_examples"/>

## Example

The following example returns the value ***2,678,400*** as the number of seconds between the two specified dates:

```
SELECT SECONDS_BETWEEN ('2009-12-05', '2010-01-05') "seconds between" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

