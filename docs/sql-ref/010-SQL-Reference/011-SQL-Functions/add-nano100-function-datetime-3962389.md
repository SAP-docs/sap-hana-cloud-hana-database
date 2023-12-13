<!-- loio3962389a62b149b69d497bb25f4ec01a -->

# ADD\_NANO100 Function \(Datetime\)

Adds the specified number of 10^-7 unit of seconds to the specified TIMESTAMP value.



<a name="loio3962389a62b149b69d497bb25f4ec01a__section_gv2_glw_ccb"/>

## Syntax

```
ADD_NANO100( <time>, <num> )
```



<a name="loio3962389a62b149b69d497bb25f4ec01a__section_hv2_glw_ccb"/>

## Syntax Elements


<dl>
<dt><b>

*<time\>*

</b></dt>
<dd>

The TIMESTAMP value to add the units of seconds to.



</dd><dt><b>

*<num\>*

</b></dt>
<dd>

The number of 10^-7 unit of seconds to increment the TIMESTAMP value by.



</dd>
</dl>



<a name="loio3962389a62b149b69d497bb25f4ec01a__section_iv2_glw_ccb"/>

## Description

Computes the specified TIMESTAMP value plus the specified number of microseconds.



<a name="loio3962389a62b149b69d497bb25f4ec01a__section_jv2_glw_ccb"/>

## Example

The following example increments the TIMESTAMP value by `864000000000` microseconds and returns ***1000-01-02 10:00:00.0000000***:

```
SELECT ADD_NANO100(TO_TIMESTAMP('1000-01-01 10:00:00.0000000'), 864000000000) FROM DUMMY;
```

The following example increments the TIMESTAMP value by `1` microsecond and returns `1000-01-01 10:00:00.0000001`:

```
SELECT ADD_NANO100(TO_TIMESTAMP('1000-01-01 10:00:00.0000000'), 1) FROM DUMMY;
```

**Related Information**  


[ADD\_SECONDS Function \(Datetime\)](add-seconds-function-datetime-20da994.md "Computes the specified time plus the specified seconds.")

