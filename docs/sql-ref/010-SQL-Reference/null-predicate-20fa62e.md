<!-- loio20fa62ef75191014a797dae048566adc -->

# NULL Predicate

Performs a comparison of the value of an expression with NULL.



<a name="loio20fa62ef75191014a797dae048566adc__sql_predicates_null_predicate_1sql_predicates_null_predicate_syntax"/>

## Syntax

```
<null_predicate> ::= <expression> IS [NOT] NULL
```



<a name="loio20fa62ef75191014a797dae048566adc__sql_predicates_null_predicate_1sql_predicates_null_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

An expression is either a simple expression such as a character, a date or a number, or it can be a scalar subquery.



</dd><dt><b>

IS NULL

</b></dt>
<dd>

Returns true if the value of *<expression\>* is NULL.



</dd><dt><b>

IS NOT NULL

</b></dt>
<dd>

Returns true if the value of *<expression\>* is not NULL.



</dd>
</dl>



<a name="loio20fa62ef75191014a797dae048566adc__sql_predicates_null_predicate_1sql_predicates_null_predicate_description"/>

## Description

Performs a comparison of the value of an expression with NULL.

**Related Information**  


[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

