<!-- loiod88c19d816db4a58805bdc575c78e70c -->

# ABAP\_DF34RAW\_TO\_DECIMAL Function \(String\)

Converts from ABAP `DECFLOAT` type `DF34_RAW` to HANA `DECFLOAT` type `DECIMAL`.



<a name="loiod88c19d816db4a58805bdc575c78e70c__sql_function_lower_1sql_function_lower_syntax"/>

## Syntax

```
ABAP_DF34RAW_TO_DECIMAL(<binary_data_in_df34raw_format>)
```



<a name="loiod88c19d816db4a58805bdc575c78e70c__section_nxg_cdp_r4b"/>

## Syntax Elements


<dl>
<dt><b>

*<binary\_data\_in\_df34raw\_format\>*

</b></dt>
<dd>

The format to convert: Decimal Floating Point, 34 Digits, RAW on database



</dd>
</dl>



<a name="loiod88c19d816db4a58805bdc575c78e70c__sql_function_lower_1sql_function_lower_description"/>

## Description

Converts from ABAP `DECFLOAT` type `DF34_RAW` to HANA `DECFLOAT` type `DECIMAL`.

Please note that only one-way conversion from ABAP to HANA type is available. The reverse conversion must be performed in the ABAP layer if needed. For more information, see[Decimal Floating Point Numbers](https://help.sap.com/doc/abapdocu_latest_index_htm/latest/en-US/index.htm?file=abenddic_decimal_floating_point.htm) in the ABAP Keyword Documentation.



<a name="loiod88c19d816db4a58805bdc575c78e70c__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example converts the binary value to type `DECIMAL`.

```
CREATE TABLE t2(b binary(64));
INSERT INTO t2 values(X'BDBBC000000000000000000000000000');
INSERT INTO t2 values(X'BDBE4000000000000000000000000001');
INSERT INTO t2 values(X'BDBEC8D9428D937193B9CEA0D7F45DF7');

SELECT ABAP_DF34RAW_TO_DECIMAL(b) FROM t2
/* returns
[ Decimal('0.1')
, Decimal('1.000000000000000000000000000000001')
, Decimal('3.141592653589793238462643383279503')]
*/

```

