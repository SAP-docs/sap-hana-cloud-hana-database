<!-- loio20db38e775191014b31aa470840e14c6 -->

# ATAN Function \(Numeric\)

Returns the arc-tangent, in radians, of a numeric argument.



<a name="loio20db38e775191014b31aa470840e14c6__sql_function_atan_1sql_function_atan_syntax"/>

## Syntax

```
ATAN(<number>)
```



## Syntax Elements


<dl>
<dt><b>

*<number\>*

</b></dt>
<dd>

Specifies a numeric argument.



</dd>
</dl>



<a name="loio20db38e775191014b31aa470840e14c6__sql_function_atan_1sql_function_atan_description"/>

## Description

Returns the arc-tangent, in radians, of the numeric argument *<number\>*. The range of *<number\>* is unlimited.



<a name="loio20db38e775191014b31aa470840e14c6__sql_function_atan_1sql_function_atan_examples"/>

## Example

The following example returns the value ***0.4636476090008061*** for `"atan"`:

```
SELECT ATAN (0.5) "atan" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

