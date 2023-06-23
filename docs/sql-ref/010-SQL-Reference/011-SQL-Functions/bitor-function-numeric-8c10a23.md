<!-- loio8c10a2303bc34150921debf745c25fe6 -->

# BITOR Function \(Numeric\)

This function performs an OR operation on the bits of two arguments.



## Syntax

```
BITOR(<expression1>, <expression2>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression1\>*

</b></dt>
<dd>

An argument for the bitwise OR operation that must be a non-negative INTEGER or VARBINARY value.



</dd><dt><b>

*<expression2\>*

</b></dt>
<dd>

An argument for the bitwise OR operation that must be a non-negative INTEGER or VARBINARY value.



</dd>
</dl>



## Description

This function performs an OR operation on the bits of the arguments *<expression1\>* and *<expression2\>*.

The BITOR functions works a bit differently than the BITAND function. The BITAND function converts string arguments into BIGINT, whereas the BITOR function converts string arguments into INT.

The BITOR function returns a result along the argument's type.



## Example

The following example performs a bitwise OR operation for the arguments ***255*** and ***123***, and returns the value ***255*** for ***"bitor"***:

```
SELECT BITOR (255, 123) "bitor" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

