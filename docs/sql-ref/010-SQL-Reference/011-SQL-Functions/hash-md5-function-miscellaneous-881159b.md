<!-- loio881159b167a246e88926075e0c59ea36 -->

# HASH\_MD5 Function \(Miscellaneous\)

Returns a 32 byte hash value of the concatenated arguments.



<a name="loio881159b167a246e88926075e0c59ea36__sql_function_hash_md5_1sql_function_hash_md5_syntax"/>

## Syntax

```
HASH_MD5(<argument> [,...])
```



<a name="loio881159b167a246e88926075e0c59ea36__sql_function_hash_md5_1sql_function_hash_md5_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<argument\>*

</b></dt>
<dd>

Specifies a VARBINARY value.

```
<argument> ::= <string_literal>
```



</dd>
</dl>



<a name="loio881159b167a246e88926075e0c59ea36__sql_function_hash_md5_1sql_function_hash_md5_description"/>

## Description

Returns a 32 byte VARBINARY hash value of the concatenated arguments. The hash is calculated using a MD5 algorithm.

To ensure unique results from concatenated arguments, delimit the arguments with another string as shown in following the examples.



<a name="loio881159b167a246e88926075e0c59ea36__sql_function_hash_MD5_1sql_function_hash_MD5_examples"/>

## Example

In the example below, the query generates a hash value based on the provided input:

```
SELECT HASH_MD5 (TO_BINARY('database')) "hash" FROM DUMMY;
```

The following examples, which both return ***7AC66C0F148DE9519B8BD264312C4D64***, show how the function concatenates its arguments:

```
SELECT HASH_MD5(to_binary('abcd'), TO_BINARY('efg')) "test1" FROM DUMMY;
```

```
SELECT HASH_MD5(TO_BINARY('abc'), TO_BINARY('defg')) "test2" FROM DUMMY;
```

The following examples show how you can delimit the arguments with another string \(in this case with 00\) to ensure unique results from the concatenation. The first statement returns ***6BB6BD45C57D57ECC69A9EB81F7409BE***, whereas the second statement returns ***1CEDEB6EB7ED12D948F66593589FBD23***. Without the delimiter, both statements return the same value: ***7AC66C0F148DE9519B8BD264312C4D64***.

```
SELECT HASH_MD5(TO_BINARY('abcd'), '00', TO_BINARY('efg')) "test1" FROM DUMMY;
```

```
SELECT HASH_MD5(TO_BINARY('abc'), '00', TO_BINARY('defg')) "test2" FROM DUMMY;
```

