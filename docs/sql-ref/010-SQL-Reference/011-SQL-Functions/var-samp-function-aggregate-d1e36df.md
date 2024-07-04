<!-- loiod1e36dfe43854bf5853fb7cca64b771b -->

# VAR\_SAMP Function \(Aggregate\)

Returns the sample variance of an expression.



## Syntax

```
VAR_SAMP(<expression>)
```



## Description

Returns the sample variance of the expression as the sum of squares of the difference of *<expression\>* from the mean of *<expression\>*, divided by the number of rows remaining minus 1. This function is similar to VAR, the only difference is that it returns NULL when the number of rows is 1.



## Examples

The following example returns ***NULL*** as the sample variance of the specified expression:

```
CREATE ROW TABLE RTABLE (A INT);
INSERT INTO RTABLE VALUES (1);
SELECT VAR_SAMP(A)"VARSAMP" FROM RTABLE;
```

The following example returns ***0.5*** as the sample variance of the specified expression:

```
INSERT INTO RTABLE VALUES (2);
SELECT VAR_SAMP(A) "VARSAMP" FROM RTABLE;
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[VAR Function \(Aggregate\)](var-function-aggregate-21a8eb1.md "Returns the variance of the given expression as the square of the standard deviation. This function can also be used as a window function.")

[VAR\_POP Function \(Aggregate\)](var-pop-function-aggregate-4faac7b.md "Returns the population variance of an expression.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

