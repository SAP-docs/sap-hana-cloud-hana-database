<!-- loio20f9d29a7519101483fb90fe2fadc959 -->

# IN Predicate

Searches for a value in a set of values and returns true or false.



<a name="loio20f9d29a7519101483fb90fe2fadc959__sql_predicates_in_predicate_1sql_predicates_in_predicate_syntax"/>

## Syntax

```
<in_predicate> ::= <search_for_expression> [ NOT ] IN { <search_in_expression_list> | <subquery> }
```



<a name="loio20f9d29a7519101483fb90fe2fadc959__sql_predicates_range_predicate_1sql_predicates_range_predicate_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<search\_for\_expression\>*

</b></dt>
<dd>

The column name or value expression to search for in the set.



</dd><dt><b>

*<search\_in\_expression\_list\>*

</b></dt>
<dd>

Specifies one or more expressions in which to search for *<search\_for\_expression\>*.

```
<search_in_expression_list> ::= <expression> [{, <expression> }...]
```



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

Specifies a subquery to search for *<search\_for\_expression\>* in.



</dd><dt><b>

NOT

</b></dt>
<dd>

Inverts the operation of the IN predicate: true is returned if *<search\_for\_expression\>* is *not* found in the specified set.



</dd>
</dl>



<a name="loio20f9d29a7519101483fb90fe2fadc959__sql_predicates_in_predicate_1sql_predicates_in_predicate_description"/>

## Description

True will be returned if the value of *<search\_for\_expression\>* is found in the *<search\_in\_expression\_list\>* or *<subquery\>*.

An expression is either a simple expression such as a character, a date or a number, or it can be a scalar subquery.

Tuples are supported for *<search\_for\_expression\>* and *<search\_in\_expression\>*. For example, `SELECT * FROM "mySchema"."myTable" WHERE (zone, company) IN (('124110','00'), ('124116','00'));`

Tuples \(list of tuples\) are also allowed when using subqueries instead of *<search\_in\_expression\>*.

While '=' \(equivalent to IN\) and '<\>' \(equivalent to NOT IN\) are supported, comparisons using symbols such as '<', '\>', and '!' are not supported.

Symbols '=', '<', '\>' and '!=' with a list of tuples is supported only when using quantified comparison with SOME/ANY/ALL.



<a name="loio20f9d29a7519101483fb90fe2fadc959__section_kvn_3p5_pgb"/>

## Examples

```
CREATE COLUMN TABLE "my_tab"
( order_nr NVARCHAR(10),
  item_nr  INTEGER,
  some_text NVARCHAR(100),
  PRIMARY KEY (order_nr, item_nr) );
  
INSERT INTO "my_tab" (order_nr, item_nr, some_text) VALUES ('A000000001', 1, 'A1 First Item');
INSERT INTO "my_tab" (order_nr, item_nr, some_text) VALUES ('A000000001', 2, 'A1 Second Item');
INSERT INTO "my_tab" (order_nr, item_nr, some_text) VALUES ('B000000001', 1, 'B1 First Item');
INSERT INTO "my_tab" (order_nr, item_nr, some_text) VALUES ('A000000002', 1, 'A2 First Item');
INSERT INTO "my_tab" (order_nr, item_nr, some_text) VALUES ('A000000002', 2, 'A2 Second Item');

SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) = ('A000000001', 2);
    
 SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) <> ('A000000001', 2);

SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) != ('A000000001', 2);

 -- works only when sub-select returns zero or one row
SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) != (select  order_nr, item_nr from "my_tab" where some_text like 'B1%');
      
-- error: feature not supported: only '=' and '<>'/'!=' operators are allowed here
SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) > ('A000000001', 2);

-- quantified comparison with SOME/ANY/ALL and sub-select is also supported          
 SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) <> ALL (select order_nr, item_nr from "my_tab" where some_text like 'B1%');
   
-- IN predicate is equivalent to quantified comparison = ANY/SOME
SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) in (('A000000001', 2), ('B000000001', 1));
SELECT * FROM "my_tab"
   WHERE (order_nr, item_nr) = ANY (('A000000001', 2), ('B000000001', 1));
```

**Related Information**  


[SELECT Statement \(Data Manipulation\)](012-SQL-Statements/select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[Expressions](expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

