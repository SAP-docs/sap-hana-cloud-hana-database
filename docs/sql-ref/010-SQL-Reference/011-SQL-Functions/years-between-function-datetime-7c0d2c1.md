<!-- loio7c0d2c161ea34def86de3f5eadd6a0af -->

# YEARS\_BETWEEN Function \(Datetime\)

Computes the number of years between two specified dates.



<a name="loio7c0d2c161ea34def86de3f5eadd6a0af__sql_function_years_between_1sql_function_years_between_syntax"/>

## Syntax

```
YEARS_BETWEEN(<date_1>, <date_2>)
```



<a name="loio7c0d2c161ea34def86de3f5eadd6a0af__sql_function_years_between_1sql_function_years_between_description"/>

## Description

Computes the number of years between *<date\_1\>* and *<date\_2\>*. Returns NULL if either of *<date\_1\>* or *<date\_2\>* is NULL.



<a name="loio7c0d2c161ea34def86de3f5eadd6a0af__sql_function_years_between_1sql_function_years_between_examples"/>

## Examples

The following example returns the value ***2*** for the years between the two specified dates:

```
 SELECT YEARS_BETWEEN(TO_DATE('2001-01-01'), TO_DATE('2003-03-14')) "years_between" FROM DUMMY;
```

The following example returns the value ***\-2*** for the years between the two specified dates

```
 SELECT YEARS_BETWEEN(TO_DATE('2003-10-03'), TO_DATE('2001-01-14')) "years_between" FROM DUMMY;
```

The following example returns the value ***1*** for the years between the two specified dates

```
 SELECT YEARS_BETWEEN(TO_DATE('2001-10-15'), TO_DATE('2003-01-14')) "years_between" FROM DUMMY;
```

The following example returns the value ***1*** for the years between the two specified dates

```
 SELECT YEARS_BETWEEN(TO_DATE('2001-10-13'), TO_DATE('2003-01-14')) "years_between" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

