<!-- loio20e788537519101487829d6ad0ba5244 -->

# SIGN Function \(Numeric\)

Returns the sign \(positive or negative\) of the specified numeric argument.



<a name="loio20e788537519101487829d6ad0ba5244__sql_function_sign_1sql_function_sign_syntax"/>

## Syntax

```
SIGN(<number>)
```



<a name="loio20e788537519101487829d6ad0ba5244__sql_function_sign_1sql_function_sign_description"/>

## Description

Returns 1 if *<number\>* is a positive value, -1 if *<number\>* is a negative value, 0 if *<number\>* is equal to zero, and NULL if *<number\>* is equal to NULL.



<a name="loio20e788537519101487829d6ad0ba5244__sql_function_sign_1sql_function_sign_examples"/>

## Example

The following example returns the value ***\-1*** for `"sign"`:

```
SELECT SIGN (-15) "sign" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

