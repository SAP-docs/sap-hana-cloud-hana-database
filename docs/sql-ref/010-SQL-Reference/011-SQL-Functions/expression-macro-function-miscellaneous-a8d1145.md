<!-- loioa8d114522b3a445bb877039fa208f9ba -->

# EXPRESSION\_MACRO Function \(Miscellaneous\)

Returns aggregated results from a query.



<a name="loioa8d114522b3a445bb877039fa208f9ba__section_yvx_tdd_kcb"/>

## Syntax

```
EXPRESSION_MACRO( <expression_macro_alias> ) 
```



<a name="loioa8d114522b3a445bb877039fa208f9ba__section_zvx_tdd_kcb"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\_macro\_alias\>*

</b></dt>
<dd>

Specifies the name of an expression macro.



</dd>
</dl>



<a name="loioa8d114522b3a445bb877039fa208f9ba__section_awx_tdd_kcb"/>

## Description

Use the EXPRESSION\_MACRO function to select an expression that is based on columns and other EXPRESSION\_MACROs from the view and that may also involve aggregation functions \(like AVG\). A SELECT statement with an EXPRESSION\_MACRO that involves an aggregation function requires the same GROUP BY clause as if the aggregation function had appeared directly in the SELECT statement.

The list of all expression macros can be found in the VIEW\_EXPRESSION\_MACROS system view.



<a name="loioa8d114522b3a445bb877039fa208f9ba__section_bwx_tdd_kcb"/>

## Example

The following example creates a table, defines a view on the table that includes an expression macro, and then queries the view using the EXPRESSION\_MACRO function to have the expression macro perform calculations on the result. In this example, the value 15 is returned \(the average of 10 and 20\).

```
CREATE TABLE t1(a INT);
INSERT INTO t1 VALUES(10);
INSERT INTO t1 VALUES(20);
CREATE VIEW v1 AS SELECT * FROM t1 WITH EXPRESSION MACROS(AVG(a) AS avgA);
SELECT EXPRESSION_MACRO(avgA) FROM v1;
```

**Related Information**  


[VIEW\_EXPRESSION\_MACROS System View](../../020-System-Views-Reference/021-System-Views/view-expression-macros-system-view-d163421.md "Describes the expression macros defined for views.")

