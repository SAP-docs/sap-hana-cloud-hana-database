<!-- loioeb21d794c95341a9816bb528f134d491 -->

# SERIES\_PERIOD\_TO\_ELEMENT Function \(Series Data\)

Returns the one-based series element number that the given period value is associated with.



## Syntax

```
SERIES_PERIOD_TO_ELEMENT( 
 <value>, {<increment_by>, <min_value>, <max_value> [, <rounding_mode>]
 [, <rounding_mode>]}
 )
```



## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

Specifies that the *<value\>* parameter can either be a numeric value or a date/time type.

```
<value> ::= INTEGER | DOUBLE | TIMESTAMP
```



</dd><dt><b>

*<increment\_by\>*

</b></dt>
<dd>

Sets the increment value.

```
<increment_by> ::= <identifier>
```

If the *<value\>* parameter is a date/time type, then the *<increment\_by\>* parameter should be a string in the form "INTERVAL number units" where units is either YEAR, MONTH, DAY, HOUR, MINUTE, or SECOND and the number must be an integer, unless the units type is SECOND and the associated data type is TIMESTAMP. If the value is numeric, then the *<increment\_by\>* parameter should be a numeric value that defines the period of the series.



</dd><dt><b>

*<min\_value\>*

</b></dt>
<dd>

Sets the minimum period value.

```
<min_value> ::= <integer>
```

For an equidistant series, there is a mapping between periods and elements. The periods are in the space of the period columns, usually timestamps. The elements are always BIGINT. The element 1 represents the first period, associated with *<min\_value\>*.



</dd><dt><b>

*<max\_value\>*

</b></dt>
<dd>

Sets the maximum period value.

```
<max_value> ::= <integer>
```



</dd><dt><b>

*<rounding\_mode\>*

</b></dt>
<dd>

Specifies that if the period value is not on a series period value, then it is rounded to the nearest series period value, which returns the associated element number.

```
<rounding_mode> ::= ROUND_HALF_UP
 | ROUND_HALF_DOWN
 | ROUND_HALF_EVEN
 | ROUND_UP
 | ROUND_DOWN
 | ROUND_CEILING
 | ROUND_FLOOR
```

The supported rounding modes are:


<table>
<tr>
<td valign="top">

**Rounding mode**

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

Specifies that the value is rounded to the nearest series value. Values that fall halfway between two series values are rounded up away from zero.

This is the default value.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_HALF\_DOWN

</td>
<td valign="top">

Specifies that the value is rounded to the nearest series value. Values that fall halfway between two round values are rounded down toward zero.

</td>
</tr>
<tr>
<td valign="top">

ROUND\_HALF\_EVEN

</td>
<td valign="top">

Specifies that the value is rounded to the nearest series value. Values that fall halfway between two rounded values are rounded to the even series value based on element number.

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

Specifies that the value is always rounded towards zero to the smaller series value.

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

*<series\_table\>*

</b></dt>
<dd>

If a series table reference is used, then this specifies that the values for *<increment\_by\>*, *<min\_value\>*, and *<max\_value\>* from the SERIES TABLE definition are used as the parameters for this function.

```
<series_table> ::= <identifier>
```



</dd>
</dl>



## Description

Returns the one-based series element number with which the given period value is associated, where period = min\_value + \( element - 1 \) \* interval.



## Examples

The following example returns the result 4:

```
SELECT SERIES_PERIOD_TO_ELEMENT(5, 2, 0, 10, ROUND_HALF_UP) "element" FROM DUMMY;
```

The following example returns the result 3:

```
SELECT SERIES_PERIOD_TO_ELEMENT(5, 2, 0, 10, ROUND_HALF_DOWN) "element" FROM DUMMY;
```

The example below picks the next element rounded down from 2014-01-05 12:00:00 from a date series from 2014-01-01 to 2014-12-32 in increments of 1 day. It returns the result 5:

```
SELECT SERIES_PERIOD_TO_ELEMENT(
    '2014-01-05 12:00:00',
    'INTERVAL 1 DAY',
    '2014-01-01',
    '2014-12-31',
    ROUND_HALF_DOWN) "element" FROM DUMMY;
```

