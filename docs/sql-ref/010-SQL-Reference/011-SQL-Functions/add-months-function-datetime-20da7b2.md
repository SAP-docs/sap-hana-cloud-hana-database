<!-- loio20da7b237519101489f3e2e1a284355a -->

# ADD\_MONTHS Function \(Datetime\)

Computes the specified date plus the specified number of months.



<a name="loio20da7b237519101489f3e2e1a284355a__sql_function_add_months_1sql_function_add_months_syntax"/>

## Syntax

```
ADD_MONTHS(<date>, <num_months>)
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



<a name="loio20da7b237519101489f3e2e1a284355a__sql_function_add_months_1sql_function_add_months_description"/>

## Description

Computes the specified date plus the specified number of months.

To compute the date so that the output date is set to the last day of the month when the input date is the last day of the month, use the ADD\_MONTHS\_LAST function.

The parameter *<date\>* must be implicitly or explicitly converted to one of the following SQL data types:

-   DATE
-   TIMESTAMP
-   SECONDDATE

The SQL data type of the output parameters is the same as the SQL data type of the input parameters. For example, ADD\_MONTHS\_LAST\(DATE\) returns a date, while ADD\_MONTHS\_LAST\(TIMESTAMP\) returns a timestamp.



<a name="loio20da7b237519101489f3e2e1a284355a__sql_function_add_months_1sql_function_add_months_examples"/>

## Example

The following example increments the date 2009-12-05 by one month, and returns the value 2010-01-05:

```
SELECT ADD_MONTHS (TO_DATE ('2009-12-05', 'YYYY-MM-DD'), 1) "add months" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

