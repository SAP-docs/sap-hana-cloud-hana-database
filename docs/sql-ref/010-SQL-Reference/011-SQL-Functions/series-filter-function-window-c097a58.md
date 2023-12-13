<!-- loioc097a58f3a7c4a3a8d851371bcc8e5ba -->

# SERIES\_FILTER Function \(Window\)

Performs a filtered calculation on a series of data.



<a name="loioc097a58f3a7c4a3a8d851371bcc8e5ba__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
SERIES_FILTER(<filter_parameter> => <expression> [, <filter_parameter> => <expression> ... ])
 OVER (
   [ <series_definition> | <series_reference> ]
   [ <window_partition_by_clause> ]
   [ ORDER BY <window_order_by_expression> ]
   [ <window_frame_clause> ]
      )
```



<a name="loioc097a58f3a7c4a3a8d851371bcc8e5ba__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<filter\_parameter\>*

</b></dt>
<dd>

```
<filter_parameter> ::= VALUE | METHOD_NAME | ALPHA | BETA
```

VALUE is a required parameter that specifies the column to which the filter is applied. The column must represent numeric data. NULL values are not permitted.

METHOD\_NAME is a required parameter that specifies the name of the filter method. Specify SINGLESMOOTH for single exponential smoothing or DOUBLESMOOTH for double exponential smoothing.

ALPHA is an optional smoothing decimal parameter for the level of the series that ranges between 0 and 1. The default value is 0.1.

BETA is a smoothing decimal parameter for the trend of the series that ranges between 0 and 1. The default value is 0.1. This parameter is only required for double exponential smoothing.

SERIES\_FILTER implements several filtering algorithms that are identified by METHOD\_NAME. Trailing NULL values in the input series are replaced by forecasted values.

All filter algorithms require that the series is equidistant and it must not contain any missing values. The function returns an error when it is called with a series property indicating a property that does not match.



</dd><dt><b>

*<window\_partition\_by\_clause\>*

</b></dt>
<dd>

Specifies one or more partitions to be created using the supplied expressions.

```
<window_partition_by_clause> ::= PARTITION BY <expression> [ { , <expression> } ... ]
```



</dd><dt><b>

*<window\_order\_by\_expression\>*

</b></dt>
<dd>

Determines the order of the input. Only one expression must be supplied in the *<window\_order\_by\_expression\>* for this function.

This expression must not contain any null values or duplicates. See the description of the *<window\_order\_by\_clause\>* clause in the *Window Functions* topic for other syntax information for this clause.



</dd><dt><b>

*<window\_frame\_clause\>*

</b></dt>
<dd>

Physically limits the rows within a partition by specifying a number of rows preceding or following the current row.

```
<window_frame_clause> ::= <window_frame_unit> <window_frame_extent>

<window_frame_unit> ::= ROWS
<window_frame_extent> ::= <window_frame_start> | <window_frame_between>
<window_frame_start> ::= UNBOUNDED PRECEDING | <window_frame_preceding> | CURRENT ROW
<window_frame_preceding> ::= <unsigned_integer> PRECEDING
<window_frame_between> ::= BETWEEN <lower_window_frame_bound> AND <upper_window_frame_bound>
<lower_window_frame_bound> ::= <window_frame_bound>
<upper_window_frame_bound> ::= <window_frame_bound>
<window_frame_bound> := <window_frame_start> | UNBOUNDED FOLLOWING | <window_frame_following>
<window_frame_following> ::= <unsigned_integer> FOLLOWING
```

ROWS requires a ORDER BY clause to be specified.

UNBOUND PRECEDING specifies that the window starts at the first row of the partition. It can only be specified as *<window\_frame\_start\>*. CURRENT ROW specifies that the window starts or ends at the current row when used with ROWS.

PRECEDING indicates that the number of rows or values to precede the current row. *<unsigned\_integer\>* should be 0 or a positive integer literal.

*<lower\_window\_frame\_bound\>* and *<upper\_window\_frame\_bound\>* specify the lower \(starting\) bound and the upper \(ending\) bound of the window frame. The upper bound cannot be smaller than the lower bound.

UNBOUNDED FOLLOWING specifies that the window ends at the last row of the partition. UNBOUNDED FOLLOWING can only be specified as a window frame end.

FOLLOWING indicates the number of rows or values to follow the current row. When specified as the window frame start, the window frame end should be *<unsigned\_integer\>* FOLLOWING. The *<unsigned\_integer\>* should be 0 or a positive integer literal.



</dd>
</dl>



<a name="loioc097a58f3a7c4a3a8d851371bcc8e5ba__sql_function_abs_1sql_function_abs_description"/>

## Description

The window functions allow you to divide the result sets of a query, or a logical partition of a query, into groups of rows called window partitions.

A window partition is specified by one or more expressions in the OVER clause.

Window functions other than ROW\_NUMBER, PERCENTILE\_DISC, PERCENTILE\_CONT and the window aggregate functions must have an ORDER BY clause in the OVER clause.

Result sets are first partitioned as specified by the PARTITION BY clause, and then sorted by ORDER BY clause specification within the window partition. Then, window functions are applied to each row within window partition boundaries.

The ORDER BY clause in the OVER clause only evaluates the window function so that the order of resulting rows is non-deterministic if not specified by ORDER BY for SELECT.

The default window frame of the window function depends on whether a window ORDER BY clause is specified. If a window ORDER BY clause is specified, then the default window frame becomes 'between UNBOUNDED PRECEDING and CURRENT ROW': The window function computes on rows preceding or peer with the current row. As a result, the function returns cumulative values.

If a window ORDER BY clause is not specified, then the default window frame becomes 'between UNBOUNDED PRECEDING and UNBOUNDED FOLLOWING': The window function computes on the whole window partition. As a result, the function returns the same value within a window partition regardless of current row.



<a name="loioc097a58f3a7c4a3a8d851371bcc8e5ba__sql_function_abs_1sql_function_abs_examples"/>

## Examples

The following example illustrates single and double exponential smoothing with forecasting.

```
DROP TABLE weather;
CREATE COLUMN TABLE weather (ts DAYDATE, temperature FLOAT);
INSERT INTO weather VALUES('2014-01-01', 0);
INSERT INTO weather VALUES('2014-01-02', 3);
INSERT INTO weather VALUES('2014-01-03', 4.5);
INSERT INTO weather VALUES('2014-01-04', 6);
INSERT INTO weather VALUES('2014-01-05', 6.3);
INSERT INTO weather VALUES('2014-01-06', 6.9);
INSERT INTO weather VALUES('2014-01-07', NULL);
INSERT INTO weather VALUES('2014-01-08', NULL);

SELECT ts, temperature, 
       SERIES_FILTER(VALUE => temperature, METHOD_NAME => 'SINGLESMOOTH', ALPHA => 0.2) OVER (ORDER BY ts) AS SES,
       SERIES_FILTER(VALUE => temperature, METHOD_NAME => 'DOUBLESMOOTH', ALPHA => 0.2, BETA => 0.3) OVER (ORDER BY ts) AS DES
FROM weather;
```


<table>
<tr>
<th valign="top">

TS

</th>
<th valign="top">

TEMPERATURE

</th>
<th valign="top">

SES

</th>
<th valign="top">

DES

</th>
</tr>
<tr>
<td valign="top">

01.01.2014

</td>
<td valign="top">

0.0

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
</tr>
<tr>
<td valign="top">

02.01.2014

</td>
<td valign="top">

3.0

</td>
<td valign="top">

0

</td>
<td valign="top">

3

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

0.6000000000000001

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

04.01.2014

</td>
<td valign="top">

6.0

</td>
<td valign="top">

1.3800000000000001

</td>
<td valign="top">

8.61

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

2.3040000000000003

</td>
<td valign="top">

10.8414

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

3.1032

</td>
<td valign="top">

12.414036

</td>
</tr>
<tr>
<td valign="top">

07.01.2014

</td>
<td valign="top">

NULL

</td>
<td valign="top">

3.86256

</td>
<td valign="top">

13.46130264

</td>
</tr>
<tr>
<td valign="top">

08.01.2014

</td>
<td valign="top">

NULL

</td>
<td valign="top">

3.86256

</td>
<td valign="top">

15.61137648

</td>
</tr>
</table>

The following example uses a window frame ROWS specification:

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
```

```
SELECT class, 
  val, 
  SUM(val) OVER(PARTITION BY class ORDER BY val) AS s0, 
  SUM(val) OVER(PARTITION BY class ORDER BY val ROWS BETWEENn UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING) AS s1, 
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) AS s2, 
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN UNBOUNDED PRECEDING AND 1 PRECEDING) AS s3, 
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN UNBOUNDED PRECEDING AND 1 FOLLOWING) AS s4
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN CURRENT ROW AND UNBOUNDED FOLLOWING) AS s5, 
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN CURRENT ROW AND CURRENT ROW) AS s6, 
  SUM(val) OVER (PARTITION BY class ORDER BY val ROWS BETWEEN CURRENT ROW AND 1 FOLLOWING) AS s7
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

S0

</th>
<th valign="top">

S1

</th>
<th valign="top">

S2

</th>
<th valign="top">

S3

</th>
<th valign="top">

S4

</th>
<th valign="top">

S5

</th>
<th valign="top">

S6

</th>
<th valign="top">

S7

</th>
<th valign="top">

S8

</th>
<th valign="top">

S9

</th>
<th valign="top">

S10

</th>
<th valign="top">

S11

</th>
<th valign="top">

S12

</th>
<th valign="top">

S13

</th>
<th valign="top">

S14

</th>
<th valign="top">

S15

</th>
<th valign="top">

S16

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

24

</td>
<td valign="top">

1

</td>
<td valign="top">

null

</td>
<td valign="top">

4

</td>
<td valign="top">

24

</td>
<td valign="top">

1

</td>
<td valign="top">

4

</td>
<td valign="top">

24

</td>
<td valign="top">

1

</td>
<td valign="top">

null

</td>
<td valign="top">

4

</td>
<td valign="top">

23

</td>
<td valign="top">

8

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

4

</td>
<td valign="top">

24

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
<td valign="top">

9

</td>
<td valign="top">

23

</td>
<td valign="top">

3

</td>
<td valign="top">

8

</td>
<td valign="top">

24

</td>
<td valign="top">

4

</td>
<td valign="top">

1

</td>
<td valign="top">

9

</td>
<td valign="top">

20

</td>
<td valign="top">

10

</td>
<td valign="top">

4

</td>
<td valign="top">

3

</td>
<td valign="top">

4

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

14

</td>
<td valign="top">

24

</td>
<td valign="top">

9

</td>
<td valign="top">

4

</td>
<td valign="top">

14

</td>
<td valign="top">

20

</td>
<td valign="top">

5

</td>
<td valign="top">

10

</td>
<td valign="top">

23

</td>
<td valign="top">

8

</td>
<td valign="top">

4

</td>
<td valign="top">

13

</td>
<td valign="top">

15

</td>
<td valign="top">

15

</td>
<td valign="top">

9

</td>
<td valign="top">

5

</td>
<td valign="top">

8

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

14

</td>
<td valign="top">

24

</td>
<td valign="top">

14

</td>
<td valign="top">

9

</td>
<td valign="top">

24

</td>
<td valign="top">

15

</td>
<td valign="top">

5

</td>
<td valign="top">

15

</td>
<td valign="top">

20

</td>
<td valign="top">

10

</td>
<td valign="top">

8

</td>
<td valign="top">

20

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
<td valign="top">

14

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

24

</td>
<td valign="top">

24

</td>
<td valign="top">

24

</td>
<td valign="top">

14

</td>
<td valign="top">

24

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
<td valign="top">

15

</td>
<td valign="top">

15

</td>
<td valign="top">

10

</td>
<td valign="top">

15

</td>
<td valign="top">

null

</td>
<td valign="top">

null

</td>
<td valign="top">

24

</td>
<td valign="top">

10

</td>
<td valign="top">

15

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

9

</td>
<td valign="top">

1

</td>
<td valign="top">

null

</td>
<td valign="top">

2

</td>
<td valign="top">

9

</td>
<td valign="top">

1

</td>
<td valign="top">

2

</td>
<td valign="top">

9

</td>
<td valign="top">

1

</td>
<td valign="top">

null

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
<td valign="top">

8

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

9

</td>
<td valign="top">

9

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

9

</td>
<td valign="top">

8

</td>
<td valign="top">

1

</td>
<td valign="top">

8

</td>
<td valign="top">

9

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

9

</td>
<td valign="top">

7

</td>
<td valign="top">

7

</td>
<td valign="top">

2

</td>
<td valign="top">

1

</td>
<td valign="top">

2

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

9

</td>
<td valign="top">

9

</td>
<td valign="top">

9

</td>
<td valign="top">

2

</td>
<td valign="top">

9

</td>
<td valign="top">

7

</td>
<td valign="top">

7

</td>
<td valign="top">

7

</td>
<td valign="top">

8

</td>
<td valign="top">

8

</td>
<td valign="top">

2

</td>
<td valign="top">

8

</td>
<td valign="top">

null

</td>
<td valign="top">

null

</td>
<td valign="top">

9

</td>
<td valign="top">

7

</td>
<td valign="top">

8

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

