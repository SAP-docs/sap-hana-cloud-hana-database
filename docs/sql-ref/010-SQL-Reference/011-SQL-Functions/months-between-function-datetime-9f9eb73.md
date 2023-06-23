<!-- loio9f9eb73468b04bbc9d6014d22d2bfb90 -->

# MONTHS\_BETWEEN Function \(Datetime\)

Computes the number of months between two dates.



<a name="loio9f9eb73468b04bbc9d6014d22d2bfb90__sql_function_month_between_1sql_function_month_between_syntax"/>

## Syntax

```
MONTHS_BETWEEN(<date_1>, <date_2>)
```



<a name="loio9f9eb73468b04bbc9d6014d22d2bfb90__sql_function_month_between_1sql_function_month_between_description"/>

## Description

Computes the number of months between *<date\_1\>* and *<date\_2\>*. Returns NULL if either of *<date\_1\>* or *<date\_2\>* is NULL.



<a name="loio9f9eb73468b04bbc9d6014d22d2bfb90__sql_function_month_between_1sql_function_month_between_examples"/>

## Examples

The following example returns ***2*** for the months between the two dates:

```
SELECT MONTHS_BETWEEN(TO_DATE ('2003-01-01'), TO_DATE('2003-03-14')) "months_between" FROM DUMMY;
```

The following example returns ***\-8*** for the months between the two dates:

```
SELECT MONTHS_BETWEEN(TO_DATE ('2003-10-03'), TO_DATE('2003-01-14')) "months_between" FROM DUMMY;
```

The following example returns ***\-9*** for the months between the two dates:

```
SELECT MONTHS_BETWEEN(TO_DATE ('2003-10-15'), TO_DATE('2003-01-14')) "months_between" FROM DUMMY;
```

The following example returns ***\-8*** for the months between the two dates:

```
SELECT MONTHS_BETWEEN(TO_DATE ('2003-10-13'), TO_DATE('2003-01-14')) "months_between" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

