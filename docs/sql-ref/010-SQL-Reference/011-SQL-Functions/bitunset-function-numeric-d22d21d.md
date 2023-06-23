<!-- loiod22d21ddd2951014a15dcdbdf3fc5e00 -->

# BITUNSET Function \(Numeric\)

Sets a specified number of bits to 0 in a target number from a specified 1-based index position.



<a name="loiod22d21ddd2951014a15dcdbdf3fc5e00__sql_function_bitunset_1sql_function_bitunset_syntax"/>

## Syntax

```
BITUNSET(<target_num>, <start_bit>, <num_to_unset>)
```



<a name="loiod22d21ddd2951014a15dcdbdf3fc5e00__sql_function_bitunset_1sql_function_bitunset_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<target\_num\>*

</b></dt>
<dd>

The VARBINARY number where the bits are to be unset.

```
<target_num> ::= <string_literal>
```



</dd><dt><b>

*<start\_bit\>*

</b></dt>
<dd>

A 1-based index position where the first bit is to be unset.

```
<start_bit> ::= <unsigned_integer>
```



</dd><dt><b>

*<num\_to\_set\>*

</b></dt>
<dd>

The number of bits to be unset in the target number.

```
<num_to_set> ::= <unsigned_integer>
```



</dd>
</dl>



<a name="loiod22d21ddd2951014a15dcdbdf3fc5e00__sql_function_bitunset_1sql_function_bitunset_description"/>

## Description

Sets *<num\_to\_unset\>* bits to 0 in *<target\_num\>* from the *<start\_bit\>* position.



<a name="loiod22d21ddd2951014a15dcdbdf3fc5e00__sql_function_bitunset_1sql_function_bitunset_examples"/>

## Example

The following example returns the value ***1FFF*** for ***"bitunset"***:

```
SELECT BITUNSET ('ffff', 1, 3) "bitunset" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

