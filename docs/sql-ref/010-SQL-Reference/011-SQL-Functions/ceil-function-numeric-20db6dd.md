<!-- loio20db6dd575191014b704978452f92bbd -->

# CEIL Function \(Numeric\)

Returns the first integer that is greater than or equal to the specified value.



<a name="loio20db6dd575191014b704978452f92bbd__sql_function_ceil_1sql_function_ceil_syntax"/>

## Syntax

```
CEIL(<number>)
```



## Syntax Elements


<dl>
<dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the number that the function returns the integer for.



</dd>
</dl>



<a name="loio20db6dd575191014b704978452f92bbd__sql_function_ceil_1sql_function_ceil_description"/>

## Description

Returns the first integer that is greater than or equal to the value of *<n\>*.



<a name="loio20db6dd575191014b704978452f92bbd__sql_function_ceil_1sql_function_ceil_examples"/>

## Example

The following example returns the value ***15*** for ***"ceiling"***:

```
SELECT CEIL (14.5) "ceiling" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

