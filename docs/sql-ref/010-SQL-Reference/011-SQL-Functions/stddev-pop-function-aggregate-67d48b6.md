<!-- loio67d48b64f0d048bfb028767cb377fbb2 -->

# STDDEV\_POP Function \(Aggregate\)

Returns the standard deviation of a given expression as the square root of the VAR\_POP function.



## Syntax

```
STDDEV_POP(<expression>)
```



## Description

Returns the standard deviation of the given expression as the square root of the VAR\_POP function.



## Examples

The following example returns ***0*** for the standard deviation of the specified expression:

```
CREATE ROW TABLE RTABLE (A INT);
INSERT INTO RTABLE VALUES (1);
SELECT STDDEV_POP(A) "STDDEVPOP" FROM RTABLE;
```

The following examples returns ***0.5*** for the standard deviation of the specified expression:

```
INSERT INTO RTABLE VALUES (2);
SELECT STDDEV_POP(A) "STDDEVPOP" FROM RTABLE;
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[STDDEV Function \(Aggregate\)](stddev-function-aggregate-c0c42b5.md "Returns the standard deviation of the given expression as the square root of the VAR function. This function can also be used as a window function.")

[STDDEV\_SAMP Function \(Aggregate\)](stddev-samp-function-aggregate-3035134.md "Returns the standard deviation of the given expression as the square root of VAR_SAMP function.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

