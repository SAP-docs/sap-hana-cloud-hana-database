<!-- loio20a4389775191014b5a6bf2ccc0df2ed -->

# Expressions

An expression is a clause that can be evaluated to return values.



<a name="loio20a4389775191014b5a6bf2ccc0df2ed___fsql_expressions_1sql_expressions_syntax"/>

## Syntax

```
<expression> ::= <case_expression>
               | <function_expression>
               | <aggregate_expression>
               | ( <expression> )
               | <json_object_expression>
               | ( <subquery> )
               | - <expression>
               | <expression> <operator> <expression>
               | <variable_name>
               | <constant>
               | [<correlation_name>.]<column_name>

```



<a name="loio20a4389775191014b5a6bf2ccc0df2ed___fsql_expressions_1sql_expressions_case_expressions"/>

## Case Expressions

A case expression allows the user to use IF - THEN - ELSE logic without using SQLScript in SQL statements.

 **Syntax** 

```
<case_expression> ::= <simple_case_expression> | <search_case_expression>

<simple_case_expression> ::= 
            CASE <expression>
            WHEN <expression> THEN <expression>
            [{ WHEN <expression> THEN <expression>}…]
            [ ELSE <expression>]
            END

<search_case_expression> > ::= 
            CASE 
            WHEN <condition> THEN <expression>
            [{ WHEN <condition> THEN <expression>}…] 
            [ ELSE <expression>]
            END

<condition> ::= <condition> OR <condition> | <condition> AND <condition>
              | NOT <condition> | ( <condition> ) | <predicate>

```

If the expression following the CASE statement is equal to the expression following the WHEN statement, then the expression following the THEN statement is returned. Otherwise, the expression following the ELSE statement is returned if it exists.

While some short-circuiting behavior to improve performance may take place, when and whether all WHEN clauses are evaluated in a CASE expression is not guaranteed.

If all *<expression\>* \(this includes predicate expressions and/or scalar expressions\) do not return an error, then the result of CASE expression is deterministic. That is, the CASE expression will always return a value \(returning behavior\) and will always return a value from the first matching part \(return value behavior\).

If any *<expression\>* returns an error, then the result of CASE is not deterministic; it may return a value or throw an error depending on an evaluation order of expressions determined by the HANA Optimizer and execution engine. If in this scenario CASE does return a value, then the value will be from the first matching part.

Consider the following example:

`CASE WHEN p1 THEN e1 WHEN p2 THEN e2 ELSE e3 END`

In SAP HANA, p1, e1, p2, e2 and e3 can be evaluated in any order. But let's assume for example's sake that p1 would always return TRUE, and e2 would always throw an exception.

If the order chosen is p1 \> e1 \> p2 \> e2 \> e3, and since p1 returns TRUE, then e1 is evaluated and returned as the result of the CASE expression. The remainder of the expressions p2, e2, and e3, are never evaluated so an exception is not thrown for e2.

If the order chosen is : e1 \> e2 \> e3 \> p1 \> p2, and since e2 returns an exception, then the rest of e3, p1, p2 is never evaluated and an exception is thrown.

Either of these orders and outcomes are possible in SAP HANA, and this is true for both*< simple\_case\_expression\>* and *<search\_case\_expression\>*.



<a name="loio20a4389775191014b5a6bf2ccc0df2ed___fsql_expressions_1sql_expressions_function_expressions"/>

## Function Expressions

SQL built-in functions can be used as expressions.

 **Syntax** 

```
 <function_expression> ::= <function_name> ( <expression> [{, <expression>}...] )

```



<a name="loio20a4389775191014b5a6bf2ccc0df2ed___fsql_expressions_1sql_expressions_aggregate_expressions"/>

## Aggregate Expressions

An aggregate expression uses an aggregate function to calculate a single value from the values of multiple rows in one or more columns.

**Syntax** 

```
 <aggregate_expression> ::= 
 COUNT(*) 
 | COUNT ( DISTINCT <expression_list> ) 
 | <agg_name> (  [ ALL | DISTINCT ] <expression> ) 
 | STRING_AGG ( <expression> [, <delimiter>] [<aggregate_order_by_clause>]) 

<agg_name> ::= CORR | CORR_SPEARMAN | COUNT | MIN | MEDIAN | MAX | SUM | AVG | STDDEV | VAR  | STDDEV_POP | VAR_POP | STDDEV_SAMP | VAR_SAMP
<delimiter> ::= <string_constant>
<aggregate_order_by_clause> ::= ORDER BY <expression> [ ASC | DESC ] [ NULLS FIRST | NULLS LAST]
```

You can specify to sort the aggregate using the *<aggregate\_order\_by\_clause\>*. ASC sorts records in ascending order. DESC sorts records in descending order. By default, for ascending ordering, NULL values are returned first, and for descending they are returned last. You can override this behavior by using NULLS FIRST or NULLS LAST to explicitly specify NULL value ordering.

**Aggregate expressions with DISTINCT:** When you specify the DISTINCT keyword in a query, duplicate values are eliminated before calculations take place. The following aggregate functions are not supported for use with DISTINCT: STDDEV\_POP, STDDEV\_SAMP, VAR\_POP, VAR\_SAMP.


<table>
<tr>
<th valign="top">

Aggregate name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

CORR



</td>
<td valign="top">

Computes the Pearson product momentum correlation coefficient between two columns. See the CORR function for more details.



</td>
</tr>
<tr>
<td valign="top">

CORR\_SPEARMAN



</td>
<td valign="top">

Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. See the CORR\_SPEARMAN function for more details.



</td>
</tr>
<tr>
<td valign="top">

COUNT



</td>
<td valign="top">

Counts the number of rows returned by a query. COUNT\(\*\) returns the number of rows, regardless of the value of those rows and including duplicate values. COUNT\(*<expression\>*\) returns the number of non-NULL values for that expression returned by the query. COUNT\(DISTINCT *<expression\_list\>*\) returns the number of distinct values for that expressions returned by the query, excluding rows with all NULL values for that expression.



</td>
</tr>
<tr>
<td valign="top">

MIN



</td>
<td valign="top">

Returns the minimum value of the expression.



</td>
</tr>
<tr>
<td valign="top">

MEDIAN



</td>
<td valign="top">

Finds the statistical median of an input column with a numeric data type. See the MEDIAN function for more information.



</td>
</tr>
<tr>
<td valign="top">

MAX



</td>
<td valign="top">

Returns the maximum value of the expression.



</td>
</tr>
<tr>
<td valign="top">

SUM



</td>
<td valign="top">

Returns the sum of the expression.



</td>
</tr>
<tr>
<td valign="top">

AVG



</td>
<td valign="top">

Returns the arithmetical mean of the expression.



</td>
</tr>
<tr>
<td valign="top">

STDDEV



</td>
<td valign="top">

Returns the standard deviation of the given expression as the square root of the VAR function.



</td>
</tr>
<tr>
<td valign="top">

STDDEV\_POP



</td>
<td valign="top">

Returns the standard deviation of the given expression as the square root of the VAR\_POP function.



</td>
</tr>
<tr>
<td valign="top">

STDDEV\_SAMP



</td>
<td valign="top">

Returns the standard deviation of the given expression as the square root of the VAR\_SAMP function.



</td>
</tr>
<tr>
<td valign="top">

VAR



</td>
<td valign="top">

Returns the variance of the given expression as the square of the standard deviation.



</td>
</tr>
<tr>
<td valign="top">

VAR\_POP



</td>
<td valign="top">

Returns the population variance of expression as the sum of squares of the difference of *<expression\>* from the mean of *<expression\>*, divided by the number of rows remaining.



</td>
</tr>
<tr>
<td valign="top">

VAR\_SAMP



</td>
<td valign="top">

Returns the sample variance of expression as the sum of squares of the difference of *<expression\>* from the mean of *<expression\>*, divided by the number of rows remaining minus 1 \(one\).This function is similar to VAR, the only difference is that it returns NULL when the number of rows is 1.



</td>
</tr>
<tr>
<td valign="top">

STRING\_AGG



</td>
<td valign="top">

Returns the concatenated string.



</td>
</tr>
</table>

**Result type of numeric aggregate expressions**


<table>
<tr>
<th valign="top">

**`aggregate name`**



</th>
<th valign="top">

**`tinyint`**



</th>
<th valign="top">

**`smallint`**



</th>
<th valign="top">

**`integer`**



</th>
<th valign="top">

**`bigint`**



</th>
<th valign="top">

**`decimal(p,s)`**



</th>
<th valign="top">

**`decimal`**



</th>
<th valign="top">

**`real`**



</th>
<th valign="top">

**`double`**



</th>
</tr>
<tr>
<td valign="top">

**`COUNT`**



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`bigint`



</td>
</tr>
<tr>
<td valign="top">

**`MIN`**



</td>
<td valign="top">

`tinyint`



</td>
<td valign="top">

`smallint`



</td>
<td valign="top">

`integer`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`decimal(p,s)`



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
<tr>
<td valign="top">

**`MAX`**



</td>
<td valign="top">

`tinyint`



</td>
<td valign="top">

`smallint`



</td>
<td valign="top">

`integer`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`decimal(p,s)`



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
<tr>
<td valign="top">

**`SUM`**



</td>
<td valign="top">

`integer`



</td>
<td valign="top">

`integer`



</td>
<td valign="top">

`integer`



</td>
<td valign="top">

`bigint`



</td>
<td valign="top">

`decimal(p',s)` \*



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
<tr>
<td valign="top">

**`AVG`**



</td>
<td valign="top">

`decimal(9,6)`



</td>
<td valign="top">

`decimal(11,6)`



</td>
<td valign="top">

`decimal(16,6)`



</td>
<td valign="top">

`decimal(25,6)`



</td>
<td valign="top">

`decimal(p,s)`



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
<tr>
<td valign="top">

**`STDDEV`**



</td>
<td valign="top">

`decimal(9,6)`



</td>
<td valign="top">

`decimal(11,6)`



</td>
<td valign="top">

`decimal(16,6)`



</td>
<td valign="top">

`decimal(25,6)`



</td>
<td valign="top">

`decimal(p,s)`



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
<tr>
<td valign="top">

**`VAR`**



</td>
<td valign="top">

`decimal(9,6)`



</td>
<td valign="top">

`decimal(11,6)`



</td>
<td valign="top">

`decimal(16,6)`



</td>
<td valign="top">

`decimal(25,6)`



</td>
<td valign="top">

`decimal(p,s)`



</td>
<td valign="top">

`decimal`



</td>
<td valign="top">

`real`



</td>
<td valign="top">

`double`



</td>
</tr>
</table>

\* p' is determined by the following rule: p' = 18 when p <= 18, p' = 28 when p <= 28 and p' = 38 when p <= 38

The following statements return the number of distinct combinations of column A and column B values, excluding any all-NULL tuples.

```
CREATE ROW TABLE T (A INT, B INT);
 INSERT INTO T VALUES (NULL, NULL);
 INSERT INTO T VALUES (1, NULL);
 INSERT INTO T VALUES (1, NULL);
 INSERT INTO T VALUES (NULL, 1);
 INSERT INTO T VALUES (1, 1);
 INSERT INTO T VALUES (1, 1);

 SELECT COUNT (DISTINCT A, B) AS DISTINCT_A_B FROM T;

 distinct_a_b
 3
```

Based on the values in the table, there are three distinct combinations \(shown in bold below\) that are not an all-NULL tuple:

-   A=1, B=NULL

-   A=NULL, B=1

-   A=1, B=1




<a name="loio20a4389775191014b5a6bf2ccc0df2ed__json_object_expressions"/>

## JSON Object Expressions

The JSON object expression generates a JSON object, and looks very similar to a JSON document, including being wrapped in curly braces. A JSON object comprises one or more key-value pairs, where:

-   *<key\>* is similar to a string literal and must always be enclosed in double quotes.
-   *<value\>* is the value for the key and can be any kind of expression, including nested JSON objects enclosed in curly braces \(\{ \}\), or arrays enclosed in square braces \(\[ \]\).


JSON object expressions are only allowed when working with JSON collection tables. They can be referenced by using statements such as SELECT, UPDATE, INSERT INTO, and can be used with operators, such as: +, -, /, \*.

**Syntax**

```
<json_object_expression> ::= {"<key>":<json_value_expression>}

<json_value_expression> ::= '<string>' 
 | <numeric_literal>
 | <boolean_literal>
 | NULL
 | <path_expression>
 | <json_object_expression>
 | <json_array_expression>

<json_array_expression> ::= [ <json_array_value_expression>,… ]

<json_array_value_expression> ::= '<string>' 
 | <numeric_literal>
 | <boolean_literal>
 | NULL
 | <path_expression>
 | <json_object_expression>
```

The following examples are valid JSON objects:

-   `{ "firstname":'John', "lastname":'Smith', "age":45 }`
-   `{ "firstname":'John', "lastname":'Smith', "age":45, "address": { 'street': 'Dietmar-Hopp-Allee', 'city': 'Heidelberg' } }`



<a name="loio20a4389775191014b5a6bf2ccc0df2ed___fsql_expressions_1sql_expressions_subqueries_in_expressions"/>

## Subqueries in Expressions

A subquery is a SELECT statement enclosed in parentheses. The SELECT statement can contain no more than one select list item. When used as an expression, a scalar subquery can only return a zero or a single value.

 **Syntax** 

```
<scalar_subquery_expression> ::= (<subquery>)
```

In the SELECT list of the top level SELECT, or in the SET clause of an UPDATE statement, you can use a scalar subquery anywhere where you can use a column name. scalar\_subquery cannot be used inside the GROUP BY clause however.

The following statement returns the number of employees in each department for example, grouped by department name:

```
 SELECT DepartmentName, COUNT(*), 'out of',
 (SELECT COUNT(*) FROM Employees)
 FROM Departments AS D, Employees AS E
 WHERE D.DepartmentID = E.DepartmentID
 GROUP BY DepartmentName;
```

**Related Information**  


[Predicates](predicates-20a2ab2.md "")

[MEDIAN Function \(Aggregate\)](011-SQL-Functions/median-function-aggregate-0531b49.md "Finds the statistical median of an input expression with a numeric data type. This function can also be used as a window function.")

[CORR\_SPEARMAN Function \(Aggregate\)](011-SQL-Functions/corr-spearman-function-aggregate-0579a65.md "Returns the Spearman's rank correlation coefficient of the values found in the corresponding rows of two columns. This function can also be used as a window function.")

[CORR Function \(Aggregate\)](011-SQL-Functions/corr-function-aggregate-aa049c2.md "Computes the Pearson product momentum correlation coefficient between two columns. This function can also be used as a window function.")

