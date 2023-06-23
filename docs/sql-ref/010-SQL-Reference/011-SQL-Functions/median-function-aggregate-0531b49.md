<!-- loio0531b496ea0c463d8c9ddfc15cbdbf04 -->

# MEDIAN Function \(Aggregate\)

Finds the statistical median of an input expression with a numeric data type. This function can also be used as a window function.



## Syntax

**Aggregate function:**

```
MEDIAN( <expression> )
```

**Window function:**

```
MEDIAN( <expression> ) <window_specification>
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the input data expression for the MEDIAN function.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



## Description

The MEDIAN function finds the statistical median of an input expression with a numeric data type. Although it is grouped with the aggregate functions, its optional OVER clause positions it as a windows function as well.

Null values are eliminated. If there is an even number of elements, then the average of the two middle elements is returned. Otherwise, the middle element is returned.

The result type is the type that is selected for the expression "x/2" for an x value of the input data type.



## Examples

**Median of integer input** The following example returns a median value of ***2***.

```
CREATE TABLE T (class NVARCHAR(10), date DAYDATE, val INT);
INSERT INTO T VALUES('A', '01.01.1972', 1);
INSERT INTO T VALUES('A', '02.01.1972', 3);
INSERT INTO T VALUES('A', '03.01.1972', null);
INSERT INTO T VALUES('A', '04.01.1972', 2);

SELECT MEDIAN(val) "median value" FROM T;
```

If the number of non-null values is even, then the average of the two middle values is returned. For the following example, the average of 2 and 3 is returned. Since the input and output types are the same, the integer is rounded. The returned result is ***3***.

```
INSERT INTO T VALUES('A', '05.01.1972', 4);
SELECT MEDIAN(val) "median value" FROM T;
```

**Median of double input** The following example uses double values instead of integers. The returned result is ***2.5***.

```
CREATE TABLE T (TS_ID NVARCHAR(10), date DAYDATE, val DOUBLE);
INSERT INTO T VALUES('A', '01.01.1972', 1.0);
INSERT INTO T VALUES('A', '02.01.1972', 3.0);
INSERT INTO T VALUES('A', '03.01.1972', null);
INSERT INTO T VALUES('A', '04.01.1972', 2.0);
INSERT INTO T VALUES('A', '05.01.1972', 4.0);

SELECT MEDIAN(val) "median value" FROM T;
```

**Median as a window function** The following example uses double values instead of integers.

```
CREATE TABLE T (TS_ID NVARCHAR(10), date DAYDATE, val DOUBLE);
INSERT INTO T VALUES('A', '01.01.1972', 1.0);
INSERT INTO T VALUES('A', '02.01.1972', 3.0);
INSERT INTO T VALUES('A', '03.01.1972', null);
INSERT INTO T VALUES('A', '04.01.1972', 2.0);
INSERT INTO T VALUES('A', '04.01.1972', 4.0);

SELECT MEDIAN(val) OVER (PARTITION BY TS_ID ) AS WF1 FROM T;
```

The returned result is:


<table>
<tr>
<th valign="top">

WF1



</th>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
</table>

 **Median of sliding window \(GROUPS BETWEEN\)** Both of the SELECT statements in the following example produce identical results.

```
CREATE TABLE T (TS_ID NVARCHAR(10), date DAYDATE, val DOUBLE);
INSERT INTO T VALUES('A', '01.01.1972', 1.0);
INSERT INTO T VALUES('A', '02.01.1972', 3.0);
INSERT INTO T VALUES('A', '03.01.1972', null);
INSERT INTO T VALUES('A', '04.01.1972', 2.0);
INSERT INTO T VALUES('A', '04.01.1972', 4.0);

SELECT MEDIAN(val) OVER (PARTITION BY TS_ID ORDER BY date) AS WF2A FROM T;
SELECT MEDIAN(val) OVER (PARTITION BY TS_ID ORDER BY date GROUPS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS WF2B FROM T;
```

The returned result is:


<table>
<tr>
<th valign="top">

WF2B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
</table>

**Median of sliding window \(ROWS BETWEEN\)** The following example uses ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW.

```
CREATE TABLE T (TS_ID NVARCHAR(10), date DAYDATE, val DOUBLE);
INSERT INTO T VALUES('A', '01.01.1972', 1.0);
INSERT INTO T VALUES('A', '02.01.1972', 3.0);
INSERT INTO T VALUES('A', '03.01.1972', null);
INSERT INTO T VALUES('A', '04.01.1972', 2.0);
INSERT INTO T VALUES('A', '04.01.1972', 4.0);

SELECT MEDIAN(val) OVER (PARTITION BY TS_ID ORDER BY date ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS WF3 FROM T;
```

The returned result is:


<table>
<tr>
<th valign="top">

WF3



</th>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2.5



</td>
</tr>
</table>

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

