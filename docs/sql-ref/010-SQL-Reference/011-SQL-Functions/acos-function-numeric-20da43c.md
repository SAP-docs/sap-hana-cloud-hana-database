<!-- loio20da43ce751910148d53a3c6f36d4873 -->

# ACOS Function \(Numeric\)

Returns the arc-cosine, in radians, of a numeric argument between -1 and 1.



<a name="loio20da43ce751910148d53a3c6f36d4873__sql_function_acos_1sql_function_acos_syntax"/>

## Syntax

```
ACOS(<num>)
```



## Syntax Elements


<dl>
<dt><b>

*<num\>*

</b></dt>
<dd>

Specifies a numeric argument between -1 and 1.



</dd>
</dl>



<a name="loio20da43ce751910148d53a3c6f36d4873__sql_function_acos_1sql_function_acos_description"/>

## Description

Returns the arc-cosine, in radians, of the numeric argument *<n\>* between -1 and 1.



<a name="loio20da43ce751910148d53a3c6f36d4873__sql_function_acos_1sql_function_acos_examples"/>

## Example

The following example returns the value ***1.0471975511965979***:

```
SELECT ACOS (0.5) "acos" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

