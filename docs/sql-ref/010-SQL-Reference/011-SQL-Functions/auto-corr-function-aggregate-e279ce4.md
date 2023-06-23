<!-- loioe279ce4d3fbb41a2801057f93dced141 -->

# AUTO\_CORR Function \(Aggregate\)

Computes all autocorrelation coefficients for a given input expression and returns an array of values.



## Syntax

```
AUTO_CORR( <expression>, <maxTimeLag> { <series_order_by_clause> | <order_by_clause> })
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the input expression. *<expression\>* values can be of any numeric type.



</dd><dt><b>

*<maxTimeLag\>*

</b></dt>
<dd>

The time frame size is limited by the maxTimeLag parameter. This parameter must be a positive integer. The result size is the minimum of maxTimeLag and column size - 2 for dense series data.



</dd><dt><b>

*<series\_orderby\>*

</b></dt>
<dd>

*<series\_orderby\>* can only be used with an equidistant series.

```
<series_orderby> ::= SERIES( <series_period> <series_equidistant_definition> )
```

The use of SQLScript variables in this clause is not supported. The series \* must not contain missing elements. For more information about this clause, see the SERIES\_GENERATE function.



</dd><dt><b>

*<order\_by\_clause\>*

</b></dt>
<dd>

Specifies the sort order of the input rows.

```
<order_by_clause> ::= ORDER BY <order_by_expression> [, <order_by_expression> [,...] ]

<order_by_expression> ::= 
 <column_name> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
 | <column_position> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 

<collate_clause> ::= COLLATE <collation_name>
```

*<collate\_clause\>* specifies the collation to use for ordering values in the results. *<collate\_clause\>* can only be used on columns defined as NVARCHAR \(or VARCHAR, which is a synonym for NVARCHAR\).*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd>
</dl>



## Description

Computes all autocorrelation coefficients for a given input expression and returns an array of values.

Pairs that contain at least one null are removed. Even though AUTO\_CORR can handle null input values, it is highly recommended to replace null values first \(e.g. by using LINEAR\_APPROX\), which allows for much faster processing.

The output is empty if there are fewer than two rows.



## Examples

The example below shows autocorrelation of dense series data and returns ***\[0.285714,-0.351351,-0.5625,-0.25,1,1,1,1\]***.

```
CREATE COLUMN TABLE correlationTable (TS_ID NVARCHAR(10), DATE DAYDATE, VALUE DOUBLE);
INSERT INTO correlationTable VALUES ('A', '2014-10-01', 1);
INSERT INTO correlationTable VALUES ('A', '2014-10-02', 2);
INSERT INTO correlationTable VALUES ('A', '2014-10-03', 3);
INSERT INTO correlationTable VALUES ('A', '2014-10-04', 4);
INSERT INTO correlationTable VALUES ('A', '2014-10-05', 5);
INSERT INTO correlationTable VALUES ('A', '2014-10-06', 1);
INSERT INTO correlationTable VALUES ('A', '2014-10-07', 2);
INSERT INTO correlationTable VALUES ('A', '2014-10-08', 3);
INSERT INTO correlationTable VALUES ('A', '2014-10-09', 4);
INSERT INTO correlationTable VALUES ('A', '2014-10-10', 5);

SELECT TS_ID, AUTO_CORR(VALUE, 8 SERIES (PERIOD FOR SERIES(DATE)
        EQUIDISTANT INCREMENT BY INTERVAL 1 DAY MISSING ELEMENTS NOT ALLOWED))
    FROM correlationTable
    GROUP BY TS_ID ORDER BY TS_ID;
```

The example below shows autocorrelation of sparse series data without considering missing entries, and returns ***\[1,1,1,1,1\]***.

```
CREATE COLUMN TABLE correlationTable (ts_id NVARCHAR(20), date DAYDATE, val DOUBLE);
INSERT INTO correlationTable VALUES ('A', '2014-10-01', 1);
INSERT INTO correlationTable VALUES ('A', '2014-10-02', 2);
INSERT INTO correlationTable VALUES ('A', '2014-10-04', 3);
INSERT INTO correlationTable VALUES ('A', '2014-10-07', 4);
INSERT INTO correlationTable VALUES ('A', '2014-10-11', 5);
INSERT INTO correlationTable VALUES ('A', '2014-10-21', 6);
INSERT INTO correlationTable VALUES ('A', '2014-10-22', 7);

SELECT ts_id, AUTO_CORR(val, 999 SERIES (PERIOD FOR SERIES(DATE)
        EQUIDISTANT INCREMENT BY INTERVAL 1 DAY MISSING ELEMENTS NOT ALLOWED))
    FROM correlationTable
    GROUP BY ts_id ORDER BY ts_id;
```

The correlationTable has missing entries, such as '2014-10-03', but the WITHIN GROUP clause considers the series to be equidistant with one day intervals, where missing elements are not allowed.

Since the series data is assumed to be dense, the autocorrelation of the data set \[1..7\] is calculated.

The example below shows autocorrelation of sparse series data considering the missing entries, and returns ***\[1.0, null, 1.0, null, null, null, null, null, null, \* 1.0, null, null, null, null, null, null, null, null, null, 1.0\]***.

```
CREATE COLUMN TABLE correlationTable (ts_id NVARCHAR(20), date DAYDATE, val DOUBLE);
INSERT INTO correlationTable VALUES ('A', '2014-10-01', 1);
INSERT INTO correlationTable VALUES ('A', '2014-10-02', 2);
INSERT INTO correlationTable VALUES ('A', '2014-10-04', 3);
INSERT INTO correlationTable VALUES ('A', '2014-10-07', 4);
INSERT INTO correlationTable VALUES ('A', '2014-10-11', 5);
INSERT INTO correlationTable VALUES ('A', '2014-10-21', 6);
INSERT INTO correlationTable VALUES ('A', '2014-10-22', 7);

SELECT ts_id, AUTO_CORR(val, 999 SERIES (PERIOD FOR SERIES(DATE)
        EQUIDISTANT INCREMENT BY INTERVAL 1 DAY MISSING ELEMENTS ALLOWED))
    FROM correlationTable
    GROUP BY ts_id ORDER BY ts_id;
```

Autocorrelation works as if there were nulls instead of the missing elements in the column.

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[CORR Function \(Aggregate\)](corr-function-aggregate-aa049c2.md "Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.")

[CORR\_SPEARMAN Function \(Aggregate\)](corr-spearman-function-aggregate-0579a65.md "Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.")

[CROSS\_CORR Function \(Aggregate\)](cross-corr-function-aggregate-b2197a4.md "Computes all cross-correlation coefficients between two given expressions.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

