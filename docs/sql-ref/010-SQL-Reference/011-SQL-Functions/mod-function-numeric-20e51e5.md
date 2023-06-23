<!-- loio20e51e5c751910149879aa97a95d564b -->

# MOD Function \(Numeric\)

Returns the remainder of a specified number divided by a specified divisor.



<a name="loio20e51e5c751910149879aa97a95d564b__sql_function_mod_1sql_function_mod_syntax"/>

## Syntax

```
MOD(<number>, <divisor>)
```



<a name="loio20e51e5c751910149879aa97a95d564b__sql_function_mod_1sql_function_mod_description"/>

## Description

Returns the remainder of a number *<number\>* divided by a divisor *<divisor\>*.

When *<number\>* is negative, this function acts differently to the standard computational modulo operation. The following list shows examples of what the MOD function returns as the result:

-   If *<divisor\>* is zero, then *<number\>* is returned.
-   If *<number\>* is greater than 0 and *<number\>* is less than *<divisor\>*, then *<number\>* is returned.
-   If *<number\>* is less than 0 and *<number\>* is greater than *<divisor\>*, then *<number\>* is returned.
-   In cases other than those mentioned above, the remainder of the absolute value of *<number\>* divided by the absolute value of *<divisor\>* is used to calculate the remainder. If *<number\>* is less than 0, then the returned remainder from MOD is a negative number, and if *<number\>* is greater than 0, then the returned remainder from MOD is a positive number.



<a name="loio20e51e5c751910149879aa97a95d564b__sql_function_mod_1sql_function_mod_examples"/>

## Example

The following example returns the value ***3***:

```
SELECT MOD (15, 4) "modulus" FROM DUMMY;
```

The following example returns the value ***\-3***:

```
SELECT MOD (-15, 4) "modulus" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

