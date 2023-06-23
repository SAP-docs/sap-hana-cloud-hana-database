<!-- loio20da994e75191014a6e4bf620c179299 -->

# ADD\_SECONDS Function \(Datetime\)

Computes the specified time plus the specified seconds.



<a name="loio20da994e75191014a6e4bf620c179299__sql_function_add_seconds_1sql_function_add_seconds_syntax"/>

## Syntax

```
ADD_SECONDS(<time>, <num_seconds>)
```



## Syntax Elements


<dl>
<dt><b>

*<time\>*

</b></dt>
<dd>

The time that is incremented.



</dd><dt><b>

*<num\_seconds\>*

</b></dt>
<dd>

The number of seconds to increment the time by. Fractional values are supported for milliseconds and microseconds:

-   1/1000 – milliseconds

-   1/1000000 - microseconds




</dd>
</dl>



<a name="loio20da994e75191014a6e4bf620c179299__sql_function_add_seconds_1sql_function_add_seconds_description"/>

## Description

Computes the specified time plus the number of specified seconds.



<a name="loio20da994e75191014a6e4bf620c179299__sql_function_add_seconds_1sql_function_add_seconds_examples"/>

## Example

The example increments the TIMESTAMP ***2012-01-01 23:30:45*** by ***60\*30*** seconds, and returns the value ***2012-01-02 00:00:45.0***:

```
SELECT ADD_SECONDS (TO_TIMESTAMP ('2012-01-01 23:30:45'), 60*30) "add seconds" FROM DUMMY;
```

**Related Information**  


[Datetime Data Types](../datetime-data-types-3f81ccc.md "Datetime data types are used to store date and time information.")

[ADD\_NANO100 Function \(Datetime\)](add-nano100-function-datetime-3962389.md "Adds the specified number of 10^-7 unit of seconds to the specified TIMESTAMP value.")

