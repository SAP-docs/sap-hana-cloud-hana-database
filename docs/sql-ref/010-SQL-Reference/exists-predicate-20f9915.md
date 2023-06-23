<!-- loio20f9915f75191014a3d7aa14a0637e41 -->

# EXISTS Predicate

Tests for the presence of a value in a set and returns either true or false.



<a name="loio20f9915f75191014a3d7aa14a0637e41__sql_predicates_exists_predicate_1sql_predicates_exists_predicate_syntax"/>

## Syntax

```
<exists_predicate> ::= [NOT] EXISTS ( <subquery> )
```



<a name="loio20f9915f75191014a3d7aa14a0637e41__sql_predicates_range_predicate_1sql_predicates_range_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

NOT

</b></dt>
<dd>

Inverts the operation of the EXISTS predicate: true is returned when the *<subquery\>* returns an empty result set and false is returned when the *<subquery\>* returns a result set.



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

Specifies what to test for. For information on subqueries, see the SELECT statement.



</dd>
</dl>



<a name="loio20f9915f75191014a3d7aa14a0637e41__sql_predicates_exists_predicate_1sql_predicates_exists_predicate_description"/>

## Description

Returns true if the *<subquery\>* returns a result set that is not empty and returns false if the *<subquery\>* returns an empty result set.

**Related Information**  


[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

