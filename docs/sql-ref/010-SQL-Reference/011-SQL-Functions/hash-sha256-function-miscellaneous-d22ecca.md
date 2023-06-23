<!-- loiod22ecca9d2951014850492e8c88d498c -->

# HASH\_SHA256 Function \(Miscellaneous\)

Returns a 32 byte hash value of the concatenated arguments.



<a name="loiod22ecca9d2951014850492e8c88d498c__sql_function_hash_sha256_1sql_function_hash_sha256_syntax"/>

## Syntax

```
HASH_SHA256(<argument> [,...])
```



<a name="loiod22ecca9d2951014850492e8c88d498c__sql_function_hash_sha256_1sql_function_hash_sha256_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<argument\>*

</b></dt>
<dd>

Specifies an argument of type VARBINARY.

```
<argument> ::= <string_literal>
```



</dd>
</dl>



<a name="loiod22ecca9d2951014850492e8c88d498c__sql_function_hash_sha256_1sql_function_hash_sha256_description"/>

## Description

Returns a 32 byte VARBINARY hash value of the concatenated arguments. The hash is calculated using a SHA256 algorithm.

To ensure unique results from concatenated arguments, delimit the arguments with another string as shown in following the examples.



<a name="loiod22ecca9d2951014850492e8c88d498c__sql_function_hash_sha256_1sql_function_hash_sha256_examples"/>

## Example

The following query returns a hash value for the specified arguments:

```
SELECT HASH_SHA256 (TO_BINARY('database')) "hash" FROM DUMMY;
```

The following examples, which both return ***7D1A54127B222502F5B79B5FB0803061152A44F92B37E23C6527BAF665D4DA9A***, show how the function concatenates its arguments:

```
SELECT HASH_SHA256(TO_BINARY('abcd'), TO_BINARY('efg')) "test1" FROM DUMMY;
```

```
SELECT HASH_SHA256(TO_BINARY('abc'), TO_BINARY('defg')) "test2" FROM DUMMY;
```

The following examples show how you can delimit the arguments with another string \(in this case with 00\) to ensure unique results from the concatenation. The first statement returns ***156D73B945474C6FB04D7CCAC1E31ACA9425F756801AD487C3561FBE6661A659***, whereas the second statement returns ***6DE75B6290747BFA61C10FD0763344002C436475683B2B7E44C7C31FA920F1E3***. Without the delimiter, both statements return the same value: ***7D1A54127B222502F5B79B5FB0803061152A44F92B37E23C6527BAF665D4DA9A***.

```
SELECT HASH_SHA256(TO_BINARY('abcd'), '00', TO_BINARY('efg')) "test3" FROM DUMMY;
```

```
SELECT HASH_SHA256(TO_BINARY('abc'), '00', TO_BINARY('defg')) "test4" FROM DUMMY;
```

