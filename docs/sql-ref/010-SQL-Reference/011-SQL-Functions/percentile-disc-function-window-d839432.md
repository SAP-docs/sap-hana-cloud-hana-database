<!-- loiod8394326f65e4fd9aa5a9750755b4665 -->

# PERCENTILE\_DISC Function \(Window\)

Returns the first value whose cumulative distribution value is greater than or equal to the percentile value of a constant.



<a name="loiod8394326f65e4fd9aa5a9750755b4665__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
PERCENTILE_DISC( <constant_literal> ) WITHIN GROUP ( ORDER BY <expression> [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] ) <window_specification>
```



<a name="loiod8394326f65e4fd9aa5a9750755b4665__section_fsc_rcq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loiod8394326f65e4fd9aa5a9750755b4665__section_qbk_wg4_sfb"/>

## Description

Returns the first value whose cumulative distribution value is greater than or equal to the percentile value of *<constant\_literal\>*.

A discrete distribution of the values of *<expression\>* is assumed. Only a single *<expression\>* can be specified in ORDER BY clause; this expression must evaluate to a numeric type. The *<constant\_literal\>* should be a numeric value between, and including, 0 to 1, because it is a percentile value. The return value is always in the set of values of *<expression\>*.



<a name="loiod8394326f65e4fd9aa5a9750755b4665__section_n41_jbl_d1b"/>

## Examples

```
CREATE TABLE p_disc (class NVARCHAR(10), val INT, offset INT);
 INSERT INTO p_disc VALUES('A', 1, 1);
 INSERT INTO p_disc VALUES('A', 3, 3);
 INSERT INTO p_disc VALUES('A', 5, null);
 INSERT INTO p_disc VALUES('A', 5, 2);
 INSERT INTO p_disc VALUES('A', 10, 0);
 INSERT INTO p_disc VALUES('B', 1, 3);
 INSERT INTO p_disc VALUES('B', 1, 1);
 INSERT INTO p_disc VALUES('B', 7, 1);
```

```
SELECT class, 
 val, 
 PERCENTILE_DISC(0.125) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pd1, 
 PERCENTILE_DISC(0.5) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pd2, 
 PERCENTILE_DISC(0.875) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pd3
FROM p_disc;
```


<table>
<tr>
<th valign="top">

CLASS



</th>
<th valign="top">

VAL



</th>
<th valign="top">

PD1



</th>
<th valign="top">

PD2



</th>
<th valign="top">

PD3



</th>
</tr>
<tr>
<td valign="top">

A



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

5



</td>
<td valign="top">

10



</td>
</tr>
<tr>
<td valign="top">

A



</td>
<td valign="top">

3



</td>
<td valign="top">

1



</td>
<td valign="top">

5



</td>
<td valign="top">

10



</td>
</tr>
<tr>
<td valign="top">

A



</td>
<td valign="top">

5



</td>
<td valign="top">

1



</td>
<td valign="top">

5



</td>
<td valign="top">

10



</td>
</tr>
<tr>
<td valign="top">

A



</td>
<td valign="top">

5



</td>
<td valign="top">

1



</td>
<td valign="top">

5



</td>
<td valign="top">

10



</td>
</tr>
<tr>
<td valign="top">

A



</td>
<td valign="top">

10



</td>
<td valign="top">

1



</td>
<td valign="top">

5



</td>
<td valign="top">

10



</td>
</tr>
<tr>
<td valign="top">

B



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

7



</td>
</tr>
<tr>
<td valign="top">

B



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

7



</td>
</tr>
<tr>
<td valign="top">

B



</td>
<td valign="top">

7



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
<td valign="top">

7



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[PERCENTILE\_CONT Function \(Window\)](percentile-cont-function-window-3028c19.md "Returns an interpolated value using the percentile value of a constant.")

