<!-- loio20e23edb75191014b906e3271722de36 -->

# IFNULL Function \(Miscellaneous\)

Returns the first non-NULL input expression.



<a name="loio20e23edb75191014b906e3271722de36__sql_function_ifnull_1sql_function_ifnull_syntax"/>

## Syntax

```
IFNULL(<expression1>, <expression2>)
```



<a name="loio20e23edb75191014b906e3271722de36__sql_function_ifnull_1sql_function_ifnull_description"/>

## Description

IFNULL returns the first non-NULL input expression. If the data types of *<expression1\>* and *<expression2\>* are different, then SAP HANA chooses the data type with the higher precedence. For example, between TIMESTAMP and STRING, TIMESTAMP has the higher precedence. See the data types documentation for more information about data type precedence.

-   Returns *<expression1\>* if *<expression1\>* is not NULL.

-   Returns *<expression2\>* if *<expression1\>* is NULL.

-   Returns NULL if both input expressions are NULL.




<a name="loio20e23edb75191014b906e3271722de36__sql_function_ifnull_1sql_function_ifnull_examples"/>

## Example

The following query returns ***diff***:

```
SELECT IFNULL ('diff', 'same') "ifnull" FROM DUMMY;
```

The following query returns ***same***:

```
SELECT IFNULL (NULL, 'same') "ifnull" FROM DUMMY;
```

The following query returns ***NULL***:

```
SELECT IFNULL (NULL, NULL) "ifnull" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

