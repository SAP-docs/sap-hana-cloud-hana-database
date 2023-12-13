<!-- loio3688c8288c024907b4d933cd7c9a72c9 -->

# NUMTOHEX Function \(String\)

Converts a numeric value to an NVARCHAR hexadecimal value.



<a name="loio3688c8288c024907b4d933cd7c9a72c9__sql_function_bintohex_1sql_function_bintohex_syntax"/>

## Syntax

```
NUMTOHEX(<integer> [, <integer>])
```



<a name="loio3688c8288c024907b4d933cd7c9a72c9__section_gdq_1hw_vdb"/>

## Syntax Elements


<dl>
<dt><b>

*<integer\>*

</b></dt>
<dd>

Specifies the numeric value to be converted to a hexadecimal value.

The second parameter controls the length of the target type. If only one parameter is provided, then the length depends on the input type. The second parameter is limited to a 16 hex string length of BIGINT type.



</dd>
</dl>



<a name="loio3688c8288c024907b4d933cd7c9a72c9__sql_function_bintohex_1sql_function_bintohex_description"/>

## Description

Converts a numeric value to a hexadecimal value as an NVARCHAR data type. The input value can be a TINYINT, SMALLINT, BIGINT, or INTEGER data type.



<a name="loio3688c8288c024907b4d933cd7c9a72c9__sql_function_bintohex_1sql_function_bintohex_examples"/>

## Example

The following example converts the numeric value `c1` to a hexadecimal NVARCHAR value, ***3039***:

```
CREATE TABLE t1 (c1 BIGINT);
INSERT INTO t1 VALUES(9223372036854775807);
INSERT INTO t1 VALUES(-9223372036854775808);
INSERT INTO t1 VALUES (-1);
INSERT INTO t1 VALUES (0);
INSERT INTO t1 VALUES (12345);
SELECT c1, NUMTOHEX(c1) FROM t1;
```

