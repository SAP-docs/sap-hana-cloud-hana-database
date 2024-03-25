<!-- loio323345041b9343479807a1c3dff38715 -->

# ABAP\_DF16RAW\_TO\_SMALLDECIMAL Function \(String\)

Converts from ABAP `DECFLOAT` type `DF16_RAW` to HANA `DECFLOAT` type `SMALLDECIMAL`.



<a name="loio323345041b9343479807a1c3dff38715__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
ABAP_DF16RAW_TO_SMALLDECIMAL(<binary_data_in_df16raw_format>)
```



<a name="loio323345041b9343479807a1c3dff38715__section_nxg_cdp_r4b"/>

## Syntax Elements


<dl>
<dt><b>

*<binary\_data\_in\_df16raw\_format\>*

</b></dt>
<dd>

The format to convert: Decimal Floating Point, 16 Digits, RAW on database



</dd>
</dl>



<a name="loio323345041b9343479807a1c3dff38715__sql_function_lower_1sql_function_lower_description"/>

## Description

Converts from ABAP `DECFLOAT` type `DF16_RAW` to HANA `DECFLOAT` type `SMALLDECIMAL`.

Please note that only one-way conversion from ABAP to HANA type is available. The reverse conversion must be performed in the ABAP layer if needed. For more information, see[Decimal Floating Point Numbers](https://help.sap.com/doc/abapdocu_latest_index_htm/latest/en-US/index.htm?file=abenddic_decimal_floating_point.htm) in the ABAP Keyword Documentation.



<a name="loio323345041b9343479807a1c3dff38715__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example converts the binary value to type decimal.

```
CREATE TABLE t1(b binary(16))
INSERT INTO t1 values(X'BF2C000000000000')
INSERT INTO t1 values(X'BF54000000000001')
INSERT INTO t1 values(X'3DE3E7F9FE7F9FE7')

SELECT ABAP_DF16RAW_TO_SMALLDECIMAL(b) FROM t1
/* returns
[ Decimal('0.1')
, Decimal('1.000000000000001')
, Decimal('-0.1')]
*/
```

