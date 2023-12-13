<!-- loio20e16ca5751910148da4fc7ec69bae03 -->

# DAYS\_BETWEEN Function \(Datetime\)

Computes the number of entire \(24 hour\) days between two dates.



<a name="loio20e16ca5751910148da4fc7ec69bae03__sql_function_days_between_1sql_function_days_between_syntax"/>

## Syntax

```
DAYS_BETWEEN(<date_1>, <date_2>)
```



<a name="loio20e16ca5751910148da4fc7ec69bae03__section_l1z_t25_zcb"/>

## Syntax Elements


<dl>
<dt><b>

*<date\_1\>*

</b></dt>
<dd>

Specifies the starting TIMESTAMP for the comparison.



</dd><dt><b>

*<date\_2\>*

</b></dt>
<dd>

Specifies the ending TIMESTAMP for the comparison.



</dd>
</dl>



<a name="loio20e16ca5751910148da4fc7ec69bae03__sql_function_days_between_1sql_function_days_between_description"/>

## Description

Computes the number of entire days between *<date\_1\>* and *<date\_2\>*.



<a name="loio20e16ca5751910148da4fc7ec69bae03__sql_function_days_between_1sql_function_days_between_examples"/>

## Example

The following example returns the value ***31*** for days between the two dates specified:

```
SELECT DAYS_BETWEEN (TO_DATE ('2009-12-05', 'YYYY-MM-DD'), TO_DATE('2010-01-05', 'YYYY-MM-DD')) "days between" FROM DUMMY;
```

The following example returns the value ***0*** for days between the two specified dates:

```
SELECT DAYS_BETWEEN('2018-02-07 23:00:00',  '2018-02-08 01:00:00') AS sinceDays FROM dummy;
```

The following example returns the value ***1*** for days between the two specified dates:

```
SELECT DAYS_BETWEEN('2018-02-07 23:00:00',  '2018-02-08 23:00:00') AS sinceDays FROM dummy;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[SAP Note 2573900 - Changed Behavior of the DAYS\_BETWEEN function in HANA 2.0 SPS03](https://me.sap.com/notes/2573900 - Changed Behavior of the DAYS_BETWEEN function in HANA 2.0
            SPS03)

