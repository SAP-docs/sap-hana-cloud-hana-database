<!-- loio7c5d6f9cea634b1ab572a8d358aee825 -->

# BITNOT Function \(Numeric\)

Performs a bitwise NOT operation on the bits of an expression.



## Syntax

```
BITNOT(<expression>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression that the function performs a bitwise NOT operation on. *<expression\>* must be an INTEGER value.



</dd>
</dl>



## Description

Performs a bitwise NOT operation on the bits of the argument *<expression\>*.

The BITNOT functions works a bit differently than the BITAND function. The BITAND function converts string arguments into BIGINT, whereas the BITNOT function converts string arguments into INT.

The BITNOT function returns a result along the argument's type.



## Example

The following example performs a BITNOT operation on ***255***, and returns the value ***\-256*** for ***"bitnot"***:

```
SELECT BITNOT (255) "bitnot" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

