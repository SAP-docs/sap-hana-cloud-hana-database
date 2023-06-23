<!-- loio20e5f7fe751910149ecdc8ee8a8a5c85 -->

# NULLIF Function \(Miscellaneous\)

Determines whether two expressions are equal.



<a name="loio20e5f7fe751910149ecdc8ee8a8a5c85__sql_function_nullif_1sql_function_nullif_syntax"/>

## Syntax

```
NULLIF(<expression1>, <expression2>)
```



<a name="loio20e5f7fe751910149ecdc8ee8a8a5c85__sql_function_nullif_1sql_function_nullif_description"/>

## Description

NULLIF compares the values of two expressions and returns NULL if *<expression1\>* equals *<expression2\>*.

If *<expression1\>* does not equal *<expression2\>*, then NULLIF returns *<expression1\>*.

If *<expression2\>* is NULL, then NULLIF returns *<expression1\>*.

NULLIF returns the same data type as *<expression1\>*. However, if *<expression1\>* is either TINYINT or SMALLINT, then NULLIF returns an INTEGER.



<a name="loio20e5f7fe751910149ecdc8ee8a8a5c85__sql_function_nullif_1sql_function_nullif_examples"/>

## Example

The following query returns ***diff***.

```
SELECT NULLIF ('diff', 'same') "nullif" FROM DUMMY;
```

The following query returns ***NULL***.

```
SELECT NULLIF('same', 'same') "nullif" FROM DUMMY;
```

