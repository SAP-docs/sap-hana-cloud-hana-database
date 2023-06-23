<!-- loio20faa69a75191014b3c8e132b035d5a8 -->

# BETWEEN Predicate

Compares a value with a list of values within the specified range and returns true or false.



<a name="loio20faa69a75191014b3c8e132b035d5a8__sql_predicates_range_predicate_1sql_predicates_range_predicate_syntax"/>

## Syntax

```
<between_predicate> ::= <expression> [NOT] BETWEEN <lower_expression> AND <upper_expression>
```



<a name="loio20faa69a75191014b3c8e132b035d5a8__sql_predicates_range_predicate_1sql_predicates_range_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The value to search for in the specified list of values.



</dd><dt><b>

*<lower\_expression\>*

</b></dt>
<dd>

An expression setting the lower bound of the value list to compare *<expression\>* to.



</dd><dt><b>

*<upper\_expression\>*

</b></dt>
<dd>

An expression setting the upper bound of the value list to compare *<expression\>* to.



</dd><dt><b>

NOT

</b></dt>
<dd>

Inverts the operation of the BETWEEN predicate: returns TRUE when *<expression\>* is not in the range of values specified between *<lower\_expression\>* and *<upper\_expression\>*, including equal to *<lower\_expression\>* and *<upper\_expression\>*.



</dd>
</dl>



<a name="loio20faa69a75191014b3c8e132b035d5a8__sql_predicates_range_predicate_1sql_predicates_comparsion_predicate_description"/>

## Description

The range predicate returns true if *<expression1\>* is within the range specified by *<lower\_expression\>* and *<upper\_expression\>*, and NOT is not specified.

> ### Note:  
> TRUE will only be returned if *<lower\_expression\>* has a value less than or equal to *<upper\_expression\>*.

An expression is either a simple expression such as a character, a date or a number, or it can be a scalar subquery.

**Related Information**  


[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

