<!-- loio20eba7c375191014b9bfbf21581ee86a -->

# TO\_BLOB Function \(Data Type Conversion\)

Converts a binary string or NCLOB \(or CLOB which is an alias of NCLOB\) data type to a BLOB data type.



<a name="loio20eba7c375191014b9bfbf21581ee86a__sql_function_to_blob_1sql_function_to_blob_syntax"/>

## Syntax

```
TO_BLOB(<value>)

<value> ::= <binary string> | <nclob_value> | <clob_value>
```



<a name="loio20eba7c375191014b9bfbf21581ee86a__sql_function_to_blob_1sql_function_to_blob_description"/>

## Description

Converts a BINARY, NCLOB \(or CLOB which is an alias of NCLOB\) *<value\>* to a BLOB data type.



<a name="loio20eba7c375191014b9bfbf21581ee86a__sql_function_to_blob_1sql_function_to_blob_examples"/>

## Example

The following example converts the BINARY value ***abcde*** to the BLOB value ***abcde***:

```
SELECT TO_BLOB (TO_BINARY('abcde')) "to blob" FROM DUMMY;
```

The following example converts the NCLOB value ***abc*** to the BLOB value `abc`:

```
SELECT TO_BLOB (TO_NCLOB('abc')) "to blob" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

