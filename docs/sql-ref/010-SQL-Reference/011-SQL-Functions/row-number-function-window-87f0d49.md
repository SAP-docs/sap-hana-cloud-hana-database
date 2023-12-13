<!-- loio87f0d4985c4a49bfb64682dcb325173d -->

# ROW\_NUMBER Function \(Window\)

Sequentially numbers the rows within a partition of a result set, with the first row of each partition assigned as 1.



<a name="loio87f0d4985c4a49bfb64682dcb325173d__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
ROW_NUMBER() <window_specification>
```



<a name="loio87f0d4985c4a49bfb64682dcb325173d__section_x35_bdq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio87f0d4985c4a49bfb64682dcb325173d__sql_function_abs_1sql_function_abs_description"/>

## Description

The output of the ROW\_NUMBER function can be non-deterministic among tie values. The ordering of the sequence is determined by the *<windows\_order\_by\_clause\>* within the OVER windows clause.



<a name="loio87f0d4985c4a49bfb64682dcb325173d__sql_function_abs_1sql_function_abs_examples"/>

## Examples

The following example returns the sales figures sorted in descending number by product type. The data is partitioned by the product name, and the row number is returned for each type within its product.

```
CREATE ROW TABLE ProductSales (ProdName NVARCHAR(50), Type NVARCHAR(20), Sales INT);
INSERT INTO ProductSales VALUES('Tee Shirt','Plain',21);
INSERT INTO ProductSales VALUES ('Tee Shirt','Lettered',22);
INSERT INTO ProductSales VALUES ('Tee Shirt','Team logo',30);
INSERT INTO ProductSales VALUES('Hoodie','Plain',60);
INSERT INTO ProductSales VALUES ('Hoodie','Lettered',65);
INSERT INTO ProductSales VALUES ('Hoodie','Team logo',80);
INSERT INTO ProductSales VALUES('Ballcap','Plain',8);
INSERT INTO ProductSales VALUES ('Ballcap','Lettered',40);
INSERT INTO ProductSales VALUES ('Ballcap','Team logo',27);

SELECT ProdName, Type, Sales,
  ROW_NUMBER() OVER (PARTITION BY ProdName ORDER BY Sales DESC) AS row_num
FROM ProductSales
ORDER BY ProdName, Sales DESC;

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

ROW\_NUM

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
</table>

In the following example, the ROW\_NUM values for the items are different because there is no *<windows\_order\_by\_clause\>* specification:

```
SELECT ProdName, Type, Sales,
  ROW_NUMBER() OVER (PARTITION BY ProdName) AS row_num
FROM ProductSales
ORDER BY ProdName, Sales DESC;

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

ROW\_NUM

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

Team logo

</td>
<td valign="top">

27

</td>
<td valign="top">

3

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

1

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

3

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

3

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

1

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

