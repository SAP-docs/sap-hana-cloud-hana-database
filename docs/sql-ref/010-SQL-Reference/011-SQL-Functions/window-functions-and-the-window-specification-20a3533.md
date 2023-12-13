<!-- loio20a353327519101495dfd0a87060a0d3 -->

# Window Functions and the Window Specification

Window functions allow you to perform analytic operations over a set of input rows.



<a name="loio20a353327519101495dfd0a87060a0d3___esql_functions_window_1sql_functions_window_syntax"/>

## Syntax

```
<function_name> <window_specification>
 
<window_specification> ::= OVER ( { [ <window_partition_by_clause> ] [ <window_order_by_clause> ] [ <window_frame_clause> ] } )
```



<a name="loio20a353327519101495dfd0a87060a0d3___esql_functions_window_1sql_functions_window_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<function\_name\>*

</b></dt>
<dd>

Specifies the window function to operate over the data. See the individual function topics for more information on their syntax.

```
<function_name> ::= 
 BINNING 
 | CUBIC_SPLINE_APPROX 
 | CUME_DIST   
 | DENSE_RANK
 | LAG 
 | LEAD 
 | LINEAR_APPROX 
 | NTILE  
 | PERCENT_RANK 
 | PERCENTILE_CONT
 | PERCENTILE_DISC
 | RANDOM_PARTITION
 | RANK               
 | ROW_NUMBER
 | SERIES_FILTER                              
 | WEIGHTED_AVG
 | <window_aggregate_functions>
 | <spatial_functions>
```

For *<window\_aggregate\_functions\>*, see [Window Aggregate Functions](window-aggregate-functions-ee3c26a.md).

For *<spatial\_functions\>*, see the *SAP HANA Cloud, SAP HANA Database Spatial Reference* guide.



</dd><dt><b>

*<window\_partition\_by\_clause\>*

</b></dt>
<dd>

```
<window_partition_by_clause> ::= PARTITION BY <expression> [ { , <expression> } ... ]
```

Creates one or more window partitions using the supplied expressions.



</dd><dt><b>

*<window\_order\_by\_clause\>*

</b></dt>
<dd>

Defines the sort order of the window.

```
<window_order_by_clause> ::= ORDER BY <window_order_by_expression> [ {, <window_order_by_expression> }  ... ]

<window_order_by_expression> ::= 
 <column> [ <collate_clause> ] [ ASC | DESC ] [ NULLS { FIRST | LAST } ] 

<collate_clause> ::= COLLATE <collation_name>
```


<dl>
<dt><b>

*<collate\_clause\>*

</b></dt>
<dd>

Specifies the collation to use. *<collate\_clause\>* can only be used on columns defined as NVARCHAR \(or VARCHAR, which is an alias for NVARCHAR\).

*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd><dt><b>

\[ ASC | DESC \]

</b></dt>
<dd>

ASC sorts records in ascending order and DESC sorts records in descending order. The default is ASC.



</dd><dt><b>

\[ NULLS FIRST | NULLS LAST \]

</b></dt>
<dd>

Specifies the ordering of NULL values.



</dd><dt><b>

*<position\>*

</b></dt>
<dd>

*<position\>* uses the entries in the select list to define the ordering required. For example:

```
SELECT col1, col2 FROM t ORDER BY 2;
```

ORDER BY 2 indicates that ordering should be undertaken using the second expression in the select list, which in this case is col2.



</dd>
</dl>



</dd><dt><b>

*<window\_frame\_clause\>*

</b></dt>
<dd>

Defines the rows \(bounds\) of a window partition by specifying the number of rows preceding or following with respect to the current row. If you specify a *<window\_frame\_clause\>*, you must also specify a *<window\_order\_by\_clause\>*.

```
<window_frame_clause> ::= <window_frame_unit> <window_frame_extent>

<window_frame_extent> ::= { <window_frame_start> | <window_frame_between> }
<window_frame_unit> ::= ROWS
<window_frame_start> ::= { UNBOUNDED PRECEDING | <window_frame_preceding> | CURRENT ROW }
<window_frame_preceding> ::= <unsigned_integer> PRECEDING

<window_frame_between> ::= BETWEEN <lower_window_frame_bound> AND <upper_window_frame_bound>
<lower_window_frame_bound> ::= <window_frame_bound>
<upper_window_frame_bound> ::= <window_frame_bound>
<window_frame_bound> := { <window_frame_start> | UNBOUNDED FOLLOWING | <window_frame_following> }
<window_frame_following> ::= <unsigned_integer> FOLLOWING
```

*<window\_frame\_between\>* specifies the lower \(starting\) bound and the upper \(ending\) bound of the window frame. The upper bound cannot be smaller than the lower bound.

UNBOUND PRECEDING specifies that the window starts at the first row of the partition. It can only be specified as *<window\_frame\_start\>*. CURRENT ROW specifies that the window starts or ends at the current row when used with ROWS.

PRECEDING indicates that the number of rows or values to precede the current row. *<unsigned\_integer\>* should be 0 or a positive integer literal.

UNBOUNDED FOLLOWING specifies that the window ends at the last row of the partition. UNBOUNDED FOLLOWING can only be specified as a window frame end.

FOLLOWING indicates the number of rows or values to follow the current row. When specified as the window frame start, the window frame end should be *<unsigned\_integer\>* FOLLOWING. The *<unsigned\_integer\>* should be 0 or a positive integer literal.



</dd>
</dl>



<a name="loio20a353327519101495dfd0a87060a0d3___esql_functions_window_1sql_functions_window_description"/>

## Description

The window functions allow you to divide the result sets of a query, or a logical partition of a query, into groups of rows called window partitions.

A window partition is specified by one or more expressions in the OVER clause.

Window functions not in the following list must have an ORDER BY clause in the OVER clause:

-   AVG
-   CORR
-   CORR\_SPEARMAN
-   COUNT
-   MAX
-   MEDIAN
-   MIN
-   PERCENTILE\_CONT
-   PERCENTILE\_DISC
-   ROW\_NUMBER
-   STDDEV
-   SUM
-   VAR

Result sets are first partitioned as specified by PARTITION BY clause, and then sorted by ORDER BY clause specification within the window partition.

Finally window functions are applied to each row within window partition boundaries.

The ORDER BY clause in the OVER clause is only used to evaluate window function so that the order of resulting rows is non-deterministic if not specified by ORDER BY for SELECT.

The default window frame of the window function depends on whether or not a window ORDER BY clause is specified. If a window ORDER BY clause is specified, the default window frame becomes 'between UNBOUNDED PRECEDING and CURRENT ROW'. That is to say that the window function computes on rows preceding or peer with current row. As a result, the function returns cumulative values.

If a window ORDER BY clause is not specified, the default window frame becomes 'between UNBOUNDED PRECEDING and UNBOUNDED FOLLOWING'. That is to say that the window function computes on the whole window partition. As a result, the function returns the same value within a window partition regardless of current row.



<a name="loio20a353327519101495dfd0a87060a0d3__section_bbv_53q_42b"/>

## Examples

The examples use the example table T defined below.

```
CREATE TABLE myTable (Class NVARCHAR(10), Value INT, Offset INT);
 INSERT INTO myTable VALUES('A', 1, 1);
 INSERT INTO myTable VALUES('A', 3, 3);
 INSERT INTO myTable VALUES('A', 5, NULL);
 INSERT INTO myTable VALUES('A', 5, 2);
 INSERT INTO myTable VALUES('A', 10, 0);
 INSERT INTO myTable VALUES('B', 1, 3);
 INSERT INTO myTable VALUES('B', 1, 1);
 INSERT INTO myTable VALUES('B', 7, 1);
```

```
SELECT Class, VALUE,
  ROW_NUMBER() OVER (PARTITION BY Class ORDER BY Value) AS ROW_NUM,
  RANK() OVER (PARTITION BY Class ORDER BY Value) AS RANK,
  DENSE_RANK() OVER (PARTITION BY Class ORDER BY Value) AS DENSE_RANK
 FROM myTable;
```


<table>
<tr>
<td valign="top">

class

</td>
<td valign="top">

val

</td>
<td valign="top">

row\_num

</td>
<td valign="top">

rank

</td>
<td valign="top">

dense\_rank

</td>
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


[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[COLLATIONS System View](../../020-System-Views-Reference/021-System-Views/collations-system-view-57ff6fd.md "Provides the list of collations that can be specified in an ORDER BY clause.")

[SAP HANA Cloud, SAP HANA Database Spatial Reference](https://help.sap.com/viewer/bc9e455fe75541b8a248b4c09b086cf5/2023_4_QRC/en-US/e1c934157bd14021a3b43b5822b2cbe9.html "This guide is the entry point for SAP HANA Spatial capabilities.") :arrow_upper_right:

[Windows Functions](windows-functions-4958a2b.md "Window functions allow you to perform analytic operations over a set of input rows.")

