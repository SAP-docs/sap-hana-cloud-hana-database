<!-- loiob2197a4784044933ae7c9ed240939dff -->

# CROSS\_CORR Function \(Aggregate\)

Computes all cross-correlation coefficients between two given expressions.



## Syntax

```
CROSS_CORR(<expression1>, <expression2>, <maxLag> 
    { <series_orderby> | <order_by_clause> } ).{ POSITIVE_LAGS | NEGATIVE_LAGS | ZERO_LAG }
```



## Syntax Elements


<dl>
<dt><b>

*<expression1\>* and *<expression2\>*

</b></dt>
<dd>

Numeric values between which the cross-correlation is calculated.



</dd><dt><b>

*<maxLag\>*

</b></dt>
<dd>

The *<maxLag\>* parameter must be a positive integer that defines the number of cross-correlation coefficients to be returned.

```
<maxLag> ::= INTEGER
```



</dd><dt><b>

*<series\_orderby\>*

</b></dt>
<dd>

The SERIES clause can only be used with an equidistant series. For more information about the SERIES clause, see the CREATE TABLE statement and the SERIES\_GENERATE function.

```
<series_orderby> ::= SERIES (<series_period> <series_equidistant_definition>)
```



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

Computes all cross-correlation coefficients between two given expressions.

The result is an array of cross-correlation coefficients of length *<maxLag\>*.

If POSITIVE\_LAGS is specified, then the cross-correlation coefficients with lags 1*<maxLag\>* are returned.

If NEGATIVE\_LAGS is specified, then the cross-correlation coefficients with lags -1 *<maxLag\>* are returned.

If ZERO\_LAG is specified, a single value associated with lag 0 is returned.

This function output can be non-deterministic among tie values.



## Example

**Example 1 - Cross correlation**

Execute the cross correlation example below:

```
CREATE COLUMN TABLE table1 ( ts_id INTEGER, number1 DOUBLE, number2 DOUBLE );

INSERT INTO table1 VALUES ('1', 1, 2);
INSERT INTO table1 VALUES ('2', 2 ,1);
INSERT INTO table1 VALUES ('3', 1 ,2);

SELECT CROSS_CORR(number1, number2, 10 ORDER BY ts_id) FROM table1;
```

The results are as follows:


<table>
<tr>
<th valign="top">

CROSS\_CORR\(NUMBER1,NUMBER2,10ORDERBYTS\_ID\)



</th>
</tr>
<tr>
<td valign="top">

1.0, -1.0, 1.0



</td>
</tr>
</table>

**Example 2 - Cross correlation using a series descriptor**

Execute the example below:

```
CREATE COLUMN TABLE TSeries( key INTEGER, ts TIMESTAMP, val1 DOUBLE, val2 DOUBLE, PRIMARY KEY(key, ts) )
    SERIES( SERIES KEY (key) EQUIDISTANT INCREMENT BY INTERVAL 1 DAY PERIOD FOR SERIES(ts) );

INSERT INTO TSeries VALUES (1, '2014-1-1', 1, 3);
INSERT INTO TSeries VALUES (2, '2014-1-3', 2, 4);
INSERT INTO TSeries VALUES (3, '2014-1-4', 4, 2);
INSERT INTO TSeries VALUES (4, '2014-1-5', 3, 1);

SELECT CROSS_CORR(val1, val2, 10 ORDER BY ts) FROM TSeries;
```

The results are as follows:


<table>
<tr>
<th valign="top">

CROSS\_CORR\(VAL1,VAL2,10ORDERBYTS\)



</th>
</tr>
<tr>
<td valign="top">

\-1.0, -0.928571, -0.6, 0.5, -1.0



</td>
</tr>
</table>

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[AUTO\_CORR Function \(Aggregate\)](auto-corr-function-aggregate-e279ce4.md "Computes all autocorrelation coefficients for a given input expression and returns an array of values.")

[CORR Function \(Aggregate\)](corr-function-aggregate-aa049c2.md "Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.")

[CORR\_SPEARMAN Function \(Aggregate\)](corr-spearman-function-aggregate-0579a65.md "Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[CREATE TABLE Statement \(Data Definition\)](../012-SQL-Statements/create-table-statement-data-definition-20d58a5.md "Creates a base or temporary table. See the CREATE VIRTUAL TABLE statement for creating virtual tables.")

