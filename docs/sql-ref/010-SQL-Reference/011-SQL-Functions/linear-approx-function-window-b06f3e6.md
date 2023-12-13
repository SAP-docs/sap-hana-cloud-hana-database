<!-- loiob06f3e60d29e4968ab2da3cca7333db0 -->

# LINEAR\_APPROX Function \(Window\)

Operates on an entire series to produce a new series that replaces missing values by interpolating between adjacent non-NULL values and extrapolating any leading or trailing null values.



<a name="loiob06f3e60d29e4968ab2da3cca7333db0__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
LINEAR_APPROX(<expression> [, <ModeArgument> [, <Value1Argument> [,
    <Value2Argument>]]]) OVER ({ SERIES(...) [<window_partition_by_clause>]
    [<window_order_by_clause>] | [<window_partition_by_clause>] <window_order_by_clause>})

<expression> ::= <identifier>
```



<a name="loiob06f3e60d29e4968ab2da3cca7333db0__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

This parameter specifies the input data column.



</dd><dt><b>

*<ModeArgument\>*

</b></dt>
<dd>

This parameter defines the applied extrapolation mode. The table below lists the possible values for *<ModeArgument\>*.

```
<ModeArgument> ::= EXTRAPOLATION_NONE
    | EXTRAPOLATION_LINEAR
    | EXTRAPOLATION_CONSTANT
```


<table>
<tr>
<th valign="top">

**Mode**

</th>
<th valign="top">

**Description**

</th>
</tr>
<tr>
<td valign="top">

EXTRAPOLATION\_NONE

</td>
<td valign="top">

Prevents the extrapolation of leading and trailing nulls. Interpolation is performed on the values in the middle.

Default value if *<ModeArgument\>* is omitted.

You do not need to specify the *<Value1Argument\>* and *<Value2Argument\>* parameters when using this mode.

For example, an input of \[null, null, 1, 2, null, null, 5, null, null\] returns \[null, null, 1, 2, 3, 4, 5, null, null\].

</td>
</tr>
<tr>
<td valign="top">

EXTRAPOLATION\_LINEAR

</td>
<td valign="top">

Performs linear extrapolation where *<Value1Argument\>* is the minimum value and *<Value2Argument\>* is the maximum value.

During the extrapolation of leading and trailing nulls, this function checks that the extrapolation results are within range of the minimum and maximum values; otherwise, values are replaced by the minimum or maximum value, whichever is appropriate.

An exception is thrown if *<Value1Argument\>* is greater than *<Value2Argument\>*.

</td>
</tr>
<tr>
<td valign="top">

EXTRAPOLATION\_CONSTANT

</td>
<td valign="top">

Performs linear extrapolation where leading and trailing nulls values are replaced by the values specified by the *<Value1Argument\>* and *<Value2Argument\>* parameters, respectively.

When *<Value1Argument\>* is not specified or null, the first non-null value is used to replace leading null values. When *<Value2Argument\>* is not specified or null, the last non-null is used to replace trailing null values.

</td>
</tr>
</table>

Linear interpolation can be applied to all number types if they can be cast into a long double type, such as INT, LONG, DOUBLE, or FLOAT.



</dd><dt><b>

*<Value1Argument\>* and *<Value2Argument\>*

</b></dt>
<dd>

These parameters define arguments for the extrapolation and can be any numeric type.

```
<Value1Argument> ::= <identifier> 
<Value2Argument> ::= <identifier> 
```



</dd><dt><b>

*<table\_schema\>*

</b></dt>
<dd>

```
<table_schema> ::= [<schema_name>.]<table_name> 
<schema_name> ::= <unicode_name> 
<table_name> ::= <identifier>
```

*<table\_schema\>* must be a base table name and not a correlation name.



</dd><dt><b>

*<window\_order\_by\_clause\>*

</b></dt>
<dd>

Determines the sort order. This expression must not contain any NULL values or duplicates. See the syntax of this clause located in the *Window Functions* topic.



</dd>
</dl>



<a name="loiob06f3e60d29e4968ab2da3cca7333db0__sql_function_abs_1sql_function_abs_description"/>

## Description

Operates on an entire series to produce a new series that replaces missing values by interpolating between adjacent non-NULL values and extrapolating any leading or trailing null values.

When using this function, the input is assumed to be equidistant. The SERIES definition must be equidistant.

When only null values are contained in the input, only null values appear in the output unless the null values are replaced by an extrapolation via the EXTRAPOLATION\_CONSTANT mode.

When using the SERIES syntax, this function uses the properties in the following table to perform linear approximation.


<table>
<tr>
<th valign="top">

**Property**

</th>
<th valign="top">

**Description**

</th>
</tr>
<tr>
<td valign="top">

NON-EQUIDISTANT

</td>
<td valign="top">

An error occurs if the series is non-equidistant.

</td>
</tr>
<tr>
<td valign="top">

MISSING ELEMENTS ALLOWED

</td>
<td valign="top">

When specified, there must be exactly one ORDER BY column that is compatible with the type of the series period column and the INCREMENT BY value.

</td>
</tr>
<tr>
<td valign="top">

PARTITION BY

</td>
<td valign="top">

If not specified, the SERIES KEY property of the SERIES syntax is used to construct the default PARTITION BY.

</td>
</tr>
<tr>
<td valign="top">

ORDER BY

</td>
<td valign="top">

If not specified, the first PERIOD column is added as an ORDER BY.

</td>
</tr>
</table>

Other SERIES properties, such as MINVALUE and MAXVALUE, are ignored.



<a name="loiob06f3e60d29e4968ab2da3cca7333db0__sql_function_abs_1sql_function_abs_examples"/>

## Examples

**Linear approximation without a series definition**

If the SERIES definition were not specified in the example above, then the result would have been different. For the same SparseApproxTable, as populated above, the example below does not specify a series. The example below returns \[-1, 0, 1, 2, 3, 4, 5, 6\].

```
SELECT LINEAR_APPROX(val, 'EXTRAPOLATION_LINEAR') OVER (PARTITION BY ts_id ORDER BY DATE) AS approximated_value 
 FROM "SparseApproxTable";
```

In the example query above, the series is assumed to be dense and equidistant, so the date column is not taken into consideration when calculating the approximations.

**Linear approximation of sparse series data**

In the example below, the INCREMENT BY INTERVAL is set to 1 MONTH, meaning that at most one row is expected for each month. Apart from the null values, values are missing for several months in the table. The LINEAR\_APPROX function always replaces the null values and does not insert new lines for missing values. However, if the SERIES definition is specified in the SELECT statement, then LINEAR\_APPROX considers the missing months when calculating the slope between two non-null values.

```
CREATE COLUMN TABLE "SparseApproxTable" (ts_id NVARCHAR(20), date DAYDATE, val DOUBLE);

INSERT INTO "SparseApproxTable" VALUES('A','2013-11-01', null);
INSERT INTO "SparseApproxTable" VALUES('A','2014-01-01', null);
INSERT INTO "SparseApproxTable" VALUES('A','2014-02-05', 2);
INSERT INTO "SparseApproxTable" VALUES('A','2014-03-07', null);
INSERT INTO "SparseApproxTable" VALUES('A','2014-05-01', 5);
INSERT INTO "SparseApproxTable" VALUES('A','2014-07-27', 7);
INSERT INTO "SparseApproxTable" VALUES('A','2014-12-07', null);
INSERT INTO "SparseApproxTable" VALUES('A','2015-02-07', null);

SELECT LINEAR_APPROX(val, 'EXTRAPOLATION_LINEAR') OVER (SERIES (
    SERIES KEY(ts_id) EQUIDISTANT INCREMENT BY INTERVAL 1 MONTH
    MISSING ELEMENTS ALLOWED PERIOD FOR SERIES(date)) 
  PARTITION BY ts_id) AS approximated_value 
 FROM "SparseApproxTable";
```


<table>
<tr>
<th valign="top">

APPROXIMATED\_VALUE

</th>
</tr>
<tr>
<td valign="top">

\-1

</td>
</tr>
<tr>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

7

</td>
</tr>
<tr>
<td valign="top">

9.666666666666666

</td>
</tr>
<tr>
<td valign="top">

11

</td>
</tr>
</table>

**Linear approximation of series data**

```
CREATE COLUMN TABLE "InterpolationTable" (TS_ID NVARCHAR(20), date DAYDATE, val DOUBLE);
INSERT INTO "InterpolationTable" VALUES('A','2013-09-30', 1);
INSERT INTO "InterpolationTable" VALUES('A','2013-10-01', 2);
INSERT INTO "InterpolationTable" VALUES('A','2013-10-02', null);
INSERT INTO "InterpolationTable" VALUES('A','2013-10-03', 10);

SELECT date, 
  val, 
  LINEAR_APPROX (val, 'EXTRAPOLATION_LINEAR') OVER (PARTITION BY TS_ID ORDER BY date) AS LINEAR_APPROX
 FROM "InterpolationTable";
```


<table>
<tr>
<th valign="top">

DATE

</th>
<th valign="top">

VAL

</th>
<th valign="top">

MYRESULT

</th>
</tr>
<tr>
<td valign="top">

Sep 30, 2013

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Oct 1, 2013

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

Oct 2, 2013

</td>
<td valign="top">

?

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

Oct 3, 2013

</td>
<td valign="top">

10

</td>
<td valign="top">

10

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

