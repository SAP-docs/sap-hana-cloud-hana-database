<!-- loio20daebda751910148c77ac06bb049df2 -->

# ASIN Function \(Numeric\)

Returns the arc-sine, in radians, of a numeric argument.



<a name="loio20daebda751910148c77ac06bb049df2__sql_function_asin_1sql_function_asin_syntax"/>

## Syntax

```
ASIN(<number>)
```



## Syntax Elements


<dl>
<dt><b>

*<number\>*

</b></dt>
<dd>

Specifies a numeric argument between -1 and 1.



</dd>
</dl>



<a name="loio20daebda751910148c77ac06bb049df2__sql_function_asin_1sql_function_asin_description"/>

## Description

Returns the arc-sine, in radians, of the numeric argument *<number\>* between -1 and 1.



<a name="loio20daebda751910148c77ac06bb049df2__sql_function_asin_1sql_function_asin_examples"/>

## Example

The following example returns the value ***0.5235987755982989*** for `"asin"`:

```
SELECT ASIN (0.5) "asin" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

