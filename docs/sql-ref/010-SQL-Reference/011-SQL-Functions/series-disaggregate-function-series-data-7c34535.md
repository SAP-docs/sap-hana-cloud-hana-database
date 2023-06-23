<!-- loio7c34535972b94f74b1a9c1760f9e4a8e -->

# SERIES\_DISAGGREGATE Function \(Series Data\)

Generates a complete series table with rows disaggregated into defined partitions.



## Syntax

```
SERIES_DISAGGREGATE(
    <source_increment_by>, <target_increment_by>
    [, <value_range> ] )
    | { SERIES_DISAGGREGATE_TINYINT
    | SERIES_DISAGGREGATE_SMALLINT
    | SERIES_DISAGGREGATE_INTEGER
    | SERIES_DISAGGREGATE_BIGINT
    | SERIES_DISAGGREGATE_SMALLDECIMAL
    | SERIES_DISAGGREGATE_DECIMAL
    | SERIES_DISAGGREGATE_TIME
    | SERIES_DISAGGREGATE_DATE
    | SERIES_DISAGGREGATE_SECONDDATE
    | SERIES_DISAGGREGATE_TIMESTAMP }
    (<source_increment_by>, <target_increment_by>, <min_value>, <max_value>)
```



## Syntax Elements


<dl>
<dt><b>

*<value\_range\>*

</b></dt>
<dd>

Defines the range of values.

```
<value_range> ::= <min_value> [, <max_value>]

<min_value> ::= <real_const> | <datetime_const>
<max_value> ::= <real_const> | <datetime_const>
```

The *<min\_value\>* is the greater *<min\_value\>* of the two specified tables, and the *<max\_value\>* is the lesser *<max\_value\>* of the two specified tables.



</dd><dt><b>

*<source\_increment\_by\>*

</b></dt>
<dd>

Sets the source increment value.

```
<source_increment_by> ::= <real_const> | <datetime_const>
```



</dd><dt><b>

*<target\_increment\_by\>*

</b></dt>
<dd>

Sets the target increment value.

```
<target_increment_by> ::= <real_const> | <datetime_const>
```



</dd><dt><b>

*<constant\_literal\>*

</b></dt>
<dd>

The *<constant\_literal\>* parameter is defined as a *<real\_const\>* or a *<datetime\_const\>*.

```
<constant_literal> ::= <real_const> | <datetime_const>
```

It is either an integer constant, an interval constant, or a defined number of elements between a minimum and maximum. If the period type is a DATETIME, then the number needs to be preceded by INTERVAL followed by a time unit, such as YEAR, MONTH, DAY, HOUR, MINUTE, or SECOND. Exponential notation is allowed.



</dd>
</dl>



## Description

For date/time types, the *<increment\_by\>* parameter should be a string in the form "INTERVAL number units" where units is either YEAR, MONTH, DAY, HOUR, MINUTE, or SECOND and the number must be an integer, unless the units type is SECOND and the associated data type is TIMESTAMP.

The *<min\_value\>* parameter for the numeric versions of this function does not need to be aligned to numeric zero with respect to the *<increment\_by\>* value. You can specify a *<source\_increment\>* of 2 and a *<min\_value\>* of 1, which results in a source series of 1, 3, 5, and so on.

This function returns a table with the following columns:


<table>
<tr>
<td valign="top">

**Column Name**



</td>
<td valign="top">

**Column Type**



</td>
<td valign="top">

**Description**



</td>
</tr>
<tr>
<td valign="top">

SOURCE\_PERIOD\_START



</td>
<td valign="top">

PERIOD\_TYPE



</td>
<td valign="top">

Specifies the start of the source period that generated this row.



</td>
</tr>
<tr>
<td valign="top">

SOURCE\_PERIOD\_END



</td>
<td valign="top">

PERIOD\_TYPE



</td>
<td valign="top">

Specifies the end of the source period that generated this row.



</td>
</tr>
<tr>
<td valign="top">

GENERATED\_PERIOD\_START



</td>
<td valign="top">

PERIOD\_TYPE



</td>
<td valign="top">

Displays the start of the period represented by this row, including the period\_start. This value is a closed interval at the start.



</td>
</tr>
<tr>
<td valign="top">

GENERATED\_PERIOD\_END



</td>
<td valign="top">

PERIOD\_TYPE



</td>
<td valign="top">

Displays the end of the period represented by this row as an open interval. The period represented by this row consists of all times that are greater than or equal to the start and less than the end.



</td>
</tr>
<tr>
<td valign="top">

ELEMENT\_NUMBER\_IN\_SOURCE\_PERIOD



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Specifies the element number of this period within its source interval.



</td>
</tr>
<tr>
<td valign="top">

ELEMENT\_NUMBER\_IN\_GENERATED\_SERIES



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Specifies the element number within the whole result set.



</td>
</tr>
<tr>
<td valign="top">

FRACTION\_OF\_SOURCE\_PERIOD



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Specifies the fraction of the length of the source period that this generated period covers.



</td>
</tr>
<tr>
<td valign="top">

FRACTION\_OF\_MIN\_MAX\_RANGE



</td>
<td valign="top">

DOUBLE



</td>
<td valign="top">

Specifies the fraction of the length of all generated periods that this generated period covers.



</td>
</tr>
</table>



## Examples

The example below generates a series of dates ranging from 1999-01-01 to 2001-01-04:

```
SELECT * FROM SERIES_DISAGGREGATE_DATE
    ('INTERVAL 1 year', 'INTERVAL 3 MONTH', '1999-01-01', '2001-01-04' );
```

The following result is returned by the example above:


<table>
<tr>
<th valign="top">

SOURCE\_PERIOD\_START



</th>
<th valign="top">

SOURCE\_PERIOD\_END



</th>
<th valign="top">

GENERATED\_PERIOD\_START



</th>
<th valign="top">

GENERATED\_PERIOD\_END



</th>
<th valign="top">

ELEMENT\_NUMBER\_IN\_SOURCE\_PERIOD



</th>
<th valign="top">

ELEMENT\_NUMBER\_IN\_GENERATED\_SERIES



</th>
<th valign="top">

FRACTION\_OF\_SOURCE\_PERIOD



</th>
<th valign="top">

FRACTION\_OF\_MIN\_MAX\_RANGE



</th>
</tr>
<tr>
<td valign="top">

Jan 1, 1999



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jan 1, 1999



</td>
<td valign="top">

Apr 1, 1999



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

0.2465753424657534



</td>
<td valign="top">

0.12311901504787962



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 1999



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Apr 1, 1999



</td>
<td valign="top">

Jul 1, 1999



</td>
<td valign="top">

1



</td>
<td valign="top">

2



</td>
<td valign="top">

0.2493150684931507



</td>
<td valign="top">

0.12448700410396717



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 1999



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jul 1, 1999



</td>
<td valign="top">

Oct 1, 1999



</td>
<td valign="top">

1



</td>
<td valign="top">

3



</td>
<td valign="top">

0.25205479452054796



</td>
<td valign="top">

0.12585499316005472



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 1999



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Oct 1, 1999



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

1



</td>
<td valign="top">

4



</td>
<td valign="top">

0.25205479452054796



</td>
<td valign="top">

0.12585499316005472



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jan 1, 2001



</td>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Apr 1, 2000



</td>
<td valign="top">

2



</td>
<td valign="top">

5



</td>
<td valign="top">

0.24863387978142076



</td>
<td valign="top">

0.12448700410396717



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jan 1, 2001



</td>
<td valign="top">

Apr 1, 2000



</td>
<td valign="top">

Jul 1, 2000



</td>
<td valign="top">

2



</td>
<td valign="top">

6



</td>
<td valign="top">

0.24863387978142076



</td>
<td valign="top">

0.12448700410396717



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jan 1, 2001



</td>
<td valign="top">

Jul 1, 2000



</td>
<td valign="top">

Oct 1, 2000



</td>
<td valign="top">

2



</td>
<td valign="top">

7



</td>
<td valign="top">

0.25136612021857924



</td>
<td valign="top">

0.12585499316005472



</td>
</tr>
<tr>
<td valign="top">

Jan 1, 2000



</td>
<td valign="top">

Jan 1, 2001



</td>
<td valign="top">

Oct 1, 2000



</td>
<td valign="top">

Jan 1, 2001



</td>
<td valign="top">

2



</td>
<td valign="top">

8



</td>
<td valign="top">

0.25136612021857924



</td>
<td valign="top">

0.12585499316005472



</td>
</tr>
</table>

The example above returns a result similar to the following:


<table>
<tr>
<th valign="top">

ELEMENT\_NUMBER



</th>
<th valign="top">

VAL



</th>
<th valign="top">

ELEMENT\_NUMBER\_IN\_GENERATED\_SERIES



</th>
<th valign="top">

DA



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2.21



</td>
<td valign="top">

1



</td>
<td valign="top">

1.105



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2.21



</td>
<td valign="top">

2



</td>
<td valign="top">

1.105



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

5.52



</td>
<td valign="top">

3



</td>
<td valign="top">

2.76



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

5.52



</td>
<td valign="top">

4



</td>
<td valign="top">

2.76



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

2.35



</td>
<td valign="top">

5



</td>
<td valign="top">

1.175



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

2.35



</td>
<td valign="top">

6



</td>
<td valign="top">

1.175



</td>
</tr>
<tr>
<td valign="top">

...



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
</table>

