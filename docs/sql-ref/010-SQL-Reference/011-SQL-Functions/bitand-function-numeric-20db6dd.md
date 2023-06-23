<!-- loio20db6dd3751910148a57978452f92bbd -->

# BITAND Function \(Numeric\)

Performs an AND operation on the bits of two arguments.



<a name="loio20db6dd3751910148a57978452f92bbd__sql_function_bitand_1sql_function_bitand_syntax"/>

## Syntax

```
BITAND(<value1>, <value2>)
```



## Syntax Elements


<dl>
<dt><b>

*<value1\>*

</b></dt>
<dd>

The argument must be an INTEGER or a VARBINARY value.



</dd><dt><b>

*<value2\>*

</b></dt>
<dd>

The argument must be an INTEGER or a VARBINARY value.



</dd>
</dl>



<a name="loio20db6dd3751910148a57978452f92bbd__sql_function_bitand_1sql_function_bitand_description"/>

## Description

Performs an AND operation on the bits of the arguments *<value1\>* and *<value2\>*.

The BITAND function works a bit differently from the BITOR, BITXOR, and BITNOT functions. The BITAND function converts string arguments into BIGINT, whereas the other functions convert string arguments into INT.

The BITAND function returns a result along the argument's type.



<a name="loio20db6dd3751910148a57978452f92bbd__sql_function_bitand_1sql_function_bitand_examples"/>

## Example

The following example returns the value ***123***:

```
SELECT BITAND (255, 123) "bitand" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

