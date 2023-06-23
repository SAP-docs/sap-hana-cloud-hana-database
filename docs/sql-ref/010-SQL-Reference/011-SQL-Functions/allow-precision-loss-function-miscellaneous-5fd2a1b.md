<!-- loio5fd2a1b5a00649be90a77e6a712c164b -->

# ALLOW\_PRECISION\_LOSS Function \(Miscellaneous\)

Allows loss of precision when aggregating decimal values using an aggregate expression.



<a name="loio5fd2a1b5a00649be90a77e6a712c164b__sql_function_add_years_1sql_function_add_years_syntax"/>

## Syntax

```
ALLOW_PRECISION_LOSS( <aggregate_expression> )
```



<a name="loio5fd2a1b5a00649be90a77e6a712c164b__section_dzm_b3t_kfb"/>

## Syntax Elements


<dl>
<dt><b>

*<aggregate\_expression\>*

</b></dt>
<dd>

The aggregate expression for which to allow precision loss. Currently SUM is the only supported aggregate expression.

```
<aggregate_expression> ::= SUM ( <expression> )
```



</dd>
</dl>



<a name="loio5fd2a1b5a00649be90a77e6a712c164b__sql_function_add_years_1sql_function_add_years_description"/>

## Description

Use this function to improve performance of an aggregation expression on DECIMAL values when loss of precision is acceptable and to improve performance of the aggregation.



<a name="loio5fd2a1b5a00649be90a77e6a712c164b__sql_function_add_years_1sql_function_add_years_examples"/>

## Example

The following example shows the difference in values returned when using the ALLOW\_PRECISION\_LOSS function:

```
CREATE TABLE TESTTABLE (COL1 decimal(10,5), COL2 decimal);
INSERT INTO TESTTABLE VALUES(1.139999, 1.138888888);
INSERT INTO TESTTABLE VALUES(2.119999, 2.118888888);
INSERT INTO TESTTABLE VALUES(2.119999, 2.118888888);
INSERT INTO TESTTABLE VALUES(2.669999, 2.668888888);
				
-- The following query, which does not allow precision loss, returns 8.01, 8.01
SELECT SUM(TO_DECIMAL(COL1,10,2)), SUM(TO_DECIMAL(COL2,10,2)) FROM TESTTABLE;
				
-- The following query, which uses the ALLOW_PRECISION_LOSS function to allow precision loss, returns 8.04, 8.04
SELECT ALLOW_PRECISION_LOSS(SUM(TO_DECIMAL(COL1,10,2))), ALLOW_PRECISION_LOSS(SUM(TO_DECIMAL(COL2,10,2))) FROM TESTTABLE;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

