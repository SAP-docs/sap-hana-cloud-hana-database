<!-- loio20e3d2fe7519101481a1fc67a4370740 -->

# LOG Function \(Numeric\)

Returns the natural logarithm of a specified number and base.



<a name="loio20e3d2fe7519101481a1fc67a4370740__sql_function_log_1sql_function_log_syntax"/>

## Syntax

```
LOG(<base>, <number>)
```



<a name="loio20e3d2fe7519101481a1fc67a4370740__sql_function_log_1sql_function_log_description"/>

## Description

Returns the natural logarithm of a number specified by *<number\>* and a base specified by *<base\>*, where *<base\>* must be a positive value other than 1, and *<number\>* must be any positive value.



<a name="loio20e3d2fe7519101481a1fc67a4370740__sql_function_log_1sql_function_log_examples"/>

## Example

The following example returns the natural logarithm for 2 base 10, which is ***0.30102999566398114***:

```
SELECT LOG (10, 2) "log" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

