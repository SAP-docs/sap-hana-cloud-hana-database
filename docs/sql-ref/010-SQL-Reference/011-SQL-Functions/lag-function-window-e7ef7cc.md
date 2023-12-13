<!-- loioe7ef7cc478f14a408e1af27fc1a78624 -->

# LAG Function \(Window\)

Returns the value of the offset rows before the current row.



<a name="loioe7ef7cc478f14a408e1af27fc1a78624__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
LAG( <expression> [, <offset> [, <default_expr> ] ] ) <window_specification>
```



<a name="loioe7ef7cc478f14a408e1af27fc1a78624__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<offset\>*

</b></dt>
<dd>

The *<offset\>* should be non-negative and the default is 1.

If the *<offset\>* crosses boundaries of the partition, then *<default\_expr\>* value is returned. If the *<default\_expr\>* is not specified, then a null value is returned. The *<offset\>* and *<default\_expr\>* are evaluated at current row.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loioe7ef7cc478f14a408e1af27fc1a78624__sql_function_abs_1sql_function_abs_description"/>

## Description

The output of the LAG function can be non-deterministic among tie values.



<a name="loioe7ef7cc478f14a408e1af27fc1a78624__sql_function_abs_1sql_function_abs_examples"/>

## Examples

```
CREATE TABLE T (class NVARCHAR(10), val INT, offset INT);
 INSERT INTO T VALUES('A', 1, 1);
 INSERT INTO T VALUES('A', 3, 3);
 INSERT INTO T VALUES('A', 5, null);
 INSERT INTO T VALUES('A', 5, 2);
 INSERT INTO T VALUES('A', 10, 0);
 INSERT INTO T VALUES('B', 1, 3);
 INSERT INTO T VALUES('B', 1, 1);
 INSERT INTO T VALUES('B', 7, 1);

SELECT class, 
  val, 
  offset,
  LEAD(val) OVER (PARTITION BY class ORDER BY val) AS lead,
  LEAD(val,offset,-val) OVER (PARTITION BY class ORDER BY val) AS lead2,
  LAG(val) OVER (PARTITION BY class ORDER BY val) AS lag,
  LAG(val,offset,-val) OVER (PARTITION BY class ORDER BY val) AS lag2
 FROM T;
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

OFFSET

</th>
<th valign="top">

LEAD

</th>
<th valign="top">

LEAD2

</th>
<th valign="top">

LAG

</th>
<th valign="top">

LAG2

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

3

</td>
<td valign="top">

3

</td>
<td valign="top">

null

</td>
<td valign="top">

\-1

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

3

</td>
<td valign="top">

5

</td>
<td valign="top">

10

</td>
<td valign="top">

1

</td>
<td valign="top">

\-3

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

null

</td>
<td valign="top">

5

</td>
<td valign="top">

\-5

</td>
<td valign="top">

3

</td>
<td valign="top">

\-5

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

2

</td>
<td valign="top">

10

</td>
<td valign="top">

\-5

</td>
<td valign="top">

5

</td>
<td valign="top">

3

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

0

</td>
<td valign="top">

null

</td>
<td valign="top">

10

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

3

</td>
<td valign="top">

1

</td>
<td valign="top">

\-1

</td>
<td valign="top">

null

</td>
<td valign="top">

\-1

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

7

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

null

</td>
<td valign="top">

\-7

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

