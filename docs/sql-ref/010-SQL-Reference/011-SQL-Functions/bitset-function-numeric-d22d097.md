<!-- loiod22d0974d29510149373deadadc83fe4 -->

# BITSET Function \(Numeric\)

Sets a specific number of bits to 1 in a target number from a specified 1-based index position.



<a name="loiod22d0974d29510149373deadadc83fe4__sql_function_bitset_1sql_function_bitset_syntax"/>

## Syntax

```
BITSET(<target_num>, <start_bit>, <num_to_set>)
```



<a name="loiod22d0974d29510149373deadadc83fe4__sql_function_bitset_1sql_function_bitset_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<target\_num\>*

</b></dt>
<dd>

The VARBINARY number where the bits are to be set.

```
<target_num> ::= <string_literal>
```



</dd><dt><b>

*<start\_bit\>*

</b></dt>
<dd>

A 1-based index position where the first bit is to be set.

```
<start_bit> ::= <unsigned_integer>
```



</dd><dt><b>

*<num\_to\_set\>*

</b></dt>
<dd>

The number of bits to be set in the target number.

```
<num_to_set> ::= <unsigned_integer>
```



</dd>
</dl>



<a name="loiod22d0974d29510149373deadadc83fe4__sql_function_bitset_1sql_function_bitset_description"/>

## Description

Sets *<num\_to\_set\>* bits to 1 in *<target\_num\>* from the *<start\_bit\>* position.



<a name="loiod22d0974d29510149373deadadc83fe4__sql_function_bitset_1sql_function_bitset_examples"/>

## Example

The following example returns the value ***E000*** for `"bitset"`:

```
SELECT BITSET ('0000', 1, 3) "bitset" FROM DUMMY;
```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

