<!-- loio12501aa67d624a87a60be1eda9c1d093 -->

# BITCOUNT Function \(Numeric\)

Counts the number of set bits of an expression.



## Syntax

```
BITCOUNT(<expression>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the expression that the function counts the number of set bits of. *<expression\>* must be an INTEGER or a VARBINARY value.



</dd>
</dl>



## Description

Counts the number of set bits of the argument *<expression\>*.

The BITCOUNT function returns an INTEGER value.



## Example

The following example counts the bits for `255`, and returns the value ***8***:

```
SELECT BITCOUNT (255) "bitcount" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

