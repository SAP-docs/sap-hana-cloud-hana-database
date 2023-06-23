<!-- loio20db6dd27519101485b2978452f92bbd -->

# BINTOHEX Function \(String\)

Converts a binary string to an NVARCHAR hexadecimal value.



<a name="loio20db6dd27519101485b2978452f92bbd__sql_function_bintohex_1sql_function_bintohex_syntax"/>

## Syntax

```
BINTOHEX(<expression>)
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



<a name="loio20db6dd27519101485b2978452f92bbd__sql_function_bintohex_1sql_function_bintohex_description"/>

## Description

Converts a binary value to a hexadecimal value as an NVARCHAR data type. If the input value is not a binary value, then it is first converted to a binary value.



<a name="loio20db6dd27519101485b2978452f92bbd__sql_function_bintohex_1sql_function_bintohex_examples"/>

## Example

The following example converts the binary value ***AB*** to a hexadecimal NVARCHAR value ***4142***:

```
SELECT BINTOHEX('AB') "bintohex" FROM DUMMY;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

