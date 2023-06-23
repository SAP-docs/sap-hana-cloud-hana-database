<!-- loio20f91040751910148e96d6cb73119afc -->

# Comparison Predicates \(ANY, SOME, and ALL\)

Compares values using the specified comparison operator and returns true, false, or unknown.



<a name="loio20f91040751910148e96d6cb73119afc__sql_predicates_comparsion_predicate_1sql_predicates_comparsion_predicate_syntax"/>

## Syntax

```
<comparison_predicate> ::=  
 <expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( { <expression_list> | <subquery> } )
```



<a name="loio20f91040751910148e96d6cb73119afc__sql_predicates_comparsion_predicate_1sql_predicates_comparsion_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\_list\>*

</b></dt>
<dd>

```
<expression_list> ::= <expression> [{, <expression>}...]
```

An *<expression\>* is either a simple expression such as a character, a date or a number, or it can be a scalar subquery.



</dd><dt><b>

ANY | SOME

</b></dt>
<dd>

Specifies that the comparison returns true if the comparison of the *<expression\>* and at least one value returned by the *<subquery\>* or *<expression\_list\>* is true. For example:

```
SELECT * FROM DeptTable WHERE DeptTable.LocColumn = SOME ('BOSTON','DALLAS');
```

If the *<subquery\>* or *<expression\_list\>* is empty, the comparison returns false.

ANY and SOME, with the equal operator, is the equivalent of IN.



</dd><dt><b>

ALL

</b></dt>
<dd>

Specifies that the comparison returns true if the comparison of all values returned by the *<subquery\>* or *<expression\_list\>* is true. If the *<subquery\>* or *<expression\_list\>* is empty, the comparison returns true. For example:

```
SELECT * FROM EmployeeTable WHERE EmployeeTable.Salary >= ALL (1400, 3000);
```



</dd>
</dl>



<a name="loio20f91040751910148e96d6cb73119afc__sql_predicates_range_predicate_1sql_predicates_comparsion_predicate_description"/>

## Description

Two values are compared using comparison predicates, and the comparison returns true, false, or unknown.

**Related Information**  


[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

