<!-- loio21a8eb1267d549c6a3eb0e15f82943e6 -->

# VAR Function \(Aggregate\)

Returns the variance of the given expression as the square of the standard deviation. This function can also be used as a window function.



<a name="loio21a8eb1267d549c6a3eb0e15f82943e6__section_xrt_wxc_mfb"/>

## Syntax

**Aggregate function:**

```
VAR( [ ALL | DISTINCT ] <expression> )
```

**Window function:**

```
VAR( <expression> ) <window_specification>
```



<a name="loio21a8eb1267d549c6a3eb0e15f82943e6__section_yrt_wxc_mfb"/>

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



<a name="loio21a8eb1267d549c6a3eb0e15f82943e6__section_nst_wxc_mfb"/>

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

`DECIMAL(9,6)`

</td>
<td valign="top">

`DECIMAL(11,6)`

</td>
<td valign="top">

`DECIMAL(16,6)`

</td>
<td valign="top">

`DECIMAL(25,6)`

</td>
<td valign="top">

`DECIMAL(p',s)`

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

> ### Note:  
> For DECIMAL\(p, s\), the result type DECIMAL\(p', s\) adheres to the following precision rules:
> 
> -   p' = 18, if p ≤ 18
> 
> -   p' = 28, if 18 < p ≤ 28
> 
> -   p' = 38, if 28 < p ≤ 38



<a name="loio21a8eb1267d549c6a3eb0e15f82943e6__section_r1g_2vq_mfb"/>

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

The following example returns ***2128.67***, the variance of values in the Price column:

```
SELECT VAR("Price") FROM "MyProducts";
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[VAR\_POP Function \(Aggregate\)](var-pop-function-aggregate-4faac7b.md "Returns the population variance of an expression.")

[VAR\_SAMP Function \(Aggregate\)](var-samp-function-aggregate-d1e36df.md "Returns the sample variance of an expression.")

