<!-- loio20e21cfd75191014a5cbbea031962073 -->

# GROUPING\_ID Function \(Miscellaneous\)

Returns an integer value to identify which grouping set each row belongs to.



<a name="loio20e21cfd75191014a5cbbea031962073__sql_function_grouping_id_1sql_function_grouping_id_syntax"/>

## Syntax

```
GROUPING_ID(<column_name_list>)
```



<a name="loio20e21cfd75191014a5cbbea031962073__sql_function_grouping_id_1sql_function_grouping_id_description"/>

## Description

The GROUPING\_ID function can be used with GROUPING SETS, ROLLUP, or CUBE, which return multiple levels of aggregation in a single result set. . GROUPING\_ID returns an integer value to identify which grouping set each row belongs to. Each column in GROUPING\_ID must be an element of GROUPING SETS.

GROUPING\_ID is assigned by converting the bit vector generated from GROUPING SETS to a decimal number by treating the bit vector as a binary number. When a bit vector is composed, 0 is assigned to each column specified in the GROUPING SETS and 1 otherwise in the order it appears in GROUPING SETS. By treating the bit vector as a binary number, this function returns an integer value as the output.



<a name="loio20e21cfd75191014a5cbbea031962073__sql_function_grouping_id_1sql_function_grouping_id_examples"/>

## Example

The following statement uses the fictitious table guided\_navi\_tab and the results indicates which grouping set each row belongs to:

```
SELECT customer, year, product, SUM(sales), 
   GROUPING_ID(customer, year, product)
   FROM guided_navi_tab
   GROUP BY GROUPING SETS (
    (customer, year, product),
    (customer, year),
    (customer, product),
    (year, product),
    (customer),
    (year),
    (product));
```


<table>
<tr>
<th valign="top">

CUSTOMER

</th>
<th valign="top">

YEAR

</th>
<th valign="top">

PRODUCT

</th>
<th valign="top">

SUM\(SALES\)

</th>
<th valign="top">

GROUPING\_ID\(CUSTOMER,YEAR,PRODUCT\),

</th>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2009

</td>
<td valign="top">

P1

</td>
<td valign="top">

100

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2010

</td>
<td valign="top">

P1

</td>
<td valign="top">

50

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2009

</td>
<td valign="top">

P1

</td>
<td valign="top">

200

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2010

</td>
<td valign="top">

P1

</td>
<td valign="top">

100

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2009

</td>
<td valign="top">

P2

</td>
<td valign="top">

200

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2010

</td>
<td valign="top">

P2

</td>
<td valign="top">

150

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2009

</td>
<td valign="top">

P2

</td>
<td valign="top">

300

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2010

</td>
<td valign="top">

P2

</td>
<td valign="top">

150

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2009

</td>
<td valign="top">

a

</td>
<td valign="top">

300

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

2010

</td>
<td valign="top">

a

</td>
<td valign="top">

200

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2009

</td>
<td valign="top">

a

</td>
<td valign="top">

500

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

2010

</td>
<td valign="top">

a

</td>
<td valign="top">

250

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

a

</td>
<td valign="top">

P1

</td>
<td valign="top">

150

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

a

</td>
<td valign="top">

P1

</td>
<td valign="top">

300

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

a

</td>
<td valign="top">

P2

</td>
<td valign="top">

350

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

a

</td>
<td valign="top">

P2

</td>
<td valign="top">

450

</td>
<td valign="top">

2

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2009

</td>
<td valign="top">

P1

</td>
<td valign="top">

300

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2010

</td>
<td valign="top">

P1

</td>
<td valign="top">

150

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2009

</td>
<td valign="top">

P2

</td>
<td valign="top">

500

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2010

</td>
<td valign="top">

P2

</td>
<td valign="top">

300

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

C1

</td>
<td valign="top">

a

</td>
<td valign="top">

a

</td>
<td valign="top">

500

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

C2

</td>
<td valign="top">

a

</td>
<td valign="top">

a

</td>
<td valign="top">

750

</td>
<td valign="top">

3

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2009

</td>
<td valign="top">

a

</td>
<td valign="top">

800

</td>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

2010

</td>
<td valign="top">

a

</td>
<td valign="top">

450

</td>
<td valign="top">

5

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

a

</td>
<td valign="top">

P1

</td>
<td valign="top">

450

</td>
<td valign="top">

6

</td>
</tr>
<tr>
<td valign="top">

a

</td>
<td valign="top">

a

</td>
<td valign="top">

P2

</td>
<td valign="top">

800

</td>
<td valign="top">

6

</td>
</tr>
</table>

