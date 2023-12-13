<!-- loio1a116cbd04a942e498ffef3a37b47461 -->

# DENSE\_RANK Function \(Window\)

Performs the same ranking operation as the RANK function, except that rank numbering does not skip when ties are found.



<a name="loio1a116cbd04a942e498ffef3a37b47461__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
DENSE_RANK() <window_specification>
```



<a name="loio1a116cbd04a942e498ffef3a37b47461__section_lnz_dcq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio1a116cbd04a942e498ffef3a37b47461__sql_function_abs_1sql_function_abs_description"/>

## Description

The DENSE\_RANK function performs the same ranking operation as the RANK function, except that rank numbering does not skip when ties are found.



<a name="loio1a116cbd04a942e498ffef3a37b47461__sql_function_abs_1sql_function_abs_examples"/>

## Examples

In this example, the RANK function returns the rank 5 for the row `('A', 10, 0)` because there were two rows that returned the rank of 3. However, DENSE\_RANK returns the rank 4 for the row `('A', 10, 0)`.

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
  ROW_NUMBER() OVER (PARTITION BY class ORDER BY val) AS row_num,
  RANK() OVER (PARTITION BY class ORDER BY val) AS rank,
  DENSE_RANK() OVER (PARTITION BY class ORDER BY val) AS dense_rank
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

ROW\_NUM

</th>
<th valign="top">

RANK

</th>
<th valign="top">

DENSE\_RANK

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
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

3

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
<td valign="top">

2

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

3

</td>
<td valign="top">

3

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

5

</td>
<td valign="top">

4

</td>
<td valign="top">

3

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

5

</td>
<td valign="top">

5

</td>
<td valign="top">

4

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

3

</td>
<td valign="top">

2

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

