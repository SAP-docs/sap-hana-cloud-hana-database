<!-- loio9a78dfb3cd8240f4be22495a098e65ea -->

# BINNING Function \(Window\)

Partitions an input set into disjoint subsets by assigning a bin number to each row.



<a name="loio9a78dfb3cd8240f4be22495a098e65ea__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
BINNING( <binning_param> => <expression> [ {, <binning_parameter> => <expression> } ... ] ) <window_specification>

<binning_param> ::= VALUE | BIN_COUNT | BIN_WIDTH | TILE_COUNT | STDDEV_COUNT
```



<a name="loio9a78dfb3cd8240f4be22495a098e65ea__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<binning\_param\>*

</b></dt>
<dd>

VALUE is always required. It specifies the column that binning is applied to. When BIN\_WIDTH is used, the input column must have a numeric data type. BIN\_COUNT specifies the number of equal-width bins. BIN\_WIDTH specifies the width of the bins. TILE\_COUNT specifies the number of bins with equal number of records. STDDEV\_COUNT specifies the number of standard deviations left and right from the mean.

The appropriate binning method is selected based on the parameter specified – exactly one of the last four parameters must be non-NULL. The value assigned to binning method parameter must be an integer expression.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio9a78dfb3cd8240f4be22495a098e65ea__sql_function_abs_1sql_function_abs_description"/>

## Description

The OVER clause must not specify a *<window\_order\_by\_clause\>* nor any window frame since the binning function works on an entire partition.



<a name="loio9a78dfb3cd8240f4be22495a098e65ea__sql_function_abs_1sql_function_abs_examples"/>

## Examples

The following example distributes the value of the input set into four bins that all have an equal width.

```
DROP TABLE weather;
CREATE ROW TABLE weather (station INT, ts DATE, temperature FLOAT);
INSERT INTO weather VALUES(1, '2014-01-01', 0);
INSERT INTO weather VALUES(1, '2014-01-02', 3);
INSERT INTO weather VALUES(1, '2014-01-03', 4.5);
INSERT INTO weather VALUES(1, '2014-01-04', 6);
INSERT INTO weather VALUES(1, '2014-01-05', 6.3);
INSERT INTO weather VALUES(1, '2014-01-06', 5.9);
INSERT INTO weather VALUES(1, '2015-01-01', 1);
INSERT INTO weather VALUES(1, '2015-01-02', 3.4);
INSERT INTO weather VALUES(1, '2015-01-03', 5);
INSERT INTO weather VALUES(1, '2015-01-04', 6.7);
INSERT INTO weather VALUES(1, '2015-01-05', 4.6);
INSERT INTO weather VALUES(1, '2015-01-06', 6.9);

SELECT *, BINNING(VALUE => temperature, BIN_COUNT => 4) OVER () AS bin_num FROM weather;
```


<table>
<tr>
<th valign="top">

STATION

</th>
<th valign="top">

TS

</th>
<th valign="top">

TEMPERATURE

</th>
<th valign="top">

BIN\_NUM

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

01.01.2014

</td>
<td valign="top">

0.0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

02.01.2014

</td>
<td valign="top">

3.0

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

03.01.2014

</td>
<td valign="top">

4.5

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

04.01.2014

</td>
<td valign="top">

6.0

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

05.01.2014

</td>
<td valign="top">

6.3

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

06.01.2014

</td>
<td valign="top">

5.9

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

01.01.2014

</td>
<td valign="top">

1.0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

02.01.2014

</td>
<td valign="top">

3.4

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

03.01.2014

</td>
<td valign="top">

5.0

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

04.01.2014

</td>
<td valign="top">

6.7

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

05.01.2014

</td>
<td valign="top">

4.6

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

06.01.2014

</td>
<td valign="top">

6.9

</td>
<td valign="top">

4

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

