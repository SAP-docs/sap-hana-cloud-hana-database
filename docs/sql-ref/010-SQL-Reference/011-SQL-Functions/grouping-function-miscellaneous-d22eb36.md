<!-- loiod22eb360d2951014b6f0b9f1e84edce9 -->

# GROUPING Function \(Miscellaneous\)

Determines whether a specified column is used in grouping.



<a name="loiod22eb360d2951014b6f0b9f1e84edce9__sql_function_grouping_1sql_function_grouping_syntax"/>

## Syntax

```
GROUPING(<column_name>)
```



<a name="loiod22eb360d2951014b6f0b9f1e84edce9__sql_function_grouping_1sql_function_grouping_description"/>

## Description

The GROUPING function can be used with GROUPING SETS, ROLLUP, or CUBE, which return multiple levels of aggregation in a single result set. The function returns 1 if the specified column is used in aggregation, and 0 otherwise. The column of GROUPING must be an element of the GROUPING SETS.



<a name="loiod22eb360d2951014b6f0b9f1e84edce9__section_clq_hpb_ccb"/>

## Example

```
CREATE COLUMN TABLE mySchema.Customers (
 cust_id INTEGER NOT NULL,
 cust_name NVARCHAR(20),
 num_emp INTEGER,
 region NVARCHAR(20),
 s_tier NVARCHAR(20),
 PRIMARY KEY ("CUST_ID")
 );
 
INSERT INTO mySchema.Customers VALUES( 1, 'CustA', 5, 'NorthEast', 'gold' );
INSERT INTO mySchema.Customers VALUES( 2, 'CustB', 26, 'NorthWest', 'gold' );
INSERT INTO mySchema.Customers VALUES( 3, 'CustC', 250, 'NorthEast', 'silver' );
INSERT INTO mySchema.Customers VALUES( 4, 'CustD', 180, 'SouthEast', 'platinum' );
INSERT INTO mySchema.Customers VALUES( 5, 'CustE', 32, 'SouthWest', 'silver' );
INSERT INTO mySchema.Customers VALUES( 6, 'CustF', 45, 'NorthEast', 'platinum' );
INSERT INTO mySchema.Customers VALUES( 7, 'CustG', 15, 'NorthWest', 'platinum' );
INSERT INTO mySchema.Customers VALUES( 8, 'CustH', 99, 'SouthEast', 'gold' );
INSERT INTO mySchema.Customers VALUES( 9, 'CustI', 6, 'NorthEast', 'silver' );
INSERT INTO mySchema.Customers VALUES( 10,'CustJ', 101, 'NorthEast', 'silver' );
INSERT INTO mySchema.Customers VALUES( 11,'Custk', 108, 'SouthEast', 'silver' );

SELECT cust_name AS "cust_name", cust_id AS "cust_id", region AS "region", s_tier AS "s_tier", num_emp AS "num_emp", 
GROUPING (region) AS "gr_reg", GROUPING (s_tier) AS "gr_tier", GROUPING (num_emp) AS "gr_num"
FROM mySchema.Customers
GROUP BY GROUPING SETS (
	(s_tier, region), 
	(region, s_tier), 
	(cust_id, cust_name, num_emp)
);
```


<table>
<tr>
<th valign="top">

cust\_name

</th>
<th valign="top">

cust\_id

</th>
<th valign="top">

region

</th>
<th valign="top">

sales\_tier

</th>
<th valign="top">

num\_emp

</th>
<th valign="top">

gr\_reg

</th>
<th valign="top">

gr\_tier

</th>
<th valign="top">

gr\_num

</th>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthWest

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthWest

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthWest

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthWest

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

gold

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthWest

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

platinum

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NorthEast

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthEast

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

SouthWest

</td>
<td valign="top">

silver

</td>
<td valign="top">

NULL

</td>
<td valign="top">

0

</td>
<td valign="top">

0

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

CustA

</td>
<td valign="top">

1

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

5

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustI

</td>
<td valign="top">

9

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

6

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustG

</td>
<td valign="top">

7

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

15

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustB

</td>
<td valign="top">

2

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

26

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustE

</td>
<td valign="top">

5

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

32

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustF

</td>
<td valign="top">

6

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

45

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustH

</td>
<td valign="top">

8

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

99

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustJ

</td>
<td valign="top">

10

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

101

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustK

</td>
<td valign="top">

11

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

108

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustD

</td>
<td valign="top">

4

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

180

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

CustC

</td>
<td valign="top">

3

</td>
<td valign="top">

NULL

</td>
<td valign="top">

NULL

</td>
<td valign="top">

250

</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

0

</td>
</tr>
</table>

