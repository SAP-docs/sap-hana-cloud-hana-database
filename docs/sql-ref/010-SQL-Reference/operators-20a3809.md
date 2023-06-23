<!-- loio20a380977519101494ceddd944e87527 -->

# Operators

Use operators to perform arithmetic operations in expressions. Operators can be used for calculation, value comparison, or to assign values.



-    [Unary and Binary Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_unary_and_binary_operators) 

-    [Operator Precedence](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_operator_precedence) 

-    [Arithmetic Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_arithmetic_operators) 

-    [String Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_string_operators) 

-    [Comparison Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_comparison_operators) 

-    [Logical Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_logical_operators) 

-    [Set Operators](operators-20a3809.md#loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_set_operators) 




<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_unary_and_binary_operators"/>

## Unary and Binary Operators

**Unary and binary operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Operation



</th>
<th valign="top">

Format



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

Unary



</td>
<td valign="top">

A unary operator applies to one operand or a single value expression.



</td>
<td valign="top">

operator operand



</td>
<td valign="top">

unary plus operator\(+\)

 

unary negation operator\(-\)

 

logical negation\(NOT\)

 

 



</td>
</tr>
<tr>
<td valign="top">

Binary



</td>
<td valign="top">

Binary A binary operator applies to two operands or two value expressions.



</td>
<td valign="top">

operand1 operator operand2



</td>
<td valign="top">

multiplicative operators \( \*, / \)

 

additive operators \( +,- \)

 

comparison operators

\( =,!=,<,\>,<=,\>=\)

 

logical operators \( AND, OR \)

 

 



</td>
</tr>
</table>



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_operator_precedence"/>

## Operator Precedence

An expression can use multiple operators. If the number of operators is greater than one, the SAP HANA database evaluates them in order of operator precedence. You can use parentheses to change the order of evaluation, as expressions contained within parentheses are always evaluated first.

If parentheses are not used, the precedence of the various operators is as indicated by the table below. The SAP HANA database evaluates operators with equal precedence from left to right within an expression.

**SQL operator precedence**


<table>
<tr>
<th valign="top">

Precedence



</th>
<th valign="top">

Operator



</th>
<th valign="top">

Operation



</th>
</tr>
<tr>
<td valign="top">

Highest



</td>
<td valign="top">

\(\)



</td>
<td valign="top">

parentheses



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

\+, -



</td>
<td valign="top">

unary positive and negative operation



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

\*, /



</td>
<td valign="top">

multiplication, division



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

\+, -



</td>
<td valign="top">

addition, subtraction



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

||



</td>
<td valign="top">

concatenation



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

=, !=, <, \>, <=, \>=, IS NULL, LIKE, BETWEEN



</td>
<td valign="top">

comparison



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

NOT



</td>
<td valign="top">

logical negation



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

AND



</td>
<td valign="top">

conjunction



</td>
</tr>
<tr>
<td valign="top">

Lowest



</td>
<td valign="top">

OR



</td>
<td valign="top">

disjunction



</td>
</tr>
</table>



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_arithmetic_operators"/>

## Arithmetic Operators

You use arithmetic operators to perform mathematical operations, such as adding, subtracting, multiplying, dividing and negation of numeric values.

**Arithmetic operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

\-*<expression\>* 



</td>
<td valign="top">

Negation. If the expression is NULL, the result is NULL.



</td>
</tr>
<tr>
<td valign="top">

 *<expression\>* + *<expression\>* 



</td>
<td valign="top">

Addition. If either expression is NULL, the result is NULL.



</td>
</tr>
<tr>
<td valign="top">

 *<expression\>* - *<expression\>* 



</td>
<td valign="top">

Subtraction. If either expression is NULL, the result is NULL.



</td>
</tr>
<tr>
<td valign="top">

 *<expression\>* \* *<expression\>* 



</td>
<td valign="top">

Multiplication. If either expression is NULL, the result is NULL.



</td>
</tr>
<tr>
<td valign="top">

 *<expression\>* / *<expression\>* 



</td>
<td valign="top">

Division. If either expression is NULL, or if the second expression is 0, an error is returned.



</td>
</tr>
</table>

When the result precision is larger than 38 \(the largest precision that the DECIMAL\(p, s\) type can hold\), the result type of arithmetic operators is DECIMAL \(floating-point decimal number\) type.

**The Result Precision and Scale of Arithmetic Operators on DECIMAL\(p, s\) Types Where e1 is DECIMAL\(p1, s2\) and e2 is DECIMAL\(p2, s2\)**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Result Precision



</th>
<th valign="top">

Result Scale



</th>
</tr>
<tr>
<td valign="top">

e1 + e2



</td>
<td valign="top">

max\(s1, s2\) + max\(p1-s1, p2-s2\) + 1



</td>
<td valign="top">

max\(s1, s2\)



</td>
</tr>
<tr>
<td valign="top">

e1 - e2



</td>
<td valign="top">

max\(s1, s2\) + max\(p1-s1, p2-s2\) + 1



</td>
<td valign="top">

max\(s1, s2\)



</td>
</tr>
<tr>
<td valign="top">

e1 \* e2



</td>
<td valign="top">

p1 + p2



</td>
<td valign="top">

s1 + s2



</td>
</tr>
<tr>
<td valign="top">

e1 / e2



</td>
<td valign="top">

p1 - s1 + s2 + max\(6, s1 + p2 + 1\)



</td>
<td valign="top">

max\(6, s1 + p2 + 1\)



</td>
</tr>
</table>



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_string_operators"/>

## String Operators

A concatenation operator combines two items, such as strings, expressions, or constants, into one.

**Concatenation operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 *<expression\>* || *<expression\>* 



</td>
<td valign="top">

String concatenation \(two vertical bars\).

If either string is NULL, it returns NULL.



</td>
</tr>
</table>

For VARCHAR or NVARCHAR type strings, leading or trailing spaces are retained. If either string is of data type NVARCHAR, the result has data type NVARCHAR and is limited to 64 MB in length. The maximum length for VARCHAR concatenation is also limited to 5000 characters.



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_comparison_operators"/>

## Comparison Operators

Syntax:

```
<comparison_operation> ::= <expression1> <comparison_operator> <expression2> 

```

**Comparison operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

=



</td>
<td valign="top">

Equal to



</td>
<td valign="top">

SELECT \* FROM students WHERE id = 25;



</td>
</tr>
<tr>
<td valign="top">

\>



</td>
<td valign="top">

Greater than



</td>
<td valign="top">

SELECT \* FROM students WHERE id \> 25;



</td>
</tr>
<tr>
<td valign="top">

<



</td>
<td valign="top">

Less than



</td>
<td valign="top">

SELECT \* FROM students WHERE id < 25;



</td>
</tr>
<tr>
<td valign="top">

\>=



</td>
<td valign="top">

Greater than or equal to



</td>
<td valign="top">

SELECT \* FROM students WHERE id \>= 25;



</td>
</tr>
<tr>
<td valign="top">

<=



</td>
<td valign="top">

Less than or equal to



</td>
<td valign="top">

SELECT \* FROM students WHERE id <= 25;



</td>
</tr>
<tr>
<td valign="top">

!=, <\>



</td>
<td valign="top">

Not equal



</td>
<td valign="top">

SELECT \* FROM students WHERE id != 25;

SELECT \* FROM students WHERE id <\> 25;



</td>
</tr>
</table>



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_logical_operators"/>

## Logical Operators

Search conditions can be combined using AND or OR operators. You can also negate them using the NOT operator.

**Logical operators**


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Syntax



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

AND



</td>
<td valign="top">

WHERE condition1 AND condition2



</td>
<td valign="top">

When using AND, the combined condition is TRUE if both conditions are TRUE, FALSE if either condition is FALSE, and UNKNOWN otherwise.



</td>
</tr>
<tr>
<td valign="top">

OR



</td>
<td valign="top">

WHERE condition1 OR condition2



</td>
<td valign="top">

When using OR, the combined condition is TRUE if either condition is TRUE, FALSE if both conditions are FALSE, and UNKNOWN otherwise.



</td>
</tr>
<tr>
<td valign="top">

NOT



</td>
<td valign="top">

WHERE NOT condition



</td>
<td valign="top">

The NOT operator is placed before a condition to negate the condition. The NOT condition is TRUE if condition is FALSE, FALSE if condition is TRUE, and UNKNOWN if condition is UNKNOWN.



</td>
</tr>
</table>



<a name="loio20a380977519101494ceddd944e87527___esql_operators_1sql_operators_set_operators"/>

## Set Operators

Set operators allow multiple queries to be combined to return a single result set.


<table>
<tr>
<th valign="top">

Operator



</th>
<th valign="top">

Returned Value



</th>
</tr>
<tr>
<td valign="top">

UNION



</td>
<td valign="top">

Combines the results of two or more select statements or query expressions



</td>
</tr>
<tr>
<td valign="top">

UNION ALL



</td>
<td valign="top">

Combines the results of two or more select statements or query expressions, including all duplicate rows.



</td>
</tr>
<tr>
<td valign="top">

INTERSECT



</td>
<td valign="top">

Combines the results of two or more select statements or query expressions, and returns all common rows.



</td>
</tr>
<tr>
<td valign="top">

EXCEPT



</td>
<td valign="top">

Takes the output from the first query and then removes the rows selected by the second query. MINUS is an accepted synonym for EXCEPT.



</td>
</tr>
</table>

**Related Information**  


[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

