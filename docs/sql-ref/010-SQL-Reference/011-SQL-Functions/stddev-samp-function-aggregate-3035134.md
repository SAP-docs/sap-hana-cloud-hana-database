<!-- loio303513466051489dbe926bd482bfc5d9 -->

# STDDEV\_SAMP Function \(Aggregate\)

Returns the standard deviation of the given expression as the square root of VAR\_SAMP function.



## Syntax

```
STDDEV_SAMP(<expression>)
```



## Description

Returns the standard deviation of the given *<expression\>* as the square root of the VAR\_SAMP function.



## Examples

The following example returns ***NULL*** for the standard deviation of the specified expression, as the square root of the VAR\_SAMP function:

```
CREATE ROW TABLE RTABLE (A INT);
INSERT INTO RTABLE VALUES (1);
SELECT STDDEV_SAMP(A) "STDDEVSAMP" FROM RTABLE;
```

The following example returns ***0.707107*** for the standard deviation of the specified expression, as the square root of VAR\_SAMP function:

```
INSERT INTO RTABLE VALUES (2);
SELECT STDDEV_SAMP(A) "STDDEVSAMP" FROM RTABLE;
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[STDDEV Function \(Aggregate\)](stddev-function-aggregate-c0c42b5.md "Returns the standard deviation of the given expression as the square root of the VAR function. This function can also be used as a window function.")

[STDDEV\_POP Function \(Aggregate\)](stddev-pop-function-aggregate-67d48b6.md "Returns the standard deviation of a given expression as the square root of the VAR_POP function.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

