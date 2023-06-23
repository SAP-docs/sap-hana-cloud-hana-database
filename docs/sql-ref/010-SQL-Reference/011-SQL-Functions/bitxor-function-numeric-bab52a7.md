<!-- loiobab52a76fde24045bce31993aa3b3c82 -->

# BITXOR Function \(Numeric\)

Performs an XOR operation on the bits of two arguments.



## Syntax

```
BITXOR(<expression1>, <expression2>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression1\>*

</b></dt>
<dd>

An argument that must be an INTEGER or a VARBINARY value.



</dd><dt><b>

*<expression2\>*

</b></dt>
<dd>

An argument for the bitwise OR operation that must be an INTEGER or a VARBINARY value.



</dd>
</dl>



## Description

Performs an XOR operation on the bits of the arguments *<expression1\>* and *<expression2\>*.

The BITXOR functions works a bit differently than the BITAND function. The BITAND function converts string arguments into BIGINT, whereas the BITXOR function converts string arguments into INT.

The BITXOR function returns a result along the argument's type.



## Example

The following example performs a bitwise XOR operation for the arguments ***255*** and ***123***, and returns the value ***132*** for ***"bitxor"***:

```
SELECT BITXOR (255, 123) "bitxor" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

