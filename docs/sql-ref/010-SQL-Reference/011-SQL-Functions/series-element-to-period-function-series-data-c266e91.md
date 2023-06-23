<!-- loioc266e91b94484674b7da636f3f477158 -->

# SERIES\_ELEMENT\_TO\_PERIOD Function \(Series Data\)

Returns the series period value associated with the specified one-based series element number.



## Syntax

```
SERIES_ELEMENT_TO_PERIOD( <element_number>, { <increment_by>, <min_value>, <max_value> } )
```



## Syntax Elements


<dl>
<dt><b>

*<element\_number\>*

</b></dt>
<dd>

Specifies the element number.

```
<element_number> ::= INTEGER
```



</dd><dt><b>

*<increment\_by\>*

</b></dt>
<dd>

Defined as either an integer constant, an interval constant, or a defined number of elements between a minimum and a maximum.

```
<increment_by> ::= <real_const> | <interval_const>
```

If the period type is a DATETIME, then the number needs to be preceded by INTERVAL followed by a time unit, such as YEAR, MONTH, DAY, HOUR, MINUTE, or SECOND. Exponential notation is allowed.



</dd><dt><b>

*<min\_value\>*

</b></dt>
<dd>

Specifies the minimum value. It can either be a numeric or a date/time value.

```
<min_value> ::= <real_const> | <datetime_const>
```



</dd><dt><b>

*<max\_value\>*

</b></dt>
<dd>

Specifies the maximum value. It can either be a numeric or a date/time value.

```
<max_value> ::= <real_const> | <datetime_const>
```



</dd>
</dl>



## Description

Returns the series period value associated with the provided one-based series element number, where rounded\_period = SERIES\_ROUND \(period, interval, round\_mode\) and element = 1 + \( rounded\_period - min\_value \) / interval.



## Examples

The example below picks the fifth element from a series from 0 to 10 in increments of 2 and returns ***8***:

```
SELECT SERIES_ELEMENT_TO_PERIOD(5, 2, 0, 10) "val" FROM DUMMY;
```

The example below picks the sixth element from a series from 1 to 10 in increments of 1.25 and returns ***7.25***:

```
SELECT SERIES_ELEMENT_TO_PERIOD(6, 1.25, 1, 10) "val" FROM DUMMY;
```

The example below picks the seventh element from a date series from 2014-01-01 to 2014-12-31 in increments of 1 day and returns ***Jan 7, 2014***:

```
SELECT SERIES_ELEMENT_TO_PERIOD(7, 'INTERVAL 1 DAY', '2014-01-01', '2014-12-31')
    "val" FROM DUMMY;
```

The example below picks the seventh element from a date series from 2014-01-01 to 2014-12-31 in increments of 1 month and returns ***Jul 1, 2014***:

```
SELECT SERIES_ELEMENT_TO_PERIOD(7, 'INTERVAL 1 MONTH',
    '2014-01-01', '2014-12-31') "val" FROM DUMMY;
```

The example below picks the 500.000th element from a time series from 2014-01-01 to 2014-12-31 in increments of 1.5 seconds and returns ***Jan 9, 2014 4:19:58.5 PM***:

```
SELECT SERIES_ELEMENT_TO_PERIOD(500000, 'INTERVAL 1.5 SECOND',
    '2014-01-01 00:00:00.000', '2014-12-31') "val" FROM DUMMY;
```

