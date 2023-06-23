<!-- loiod88c19d816db4a58805bdc575c78e70c -->

# ABAP\_DF34RAW\_TO\_DECIMAL Function \(String\)

Converts from ABAP decfloat type DF34\_RAW to HANA decfloat type decimal.



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

Converts from ABAP decfloat type DF34\_RAW to HANA decfloat type decimal.



<a name="loiod88c19d816db4a58805bdc575c78e70c__sql_function_lower_1sql_function_lower_examples"/>

## Example

The following example converts the binary value to type decimal.

```
CREATE TABLE t2(b binary(32))
INSERT INTO t2 values(X'BF2C000000000000')
INSERT INTO t2 values(X'BF54000000000001')
INSERT INTO t2 values(X'3DE3E7F9FE7F9FE7')

SELECT ABAP_DF34RAW_TO_DECIMAL(b) FROM t2
/* returns
[ Decimal('0.1')
, Decimal('1.000000000000000000000000000000001')
, Decimal('3.141592653589793238462643383279503')]
*/

```

