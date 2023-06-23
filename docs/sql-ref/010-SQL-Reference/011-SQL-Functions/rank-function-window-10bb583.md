<!-- loio10bb583b586e47a09790eb8f8eeeab62 -->

# RANK Function \(Window\)

Returns rank of a row within a partition, starting from 1.



<a name="loio10bb583b586e47a09790eb8f8eeeab62__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
RANK() <window_specification>
```



<a name="loio10bb583b586e47a09790eb8f8eeeab62__section_vmr_ycq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio10bb583b586e47a09790eb8f8eeeab62__sql_function_abs_1sql_function_abs_description"/>

## Description

The RANK function returns duplicate values in the ranking sequence when there are ties between values and the next rankings are skipped.



<a name="loio10bb583b586e47a09790eb8f8eeeab62__sql_function_abs_1sql_function_abs_examples"/>

## Examples

In this example, the data is partitioned by the product name, and the sales of types within the products are ranked. The plain ballcap is ranked 4 instead of 3 because of the sales numbers for the team logo and lettered versions of the ballcap, which are tied at rank 2.

```
CREATE ROW TABLE ProductSales (ProdName NVARCHAR(50), Type NVARCHAR(20), Sales INT);
INSERT INTO ProductSales VALUES('Tee Shirt','Plain',21);
INSERT INTO ProductSales VALUES('Tee Shirt','Lettered',22);
INSERT INTO ProductSales VALUES('Tee Shirt','Team logo',30);
INSERT INTO ProductSales VALUES('Hoodie','Plain',60);
INSERT INTO ProductSales VALUES('Hoodie','Lettered',65);
INSERT INTO ProductSales VALUES('Hoodie','Team logo',80);
INSERT INTO ProductSales VALUES('Ballcap','Vintage',60);
INSERT INTO ProductSales VALUES('Ballcap','Plain',8);
INSERT INTO ProductSales VALUES('Ballcap','Lettered',40);
INSERT INTO ProductSales VALUES('Ballcap','Team logo',40);

SELECT ProdName, Type, Sales,
RANK() OVER ( PARTITION BY ProdName ORDER BY Sales DESC ) AS Rank
FROM ProductSales
ORDER BY ProdName, Type;
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

RANK



</th>
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

2



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

4



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

40



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

Ballcap



</td>
<td valign="top">

Vintage



</td>
<td valign="top">

60



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

2



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

3



</td>
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

Tee Shirt



</td>
<td valign="top">

Lettered



</td>
<td valign="top">

22



</td>
<td valign="top">

2



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

3



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
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

