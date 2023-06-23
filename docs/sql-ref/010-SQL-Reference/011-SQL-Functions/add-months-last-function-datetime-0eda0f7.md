<!-- loio0eda0f731fb34bd2a6237cd7d33374ef -->

# ADD\_MONTHS\_LAST Function \(Datetime\)

Computes the specified date plus the specified number of months, with the output date being the last day of the month if the input date is the last day of the month, even if those two dates differ.



## Syntax

```
ADD_MONTHS_LAST(<date>, <num_months>)
```



## Syntax Elements


<dl>
<dt><b>

*<date\>*

</b></dt>
<dd>

The date that is incremented.



</dd><dt><b>

*<num\_months\>*

</b></dt>
<dd>

The number of months by which to increment the date.



</dd>
</dl>



## Description

Computes the specified date plus the specified number of months. If the input date is the last day of the input month, then the output date is set to the last day of the output month.

To compute the date plus months without using the last day of the month functionality, use the ADD\_MONTHS function.

The parameter *<date\>* must be implicitly or explicitly converted to one of the following SQL data types:

-   DATE
-   TIMESTAMP
-   SECONDDATE

The SQL data type of the output parameters is the same as the SQL data type of the input parameters. For example, ADD\_MONTHS\_LAST\(DATE\) returns a date, while ADD\_MONTHS\_LAST\(TIMESTAMP\) returns a timestamp.



## Example

The following example increments the date 2009-02-28 \(the last day in February\), by one month, and returns the value 2009-03-31, \(the last day of March\).

```
SELECT ADD_MONTHS_LAST (TO_DATE ('2009-02-28', 'YYYY-MM-DD'), 1) "add months last" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

