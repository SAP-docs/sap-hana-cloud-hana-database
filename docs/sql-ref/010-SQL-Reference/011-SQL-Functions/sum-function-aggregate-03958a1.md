<!-- loio03958a1eb0ad4950b00dedd8fdda475a -->

# SUM Function \(Aggregate\)

Returns the sum of the expression. This function can also be used as a window function.



<a name="loio03958a1eb0ad4950b00dedd8fdda475a__section_xrt_wxc_mfb"/>

## Syntax

**Aggregate function:**

```
SUM( [ ALL | DISTINCT ] <expression> )
```

**Window function:**

```
SUM( <expression> ) <window_specification>
```



<a name="loio03958a1eb0ad4950b00dedd8fdda475a__section_yrt_wxc_mfb"/>

## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the input data for the function.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio03958a1eb0ad4950b00dedd8fdda475a__section_nst_wxc_mfb"/>

## Description

**Result type based on input**


<table>
<tr>
<th valign="top">

**`TINYINT`**

</th>
<th valign="top">

**`SMALLINT`**

</th>
<th valign="top">

**`INTEGER`**

</th>
<th valign="top">

**`BIGINT`**

</th>
<th valign="top">

**`DECIMAL(p,s)`**

</th>
<th valign="top">

**`DECIMAL`**

</th>
<th valign="top">

**`REAL`**

</th>
<th valign="top">

**`DOUBLE`**

</th>
</tr>
<tr>
<td valign="top">

`INTEGER`

</td>
<td valign="top">

`INTEGER`

</td>
<td valign="top">

`INTEGER`

</td>
<td valign="top">

`BIGINT`

</td>
<td valign="top">

`DECIMAL(p,s)` \*

</td>
<td valign="top">

`DECIMAL`

</td>
<td valign="top">

`REAL`

</td>
<td valign="top">

`DOUBLE`

</td>
</tr>
</table>



<a name="loio03958a1eb0ad4950b00dedd8fdda475a__section_r1g_2vq_mfb"/>

## Example

The following statements create a table with data for example purposes:

```
DROP TABLE "MyProducts";
CREATE COLUMN TABLE "MyProducts"(
  "Product_ID" NVARCHAR(10),
  "Product_Name" NVARCHAR(100),
  "Category" NVARCHAR(100),
  "Quantity" INTEGER,
  "Price" DECIMAL(10,2),
  PRIMARY KEY ("Product_ID") );
				
INSERT INTO "MyProducts" VALUES('P1','Shirts', 'Clothes', 32, 20.99);
INSERT INTO "MyProducts" VALUES('P2','Jackets', 'Clothes', 16, 99.49);
INSERT INTO "MyProducts" VALUES('P3','Trousers', 'Clothes', 30, 32.99);
INSERT INTO "MyProducts" VALUES('P4','Coats', 'Clothes', 5, 129.99);
INSERT INTO "MyProducts" VALUES('P5','Purse', 'Accessories', 3, 89.49);
```

The following example sums the quantities of coats and jackets, and returns the value 21:

```
SELECT SUM("Quantity") FROM "MyProducts" WHERE "Product_Name" IN ('Jackets', 'Coats');
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

