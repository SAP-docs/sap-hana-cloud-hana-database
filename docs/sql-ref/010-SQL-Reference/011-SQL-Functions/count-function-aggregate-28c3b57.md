<!-- loio28c3b573c4354f75a1931202e2271d7c -->

# COUNT Function \(Aggregate\)

Counts the number of rows returned by a query. This function can also be used as a window function.



<a name="loio28c3b573c4354f75a1931202e2271d7c__section_xrt_wxc_mfb"/>

## Syntax

**Aggregate function:**

```
COUNT (*)
 | COUNT ( [ ALL ] <expression> )
 | COUNT ( DISTINCT <expression_list>
```

**Window function:**

```
COUNT (*) [ <window_specification> ]
 | COUNT ( [ ALL ] <expression> ) [ <window_specification> ]
 | COUNT ( DISTINCT <expression> ) [ <window_specification> ]
```



<a name="loio28c3b573c4354f75a1931202e2271d7c__section_yrt_wxc_mfb"/>

## Syntax Elements


<dl>
<dt><b>

\*

</b></dt>
<dd>

Returns the number of rows returned by the query, regardless of the value of those rows, and including duplicate values.



</dd><dt><b>

ALL

</b></dt>
<dd>

Optional keyword reflecting the default behavior. That is, ***COUNT\(ALL *<expression\>*\)*** and ***COUNT\(*<expression\>*\)*** return the same result.



</dd><dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies the input data for the function. The function returns the number of non-NULL values for the specified expression returned by the query, including duplicate values \(unless DISTINCT is also specified\).



</dd><dt><b>

*<expression\_list\>*

</b></dt>
<dd>

Specifies the input data for the function as a comma-separated list of *<expression\>*. *<expression\_list\>* is only supported for use with the DISTINCT clause.

```
<expression_list>::= <expression> [, <expression> [,…] ]
```



</dd><dt><b>

DISTINCT

</b></dt>
<dd>

Returns the number of distinct values returned by the query, excluding rows with all NULL values for that expression.



</dd><dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For syntax, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio28c3b573c4354f75a1931202e2271d7c__section_nst_wxc_mfb"/>

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

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
<td valign="top">

`BIGINT`



</td>
</tr>
</table>



<a name="loio28c3b573c4354f75a1931202e2271d7c__section_r1g_2vq_mfb"/>

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

The following example returns ***5***, the number of rows in the MyProducts table:

```
SELECT COUNT(*) FROM "MyProducts";
```

The following example returns ***2***, the number of rows with distinct values in the Category column:

```
SELECT COUNT(DISTINCT "Category") FROM "MyProducts";
```

**Related Information**  


[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[Window Aggregate Functions](window-aggregate-functions-ee3c26a.md "Some aggregate functions can be used as window functions over a window specification.")

[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

