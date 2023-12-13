<!-- loio886723669fb34ff8b5c51eabc003cbd2 -->

# NTILE Function \(Window\)

Distributes rows into a specified number of buckets and assigns the bucket number starting from 1 to each row in the bucket.



<a name="loio886723669fb34ff8b5c51eabc003cbd2__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
NTILE( <number_of_buckets> ) <window_specification>
```



<a name="loio886723669fb34ff8b5c51eabc003cbd2__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<number\_of\_buckets\>*

</b></dt>
<dd>

Specifies the number of buckets to distribute rows to.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio886723669fb34ff8b5c51eabc003cbd2__sql_function_abs_1sql_function_abs_description"/>

## Description

The output of NTILE function can be non-deterministic among tie values.



<a name="loio886723669fb34ff8b5c51eabc003cbd2__sql_function_abs_1sql_function_abs_examples"/>

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

SELECT class, val,
  NTILE(3) OVER (PARTITION BY class ORDER BY val) AS NTILE,
  FIRST_VALUE(val) OVER (PARTITION BY class ORDER BY val) AS first,
  LAST_VALUE(val) OVER (PARTITION BY class ORDER BY val) AS last,
  NTH_VALUE(val, 4) OVER (PARTITION BY class ORDER BY val) AS nth
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

NTILE

</th>
<th valign="top">

FIRST

</th>
<th valign="top">

LAST

</th>
<th valign="top">

NTH

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

1

</td>
<td valign="top">

1

</td>
<td valign="top">

null

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

1

</td>
<td valign="top">

3

</td>
<td valign="top">

null

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

1

</td>
<td valign="top">

5

</td>
<td valign="top">

5

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

1

</td>
<td valign="top">

5

</td>
<td valign="top">

5

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

3

</td>
<td valign="top">

1

</td>
<td valign="top">

10

</td>
<td valign="top">

5

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

1

</td>
<td valign="top">

null

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

2

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

null

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

3

</td>
<td valign="top">

1

</td>
<td valign="top">

7

</td>
<td valign="top">

null

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

