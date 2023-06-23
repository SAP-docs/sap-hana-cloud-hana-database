<!-- loio20da5fa8751910148969da2572b25ed8 -->

# ADD\_DAYS Function \(Datetime\)

Computes the specified date, plus or minus the specified number of days.



<a name="loio20da5fa8751910148969da2572b25ed8__sql_function_add_days_1sql_function_add_days_syntax"/>

## Syntax

```
ADD_DAYS(<date>, <num_days>)
```



## Syntax Elements


<dl>
<dt><b>

*<date\>*

</b></dt>
<dd>

Specifies the date to increment.



</dd><dt><b>

*<num\_days\>*

</b></dt>
<dd>

Specifies the number of days \(integer\). A positive integer increments the date by the specified amount; a negative integer decrements the date.



</dd>
</dl>



<a name="loio20da5fa8751910148969da2572b25ed8__sql_function_add_days_1sql_function_add_days_description"/>

## Description

Computes the specified date plus or minus the specified number of days.



<a name="loio20da5fa8751910148969da2572b25ed8__sql_function_add_days_1sql_function_add_days_examples"/>

## Example

The following example increments the date value ***2009-12-05*** by 30 days and returns the value ***2010-01-04***:

```
SELECT ADD_DAYS (TO_DATE ('2009-12-05', 'YYYY-MM-DD'), 30) "add days" FROM DUMMY;
```

The following example decrements the date value ***2009-12-05*** by 30 days and returns the value ***2009-11-05***:

```
SELECT ADD_DAYS (TO_DATE ('2009-12-05', 'YYYY-MM-DD'), -30) "subtract days" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

