<!-- loio20e2fddb75191014a794e3271722de36 -->

# LEAST Function \(Miscellaneous\)

Returns the lesser value of two specified arguments.



<a name="loio20e2fddb75191014a794e3271722de36__sql_function_least_1sql_function_least_syntax"/>

## Syntax

```
LEAST(<argument_1> [, <argument_2>]...)
```



<a name="loio20e2fddb75191014a794e3271722de36__sql_function_least_1sql_function_least_description"/>

## Description

Returns the lesser value of the arguments. If one of the arguments is NULL, the return is NULL.



<a name="loio20e2fddb75191014a794e3271722de36__sql_function_least_1sql_function_least_examples"/>

## Example

The following query returns ***aa***.

```
SELECT LEAST('aa', 'ab', 'ba', 'bb') "least" FROM DUMMY;
```

