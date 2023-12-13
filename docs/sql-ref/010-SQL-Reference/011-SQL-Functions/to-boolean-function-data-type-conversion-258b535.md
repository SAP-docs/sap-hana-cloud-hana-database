<!-- loio258b5350ad43487397d47f2ab309952d -->

# TO\_BOOLEAN Function \(Data Type Conversion\)

Converts a value to a BOOLEAN data type.



<a name="loio258b5350ad43487397d47f2ab309952d__sql_function_to_binary_1sql_function_to_binary_syntax"/>

## Syntax

```
TO_BOOLEAN(<value>)
```



<a name="loio258b5350ad43487397d47f2ab309952d__section_u5s_hjb_qdb"/>

## Syntax Elements


<dl>
<dt><b>

*<value\>*

</b></dt>
<dd>

If *<value\>* is:

-   `1`, `'true'`, or `true` then TO\_BOOLEAN returns the value ***true***.
-   `0`, `'false'`, or `false` then TO\_BOOLEAN returns the value ***false***.
-   `unknown(Boolean)` or '`unknown`' then TO\_BOOLEAN returns the value ***unknown***.


'`true`', '`false`', and '`unknown`' are not case sensitive, meaning that values of '`TRUE`' and '`TruE`' are treated the same as a value of `true`. TO\_BOOLEAN throws an exception when *<value\>* is not one of `true`, `false`, `unknown`, 0, 1, '0', '1',`'true'`,`'false'` or `'unknown'`.



</dd>
</dl>



<a name="loio258b5350ad43487397d47f2ab309952d__sql_function_to_binary_1sql_function_to_binary_description"/>

## Description

Converts a *<value\>* to a BOOLEAN data type.



<a name="loio258b5350ad43487397d47f2ab309952d__sql_function_to_binary_1sql_function_to_binary_examples"/>

## Example

Converts the value `0` to the BOOLEAN value ***FALSE***.

```
SELECT TO_BOOLEAN(0) FROM DUMMY;
```

Converts the value `1` to the BOOLEAN value ***TRUE***.

```
SELECT TO_BOOLEAN(1) FROM DUMMY;
```

**Related Information**  


[Boolean Data Type](../boolean-data-type-f044a9c.md "The BOOLEAN data type stores boolean values, which are TRUE, FALSE, and UNKNOWN, where UNKNOWN is a synonym of NULL.")

