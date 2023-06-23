<!-- loio20dab50375191014bd8fe42e781bdaa0 -->

# ADD\_YEARS Function \(Datetime\)

Computes the specified date plus the specified years.



<a name="loio20dab50375191014bd8fe42e781bdaa0__sql_function_add_years_1sql_function_add_years_syntax"/>

## Syntax

```
ADD_YEARS(<date>, <num_years>)
```



## Syntax Elements


<dl>
<dt><b>

*<date\>*

</b></dt>
<dd>

The date that is incremented.



</dd><dt><b>

*<num\_years\>*

</b></dt>
<dd>

The number of years by which to increment the date.



</dd>
</dl>



<a name="loio20dab50375191014bd8fe42e781bdaa0__sql_function_add_years_1sql_function_add_years_description"/>

## Description

Computes the specified date plus the specified number of years.



<a name="loio20dab50375191014bd8fe42e781bdaa0__sql_function_add_years_1sql_function_add_years_examples"/>

## Example

The following example increments the specified date value ***2009-12-05*** by ***1*** year, and returns the value ***2010-12-05***:

```
SELECT ADD_YEARS (TO_DATE ('2009-12-05', 'YYYY-MM-DD'), 1) "add years" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

