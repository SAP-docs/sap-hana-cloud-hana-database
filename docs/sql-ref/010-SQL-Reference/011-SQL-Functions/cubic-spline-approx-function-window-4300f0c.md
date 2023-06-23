<!-- loio4300f0ccdf024a11a40a82615832e430 -->

# CUBIC\_SPLINE\_APPROX Function \(Window\)

Replaces null values by interpolating the gaps based on calculated cubic splines and linearly extrapolating any leading or trailing null values.



<a name="loio4300f0ccdf024a11a40a82615832e430__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
CUBIC_SPLINE_APPROX ( <expression> [, <BoundaryConditionArgument> [, <ExtrapolationModeArgument> [, <Value1Argument> [, <Value2Argument> ] ] ] ] ) 
 [ OVER ( {
     SERIES(...) [ PARTITION BY <col1> [,...] [ <window_order_by_clause> ]
   | [ PARTITION BY <col1>[,...] <window_order_by_clause>
     } ) ]
```



<a name="loio4300f0ccdf024a11a40a82615832e430__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the input data expression



</dd><dt><b>

*<BoundaryConditionArgument\>*

</b></dt>
<dd>

Specifies the boundary conditions that are used for the cubic spline calculation. The default value is SPLINE\_TYPE\_NATURAL. If this parameter is omitted, then natural boundary conditions are used to calculate the interpolating cubic splines.

```
<BoundaryConditionArgument> ::= SPLINE_TYPE_NATURAL | SPLINE_TYPE_NOT_A_KNOT
```



</dd><dt><b>

*<ExtrapolationModeArgument\>*

</b></dt>
<dd>

Defines the applied extrapolation mode. The default value is EXTRAPOLATION\_NONE, which indicates that extrapolation does not occur if this parameter is omitted.

```
<ExtrapolationModeArgument> ::= EXTRAPOLATION_NONE
 | EXTRAPOLATION_LINEAR
 | EXTRAPOLATION_CONSTANT
```

The definition, default value, and use of ExtrapolationModeArgument in conjunction with the Value1Argument and Value2Argument is identical to the LINEAR\_APPROX function except from the calculation of the slope.

When using EXTRAPOLATION\_LINEAR mode, the slope of the extrapolation line is set equal to the slope of the calculated cubic splines at the boundary points. For example, the slope of the calculated spline at the first non-null value is taken as the slope of the extrapolating line for leading nulls. Similarly, the slope of the calculated spline at the last non-null value is taken as the slope of the extrapolating line for trailing nulls.

Cubic spline interpolation can be applied to all number types that can be cast into long double type, such as INT, LONG, DOUBLE, or FLOAT.



</dd><dt><b>

*<window\_order\_by\_clause\>*

</b></dt>
<dd>

Determines the sort order. This expression must not contain any NULL values or duplicates. See the syntax of this clause located in the *Window Functions* topic.



</dd>
</dl>



<a name="loio4300f0ccdf024a11a40a82615832e430__sql_function_abs_1sql_function_abs_description"/>

## Description

Replaces null values by interpolating the gaps based on calculated cubic splines and linearly extrapolating any leading or trailing null values.



<a name="loio4300f0ccdf024a11a40a82615832e430__sql_function_abs_1sql_function_abs_examples"/>

## Examples

**Natural cubic spline interpolation**

Perform natural cubic spline interpolation:

```
SELECT CUBIC_SPLINE_APPROX(temperature, 'SPLINE_TYPE_NATURAL') OVER (PARTITION BY station ORDER BY ts) 
  FROM WEATHER;
```

For natural boundary conditions, the BoundaryConditionArgument can be omitted. The following query returns identical results to the above one:

```
SELECT CUBIC_SPLINE_APPROX(temperature)
    OVER(PARTITION BY station ORDER BY ts) FROM WEATHER;
```

Perform cubic spline interpolation by using not-a-knot boundary conditions:

```
SELECT CUBIC_SPLINE_APPROX(temperature, 'SPLINE_TYPE_NOT_A_KNOT')
    OVER(PARTITION BY station ORDER BY ts) FROM WEATHER;
```

This example performs linear extrapolation on a series.

```
SELECT date, val, LINEAR_APPROX(val, 'EXTRAPOLATION_LINEAR') OVER(
    SERIES(SERIES KEY(ts_id) PERIOD FOR SERIES(date)
        EQUIDISTANT INCREMENT BY INTERVAL 1 DAY MISSING ELEMENTS ALLOWED))
    FROM InterpolationTable;
```

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

