<!-- loio20db65417519101484eded495b2526ae -->

# ATAN2 Function \(Numeric\)

Returns the arc-tangent, in radians, of the ratio of two numbers.



<a name="loio20db65417519101484eded495b2526ae__sql_function_atan2_1sql_function_atan2_syntax"/>

## Syntax

```
ATAN2(<number1>, <number2>)
```



## Syntax Elements


<dl>
<dt><b>

*<number1\>*

</b></dt>
<dd>

Specifies the first numeric argument.



</dd><dt><b>

*<number2\>*

</b></dt>
<dd>

Specifies the second numeric argument.



</dd>
</dl>



<a name="loio20db65417519101484eded495b2526ae__sql_function_atan2_1sql_function_atan2_description"/>

## Description

Returns the arc-tangent, in radians, of the ratio of two numbers *<number1\>* and *<number2\>*.



<a name="loio20db65417519101484eded495b2526ae__sql_function_atan2_1sql_function_atan2_examples"/>

## Example

The following example returns the value ***0.4636476090008061*** for `"atan2"`:

```
SELECT ATAN2 (1.0, 2.0) "atan2" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

