<!-- loiod18abab24ad9470d98a760b61955d073 -->

# RAND\_SECURE Function \(Numeric\)

Returns a pseudo-random value that is safe for cryptographic or security purposes.



## Syntax

```
RAND_SECURE()
```



## Description

Returns a DOUBLE value in the range of 0.0 to less than 1.0.

Values generated by the RAND\_SECURE function are safe for cryptographic or security purposes.

The RAND function offers better performance than the RAND\_SECURE function, but returns a value that is not safe for cryptographic or security purposes.



## Example

The following example returns a DOUBLE value similar to ***0.9646101191337793***.

```
SELECT RAND_SECURE() from dummy;
```

**Related Information**  


[RAND Function \(Numeric\)](rand-function-numeric-20e64d8.md "Returns a pseudo-random DOUBLE value.")

[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

