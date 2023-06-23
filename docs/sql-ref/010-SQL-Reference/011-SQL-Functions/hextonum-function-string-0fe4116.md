<!-- loio0fe4116d8e7347d6a22923c6d7b8c6e2 -->

# HEXTONUM Function \(String\)

Converts a hexadecimal value to a BIGINT string value.



<a name="loio0fe4116d8e7347d6a22923c6d7b8c6e2__sql_function_bintohex_1sql_function_bintohex_syntax"/>

## Syntax

```
HEXTONUM(<string> [, -1])
```



<a name="loio0fe4116d8e7347d6a22923c6d7b8c6e2__section_gdq_1hw_vdb"/>

## Syntax Elements


<dl>
<dt><b>

*<string\>*

</b></dt>
<dd>

Specifies the hexadecimal value to be converted to a string value.



</dd><dt><b>

\-1

</b></dt>
<dd>

The result is interpreted as a negative number if a second parameter is provided.



</dd>
</dl>



<a name="loio0fe4116d8e7347d6a22923c6d7b8c6e2__sql_function_bintohex_1sql_function_bintohex_description"/>

## Description

Converts a hexadecimal value to a string value as a BIGINT data type. The input value must be an NVARCHAR string type that is no longer than 16 characters.



<a name="loio0fe4116d8e7347d6a22923c6d7b8c6e2__sql_function_bintohex_1sql_function_bintohex_examples"/>

## Example

The following example converts the hexadecimal value ***c2*** to a BIGINT string value ***12,345***:

```
CREATE TABLE t2 (c2 NVARCHAR(16));
INSERT INTO t2 VALUES('7FFFFFFFFFFFFFFF');
INSERT INTO t2 VALUES('8000000000000000');
INSERT INTO t2 VALUES ('FFFFFFFFFFFFFFFF');
INSERT INTO t2 VALUES ('0');
INSERT INTO t2 VALUES ('3039');
SELECT c2, HEXTONUM(c2) FROM t2;
```

**Related Information**  


[Character String Data Types](../character-string-data-types-a33f788.md "Character string data types are used to store values that contain character strings.")

