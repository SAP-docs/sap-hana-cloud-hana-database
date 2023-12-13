<!-- loioee3c26a9f6354191800e6d0ba8485200 -->

# Window Aggregate Functions

Some aggregate functions can be used as window functions over a window specification.



## Syntax

```
<aggregate_function_or_expression_as_window_function> ::= 
 <aggregate_function_name> ( <arguments> ) <window_specification>

<aggregate_function_name> ::= 
 AVG
 | CORR 
 | CORR_SPEARMAN 
 | COUNT
 | FIRST_VALUE 
 | LAST_VALUE 
 | MAX 
 | MEDIAN 
 | MIN 
 | NTH_VALUE 
 | STDDEV 
 | SUM
 | VAR
```



<a name="loioee3c26a9f6354191800e6d0ba8485200__section_ch2_55n_gfb"/>

## Syntax Elements


<dl>
<dt><b>

*<aggregate\_function\_name\>*

</b></dt>
<dd>

Specifies the aggregate function or aggregate expression to use as a window function.



</dd><dt><b>

*<arguments\>*

</b></dt>
<dd>

Specifies the input to the function. Refer to the individual function topic for the definition of *<arguments\>*.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Specifies the window definition. See [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md)



</dd>
</dl>



<a name="loioee3c26a9f6354191800e6d0ba8485200__section_fz2_n1l_d1b"/>

## Description

Window aggregate functions are aggregate functions that can be used as window functions.



<a name="loioee3c26a9f6354191800e6d0ba8485200__section_pcx_k1l_d1b"/>

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
  COUNT(*) OVER (PARTITION BY class) AS c1,
  COUNT(offset) OVER (PARTITION BY class) AS c2,
  COUNT(*) OVER (PARTITION BY class ORDER BY val) AS c3,
  COUNT(offset) OVER (PARTITION BY class ORDER BY val) AS c4,
  MAX(val) OVER (PARTITION BY class) AS m1,
  MAX(val) OVER (PARTITION BY class ORDER BY val) AS m2
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

C1

</th>
<th valign="top">

C2

</th>
<th valign="top">

C3

</th>
<th valign="top">

C4

</th>
<th valign="top">

M1

</th>
<th valign="top">

M2

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

4

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

10

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

3

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
<td valign="top">

10

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

null

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

4

</td>
<td valign="top">

3

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

A

</td>
<td valign="top">

5

</td>
<td valign="top">

2

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

4

</td>
<td valign="top">

3

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

A

</td>
<td valign="top">

10

</td>
<td valign="top">

0

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

5

</td>
<td valign="top">

4

</td>
<td valign="top">

10

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

3

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

7

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

1

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
<td valign="top">

2

</td>
<td valign="top">

7

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

3

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
<td valign="top">

7

</td>
<td valign="top">

7

</td>
</tr>
</table>

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[AVG Function \(Aggregate\)](avg-function-aggregate-2c93334.md "Returns the arithmetical mean of the expression. This function can also be used as a window function.")

[CORR Function \(Aggregate\)](corr-function-aggregate-aa049c2.md "Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.")

[CORR\_SPEARMAN Function \(Aggregate\)](corr-spearman-function-aggregate-0579a65.md "Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.")

[COUNT Function \(Aggregate\)](count-function-aggregate-28c3b57.md "Counts the number of rows returned by a query. This function can also be used as a window function.")

[FIRST\_VALUE Function \(Aggregate\)](first-value-function-aggregate-034b175.md "Returns the value of the first element of an expression. This function can also be used as a window function.")

[LAST\_VALUE Function \(Aggregate\)](last-value-function-aggregate-32e95b7.md "Returns the value of the last element of an expression. This function can also be used as a window function.")

[MAX Function \(Aggregate\)](max-function-aggregate-6929090.md "Returns the maximum value of the expression. This function can also be used as a window function.")

[MEDIAN Function \(Aggregate\)](median-function-aggregate-0531b49.md "Finds the statistical median of an input expression with a numeric data type. This function can also be used as a window function.")

[MIN Function \(Aggregate\)](min-function-aggregate-4409b0c.md "Returns the minimum value of the expression. This function can also be used as a window function.")

[NTH\_VALUE Function \(Aggregate\)](nth-value-function-aggregate-6522df9.md "Returns the value of an element at a specific position in an expression. This function can also be used as a window function.")

[STDDEV Function \(Aggregate\)](stddev-function-aggregate-c0c42b5.md "Returns the standard deviation of the given expression as the square root of the VAR function. This function can also be used as a window function.")

[SUM Function \(Aggregate\)](sum-function-aggregate-03958a1.md "Returns the sum of the expression. This function can also be used as a window function.")

[VAR Function \(Aggregate\)](var-function-aggregate-21a8eb1.md "Returns the variance of the given expression as the square of the standard deviation. This function can also be used as a window function.")

