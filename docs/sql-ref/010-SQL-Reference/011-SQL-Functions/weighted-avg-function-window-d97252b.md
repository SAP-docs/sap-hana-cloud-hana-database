<!-- loiod97252bcd22f4d9fa4812715cee5139b -->

# WEIGHTED\_AVG Function \(Window\)

Computes a weighted moving average by using arithmetically decreasing weights.



<a name="loiod97252bcd22f4d9fa4812715cee5139b__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
WEIGHTED_AVG(<expression>) <window_specification>
```



<a name="loiod97252bcd22f4d9fa4812715cee5139b__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

*<expression\>* indicates a numeric column that is used in the weighted moving average calculation.

In a window frame where *<n\>* represents the actual number of elements \(ROWS or GROUPS\) in the window frame, and *<i\>* represents the element number in the series, the weight factors are calculated with the following algorithm:

```
weight(<i>) = 2 * (<n> + 1 - <i>) / (<n> * (<n> + 1))
```

The weight factors are applied in reverse order so that in a window frame with n rows, the first weight factor is multiplied with the value of row n, the second weight factor with the value of row n-1, and so on. When using WEIGHTED\_AVG with the GROUPS unit, the values within a group are first arithmetically averaged before they are multiplied with the corresponding weight factor.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loiod97252bcd22f4d9fa4812715cee5139b__sql_function_abs_1sql_function_abs_description"/>

## Description

Computes a weighted moving average by using arithmetically decreasing weights.



<a name="loiod97252bcd22f4d9fa4812715cee5139b__sql_function_abs_1sql_function_abs_examples"/>

## Examples

```
CREATE TABLE weather (station INT, ts DAYDATE, temperature FLOAT);
INSERT INTO weather VALUES(1, '2014-01-01', 0.0);
INSERT INTO weather VALUES(1, '2014-01-02', 3.0);
INSERT INTO weather VALUES(1, '2014-01-03', 4.5);
INSERT INTO weather VALUES(1, '2014-01-04', 6.0);
INSERT INTO weather VALUES(1, '2014-01-05', 6.3);
INSERT INTO weather VALUES(1, '2014-01-06', 5.9);
INSERT INTO weather VALUES(2, '2014-01-01', 1.0);
INSERT INTO weather VALUES(2, '2014-01-02', 3.4);
INSERT INTO weather VALUES(2, '2014-01-03', 5.0);
INSERT INTO weather VALUES(2, '2014-01-04', 6.7);
INSERT INTO weather VALUES(2, '2014-01-05', 4.6);
INSERT INTO weather VALUES(2, '2014-01-06', 6.9);

SELECT ts, temperature, WEIGHTED_AVG(temperature) OVER (ORDER BY ts ROWS BETWEEN 1 PRECEDING AND CURRENT ROW) FROM weather ORDER BY ts;
```


<table>
<tr>
<th valign="top">

ts

</th>
<th valign="top">

TEMPERATURE

</th>
<th valign="top">

WEIGHTED\_AVG\(temperature\) OVER \(ORDER BY ts ROWS BETWEEN 1 PRECEDING AND CURRENT ROW\) FROM weather ORDER BY ts

</th>
</tr>
<tr>
<td valign="top">

01.01.2014

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

01.01.2014

</td>
<td valign="top">

1

</td>
<td valign="top">

0.6666666666666666

</td>
</tr>
<tr>
<td valign="top">

02.01.2014

</td>
<td valign="top">

3

</td>
<td valign="top">

2.3333333333333335

</td>
</tr>
<tr>
<td valign="top">

02.01.2014

</td>
<td valign="top">

3.4

</td>
<td valign="top">

3.2666666666666666

</td>
</tr>
<tr>
<td valign="top">

03.01.2014

</td>
<td valign="top">

4.5

</td>
<td valign="top">

4.133333333333333

</td>
</tr>
<tr>
<td valign="top">

03.01.2014

</td>
<td valign="top">

5

</td>
<td valign="top">

4.833333333333333

</td>
</tr>
<tr>
<td valign="top">

04.01.2014

</td>
<td valign="top">

6

</td>
<td valign="top">

5.666666666666666

</td>
</tr>
<tr>
<td valign="top">

04.01.2014

</td>
<td valign="top">

6.7

</td>
<td valign="top">

6.466666666666667

</td>
</tr>
<tr>
<td valign="top">

05.01.2014

</td>
<td valign="top">

6.3

</td>
<td valign="top">

6.433333333333333

</td>
</tr>
<tr>
<td valign="top">

05.01.2014

</td>
<td valign="top">

4.6

</td>
<td valign="top">

5.166666666666666

</td>
</tr>
<tr>
<td valign="top">

06.01.2014

</td>
<td valign="top">

5.9

</td>
<td valign="top">

5.466666666666667

</td>
</tr>
<tr>
<td valign="top">

06.01.2014

</td>
<td valign="top">

6.9

</td>
<td valign="top">

6.566666666666666

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

