<!-- loio435ec476ab494ad6b8409f22abec13fe -->

# SERIES\_ROUND Function \(Series Data\)

Rounds a specified value to the series value using the specified rounding settings.



## Syntax

```
SERIES_ROUND( <value>, <increment_by>[, <rounding_mode> [, <alignment_expression> ] ] )
```



## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

Specifies that the value parameter can either be a numeric value or a date/time type.

```
<value> ::= { <real_const> | <datetime_const> }
```



</dd><dt><b>

*<increment\_by\>*

</b></dt>
<dd>

If the *<value\>* parameter is numeric, then the *<increment\_by\>* value must be a numeric value that defines the period of the series.

```
<increment_by>::= <interval_const>
```

If the *<value\>* parameter is a date/time type, then the *<increment\_by\>* value must be a string of the form "INTERVAL number units" where units is either YEAR, MONTH, DAY, HOUR, MINUTE, or SECOND and the number must be an integer, unless the unit type is SECOND and the associated data type is TIMESTAMP.



</dd><dt><b>

*<rounding\_mode\>*

</b></dt>
<dd>

Specifies that the natural zero that serves as the basis for the rounding depends on the data type and interval.

```
<rounding_mode> ::= ROUND_HALF_UP
 | ROUND_HALF_DOWN
 | ROUND_HALF_EVEN
 | ROUND_UP
 | ROUND_DOWN
 | ROUND_CEILING
 | ROUND_FLOOR
```

For numeric types, zero is the numeric zero. For date types with the interval units of DAY or smaller, zero is midnight. For MONTH and YEAR intervals, zero is midnight on the first day of the month, and midnight on the first day of the year, respectively. The following rounding modes are supported:


<table>
<tr>
<td valign="top">

**Mode**

</td>
<td valign="top">

**Description**

</td>
</tr>
<tr>
<td valign="top">

ROUND\_HALF\_UP

</td>
<td valign="top">

Specifies the default value. The value is rounded to the nearest series value. Values that fall halfway between two series values are rounded up, away from zero.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_HALF\_DOWN

</td>
<td valign="top">

Specifies that the value is rounded to the nearest series value. Values that fall halfway between two round values are rounded down, toward zero.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_HALF\_EVEN

</td>
<td valign="top">

Specifies that the value is rounded to the nearest series value. Values that fall halfway between two rounded values are rounded to the even series value, based on element number.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_UP

</td>
<td valign="top">

Specifies that the value is always rounded away from zero to the larger series value.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_DOWN

</td>
<td valign="top">

Specifies that the value is always rounded toward zero to the smaller series value.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_CEILING

</td>
<td valign="top">

Specifies that the value is always rounded in a positive direction to the larger series value.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_FLOOR

</td>
<td valign="top">

Specifies that the value is always rounded in a negative direction to the smaller series value.

</td>
</tr>
</table>



</dd><dt><b>

*<alignment\_expression\>*

</b></dt>
<dd>

Specifies that this parameter must be convertible to the *<value\>* data type.

```
<alignment_expression> ::= { <real_const> | <datetime_const> }
```

A *<rounding\_mode\>* must be specified when using this parameter.



</dd>
</dl>



## Description

Rounds a specified value to the series value using the specified rounding settings.



## Examples

The example below shows how to round up 4.5 to a series incremented by 3. It returns the result ***6***:

```
SELECT SERIES_ROUND(4.5, 3, ROUND_HALF_UP) "result" FROM DUMMY;
```

The example below shows how to round down 4.5 to a series incremented by 3. The example below shows returns the result ***3***:

```
SELECT SERIES_ROUND(4.5, 3, ROUND_HALF_DOWN) "result" FROM DUMMY;
```

The example below shows how to round down a date to the beginning of the year. It returns the result ***Jan 1, 2013***:

```
SELECT SERIES_ROUND('2013-05-24', 'INTERVAL 1 YEAR', ROUND_DOWN) "result"
    FROM DUMMY;
```

The example below shows how to round up a time to the next 10 minute interval. It returns the result***4:30:00 AM***:

```
SELECT SERIES_ROUND('04:25:01', 'INTERVAL 10 MINUTE') "result" FROM DUMMY;
```

