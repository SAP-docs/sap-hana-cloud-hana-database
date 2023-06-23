<!-- loio0662e967cf0342679ce7adf1a0e16aca -->

# BINTONHEX Function \(String\)

Converts a binary value to a hexadecimal value as an NVARCHAR data type.



<a name="loio0662e967cf0342679ce7adf1a0e16aca__sql_function_bintohex_1sql_function_bintohex_syntax"/>

## Syntax

```
BINTONHEX(<expression>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

The value to be converted to a hexadecimal value.



</dd>
</dl>



<a name="loio0662e967cf0342679ce7adf1a0e16aca__sql_function_bintohex_1sql_function_bintohex_description"/>

## Description

Converts a binary value to a hexadecimal value as an NVARCHAR data type. The input value is converted to a binary value first if it is not a binary value.



<a name="loio0662e967cf0342679ce7adf1a0e16aca__sql_function_bintohex_1sql_function_bintohex_examples"/>

## Example

The following example converts the binary value ***AB*** to a hexadecimal NVARCHAR value ***4142***.

```
SELECT BINTONHEX('AB') "bintonhex" FROM DUMMY; 
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

