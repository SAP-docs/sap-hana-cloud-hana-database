<!-- loiof4351278aade4ac3be7618181acd2ea4 -->

# CUME\_DIST Function \(Window\)

Returns the relative rank of a row.



<a name="loiof4351278aade4ac3be7618181acd2ea4__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
CUME_DIST() <window_specification>
```



<a name="loiof4351278aade4ac3be7618181acd2ea4__section_uqj_trk_d1b"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loiof4351278aade4ac3be7618181acd2ea4__sql_function_abs_1sql_function_abs_description"/>

## Description

Returns the relative rank of a row.

The relative rank of a row R is defined as NP/NR, where:

-   NP is defined to be the number of rows preceding or peer with R in the window ordering of the window partition of R.

-   NR is defined to be the number of rows in the window ordering of the window.




<a name="loiof4351278aade4ac3be7618181acd2ea4__sql_function_abs_1sql_function_abs_examples"/>

## Examples

```
CREATE ROW TABLE ProductSales (ProdName NVARCHAR(50), Description NVARCHAR(20), Sales INT);
INSERT INTO ProductSales VALUES('Tee Shirt','Plain',21);
INSERT INTO ProductSales VALUES ('Tee Shirt','Lettered',22);
INSERT INTO ProductSales VALUES ('Tee Shirt','Team logo',30);
INSERT INTO ProductSales VALUES('Hoodie','Plain',60);
INSERT INTO ProductSales VALUES ('Hoodie','Lettered',65);
INSERT INTO ProductSales VALUES ('Hoodie','Team logo',80);
INSERT INTO ProductSales VALUES('Ballcap','Plain',8);
INSERT INTO ProductSales VALUES ('Ballcap','Lettered',40);
INSERT INTO ProductSales VALUES ('Ballcap','Team logo',27);

SELECT ProdName, Description, Sales,
  PERCENT_RANK() OVER (ORDER BY Sales ASC) AS Percent_Rank,
  CUME_DIST() OVER (ORDER BY Sales ASC) AS Cume_Dist
FROM ProductSales
ORDER BY Sales DESC;
```


<table>
<tr>
<th valign="top">

PRODNAME



</th>
<th valign="top">

DESCRIPTION



</th>
<th valign="top">

SALES



</th>
<th valign="top">

PERCENT\_RANK



</th>
<th valign="top">

CUME\_DIST



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
<td valign="top">

1



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

0.875



</td>
<td valign="top">

0.8888888888888888



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

0.75



</td>
<td valign="top">

0.7777777777777778



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

0.625



</td>
<td valign="top">

0.6666666666666666



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

0.5



</td>
<td valign="top">

0.5555555555555556



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

0.375



</td>
<td valign="top">

0.4444444444444444



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

0.25



</td>
<td valign="top">

0.3333333333333333



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

0.125



</td>
<td valign="top">

0.2222222222222222



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
<td valign="top">

0.1111111111111111



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

