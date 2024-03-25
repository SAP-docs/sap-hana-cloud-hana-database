<!-- loio4faac7bced8140b0a703eb32b420edf8 -->

# VAR\_POP Function \(Aggregate\)

Returns the population variance of an expression.



## Syntax

```
VAR_POP(<expression>)
```



## Description

Returns the population variance of the expression as the sum of squares of the difference of *<expression\>* from the mean of *<expression\>*, divided by the number of rows remaining.



## Examples

The following example returns ***0.2*** as the population variance for the specified expression:

```
CREATE ROW TABLE RTABLE (A INT);
INSERT INTO RTABLE VALUES (1);
SELECT VAR_POP(A) "VARPOP" FROM RTABLE;
```

The following example returns ***0.25*** as the population variance for the specified expression:

```
INSERT INTO RTABLE VALUES (2);
SELECT VAR_POP(A) "VARPOP" FROM RTABLE;
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[VAR Function \(Aggregate\)](var-function-aggregate-21a8eb1.md "Returns the variance of the given expression as the square of the standard deviation. This function can also be used as a window function.")

[VAR\_SAMP Function \(Aggregate\)](var-samp-function-aggregate-d1e36df.md "Returns the sample variance of an expression.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

