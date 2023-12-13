<!-- loio90f4533f07d34269a47924c963f1d5ec -->

# PERCENT\_RANK Function \(Window\)

Calculates the percentage of values that are either less than or greater than the current value, per the ORDER BY specification for the window.



<a name="loio90f4533f07d34269a47924c963f1d5ec__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
PERCENT_RANK() <window_specification>
```



<a name="loio90f4533f07d34269a47924c963f1d5ec__section_fsc_rcq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio90f4533f07d34269a47924c963f1d5ec__sql_function_abs_1sql_function_abs_description"/>

## Description

For any row in group of rows in a result set, PERCENT\_RANK calculates the percentage of values that are either less than or greater than the current value, per the ORDER BY specification for the window.

PERCENT\_RANK returns \(fractional\) integers starting at 0 and ending with 1, as defined by the sort order \(ASC or DESC\) in the ORDER BY clause.

The relative rank of a row R is defined as \(RANK\(\)-1\)/\(NR-1\), where NR is defined to be the number of rows in the window partition of R.



<a name="loio90f4533f07d34269a47924c963f1d5ec__sql_function_abs_1sql_function_abs_examples"/>

## Examples

In the this example, the rows are partitioned by ProdName, creating a group of rows for each product name. For each row, the PERCENT\_RANK column expresses the rank of the sales value for that row as a percentage. Specifically, because ORDER BY \(Sales ASC\) is specified, PERCENT\_RANK returns the percentage of values in the same group that have a lower value.

```
CREATE ROW TABLE ProductSales (ProdName NVARCHAR(50), Type NVARCHAR(20), Sales INT);
INSERT INTO ProductSales VALUES('Tee Shirt','Plain',21);
INSERT INTO ProductSales VALUES('Tee Shirt','Lettered',22);
INSERT INTO ProductSales VALUES('Tee Shirt','Team logo',30);
INSERT INTO ProductSales VALUES('Hoodie','Plain',60);
INSERT INTO ProductSales VALUES('Hoodie','Lettered',65);
INSERT INTO ProductSales VALUES('Hoodie','Team logo',80);
INSERT INTO ProductSales VALUES('Hoodie','Vintage',67);
INSERT INTO ProductSales VALUES('Ballcap','Plain',8);
INSERT INTO ProductSales VALUES('Ballcap','Lettered',40);
INSERT INTO ProductSales VALUES('Ballcap','Team logo',27);

SELECT ProdName, Type, Sales,
  PERCENT_RANK() OVER (PARTITION BY ProdName ORDER BY Sales ASC) AS Percent_Rank
FROM ProductSales
ORDER BY Sales DESC;
```


<table>
<tr>
<th valign="top">

PRODNAME

</th>
<th valign="top">

Type

</th>
<th valign="top">

SALES

</th>
<th valign="top">

PERCENT\_RANK

</th>
</tr>
<tr>
<td valign="top">

Hoodie

</td>
<td valign="top">

Team logo

</td>
<td valign="top">

80

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Hoodie

</td>
<td valign="top">

Vintage

</td>
<td valign="top">

67

</td>
<td valign="top">

0.6666666666666666

</td>
</tr>
<tr>
<td valign="top">

Hoodie

</td>
<td valign="top">

Lettered

</td>
<td valign="top">

65

</td>
<td valign="top">

0.3333333333333333

</td>
</tr>
<tr>
<td valign="top">

Hoodie

</td>
<td valign="top">

Plain

</td>
<td valign="top">

60

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Ballcap

</td>
<td valign="top">

Lettered

</td>
<td valign="top">

40

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Tee Shirt

</td>
<td valign="top">

Team logo

</td>
<td valign="top">

30

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

Ballcap

</td>
<td valign="top">

Team logo

</td>
<td valign="top">

27

</td>
<td valign="top">

0.5

</td>
</tr>
<tr>
<td valign="top">

Tee Shirt

</td>
<td valign="top">

Lettered

</td>
<td valign="top">

22

</td>
<td valign="top">

0.5

</td>
</tr>
<tr>
<td valign="top">

Tee Shirt

</td>
<td valign="top">

Plain

</td>
<td valign="top">

21

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

Ballcap

</td>
<td valign="top">

Plain

</td>
<td valign="top">

8

</td>
<td valign="top">

0

</td>
</tr>
</table>

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[RANK Function \(Window\)](rank-function-window-10bb583.md "Returns rank of a row within a partition, starting from 1.")

