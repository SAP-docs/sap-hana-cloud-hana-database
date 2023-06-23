<!-- loio20ecb35c75191014b225b00e53f9c1b8 -->

# TO\_DATS Function \(Data Type Conversion\)

Converts a date string into an ABAP DATE string.



<a name="loio20ecb35c75191014b225b00e53f9c1b8__sql_function_to_dats_1sql_function_to_dats_syntax"/>

## Syntax

```
TO_DATS(<date>)
```



<a name="loio20ecb35c75191014b225b00e53f9c1b8__sql_function_to_dats_1sql_function_to_dats_description"/>

## Description

Converts the date string *<date\>* into an ABAP DATE string with format 'YYYYMMDD'.



<a name="loio20ecb35c75191014b225b00e53f9c1b8__sql_function_to_dats_1sql_function_to_dats_examples"/>

## Example

The following example converts the value ***2010-01-12*** to the ABAP DATE string ***20100112***.

```
SELECT TO_DATS ('2010-01-12') "abap date" FROM DUMMY;
```

**Related Information**  


[Data Type Conversion](../data-type-conversion-46ff965.md "Both implicit and explicit data type conversions are allowed in the SAP HANA database.")

