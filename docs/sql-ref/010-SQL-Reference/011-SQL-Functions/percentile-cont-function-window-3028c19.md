<!-- loio3028c19181b14bdf80fcc5333c5dc7b1 -->

# PERCENTILE\_CONT Function \(Window\)

Returns an interpolated value using the percentile value of a constant.



<a name="loio3028c19181b14bdf80fcc5333c5dc7b1__sql_function_abs_1sql_function_abs_syntax"/>

## Syntax

```
PERCENTILE_CONT( <constant_literal> ) WITHIN GROUP ( ORDER BY <expression> [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] ) <window_specification>
```



<a name="loio3028c19181b14bdf80fcc5333c5dc7b1__section_fsc_rcq_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<window\_specification\>*

</b></dt>
<dd>

Defines a window on the data over which the function operates. For *<window\_specification\>*, see [Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md).



</dd>
</dl>



<a name="loio3028c19181b14bdf80fcc5333c5dc7b1__sql_function_abs_1sql_function_abs_description"/>

## Description

Returns an interpolated value using the percentile value of *<constant\_literal\>*.

A continuous distribution of the values of *<expression\>* is assumed. Only a single *<expression\>* can be specified in ORDER BY clause; this expression must evaluate to a numeric type. The *<constant\_literal\>* should be a numeric value between, and including, 0 to 1, because it is a percentile value. In the interpolation, nulls are discarded in the calculation, and all indexes are 1 based. The details of the interpolation are as follows:

```
NR = the number of
 rows in the window partition R* P = the specified
 percentile value** INDEX1 = floor( 1 + ( P * (NR - 1) ) )
 INDEX2 = ceil( 1 + ( P * (NR - 1) ) )
 COEF1 = INDEX2 - ( 1 + ( P * (NR - 1) ) )
 COEF2 = INDEX1 - ( 1 + ( P * (NR - 1) ) )

 if INDEX1 == INDEX2
 then returns (value at INDEX1)
 else returns ( ( value at INDEX1 ) * COEF1 + ( value at INDEX2 ) * COEF2 )
```



<a name="loio3028c19181b14bdf80fcc5333c5dc7b1__section_n41_jbl_d1b"/>

## Examples

```
DROP TABLE p_cont;
CREATE TABLE p_cont (class NVARCHAR(10), val INT, offset INT);
 INSERT INTO p_cont VALUES('A', 1, 1);
 INSERT INTO p_cont VALUES('A', 3, 3);
 INSERT INTO p_cont VALUES('A', 5, null);
 INSERT INTO p_cont VALUES('A', 5, 2);
 INSERT INTO p_cont VALUES('A', 10, 0);
 INSERT INTO p_cont VALUES('B', 1, 3);
 INSERT INTO p_cont VALUES('B', 1, 1);
 INSERT INTO p_cont VALUES('B', 7, 1);
```

```
SELECT class, 
 val, 
 PERCENTILE_CONT(0.125) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pc1, 
 PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pc2, 
 PERCENTILE_CONT(0.875) WITHIN GROUP (ORDER BY val) OVER (PARTITION BY class) AS pc3 
FROM p_cont;
```


<table>
<tr>
<th valign="top">

CLASS

</th>
<th valign="top">

VAL

</th>
<th valign="top">

PC1

</th>
<th valign="top">

PC2

</th>
<th valign="top">

PC3

</th>
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

1

</td>
<td valign="top">

2.0

</td>
<td valign="top">

5.0

</td>
<td valign="top">

7.5

</td>
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

3

</td>
<td valign="top">

2.0

</td>
<td valign="top">

5.0

</td>
<td valign="top">

7.5

</td>
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

5

</td>
<td valign="top">

2.0

</td>
<td valign="top">

5.0

</td>
<td valign="top">

7.5

</td>
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

5

</td>
<td valign="top">

2.0

</td>
<td valign="top">

5.0

</td>
<td valign="top">

7.5

</td>
</tr>
<tr>
<td valign="top">

A

</td>
<td valign="top">

10

</td>
<td valign="top">

2.0

</td>
<td valign="top">

5.0

</td>
<td valign="top">

7.5

</td>
</tr>
<tr>
<td valign="top">

B

</td>
<td valign="top">

1

</td>
<td valign="top">

1.0

</td>
<td valign="top">

1.0

</td>
<td valign="top">

5.5

</td>
</tr>
<tr>
<td valign="top">

B

</td>
<td valign="top">

1

</td>
<td valign="top">

1.0

</td>
<td valign="top">

1.0

</td>
<td valign="top">

5.5

</td>
</tr>
<tr>
<td valign="top">

B

</td>
<td valign="top">

7

</td>
<td valign="top">

1.0

</td>
<td valign="top">

1.0

</td>
<td valign="top">

5.5

</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Window Functions and the Window Specification](window-functions-and-the-window-specification-20a3533.md "Window functions allow you to perform analytic operations over a set of input rows.")

[PERCENTILE\_DISC Function \(Window\)](percentile-disc-function-window-d839432.md "Returns the first value whose cumulative distribution value is greater than or equal to the percentile value of a constant.")

