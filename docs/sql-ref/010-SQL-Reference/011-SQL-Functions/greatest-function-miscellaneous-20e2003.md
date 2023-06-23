<!-- loio20e20038751910148ed9fadf866413e0 -->

# GREATEST Function \(Miscellaneous\)

Returns the greatest value among the specified arguments.



<a name="loio20e20038751910148ed9fadf866413e0__sql_function_greatest_1sql_function_greatest_syntax"/>

## Syntax

```
GREATEST(<argument> [{, <argument>}...])
```



<a name="loio20e20038751910148ed9fadf866413e0__sql_function_greatest_1sql_function_greatest_description"/>

## Description

Returns the greatest value among the arguments \(n1, n2, ...\). If one of the arguments is NULL, the return is NULL.



<a name="loio20e20038751910148ed9fadf866413e0__sql_function_greatest_1sql_function_greatest_examples"/>

## Example

The following example returns bb as the greatest value:

```
SELECT GREATEST ('aa', 'ab', 'ba', 'bb') "greatest" FROM DUMMY;
```

