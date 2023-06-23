<!-- loiobcbb7ba0f4f2495ca954132382226929 -->

# NDIV0 Function \(Numeric\)

Returns 0 when divided by 0; otherwise, it returns the result of the division.



<a name="loiobcbb7ba0f4f2495ca954132382226929__sql_function_sign_1sql_function_sign_syntax"/>

## Syntax

```
NDIV0( <numerator>, <denominator> )
```



<a name="loiobcbb7ba0f4f2495ca954132382226929__sql_function_sign_1sql_function_sign_description"/>

## Description

Returns 0 if *<denominator\>* is 0. Otherwise, it returns the division of the numerator by the denominator. *<numerator\>* and *<denominator\>* can be any numeric value. The function allows you to avoid divided-by-zero error messages and can continue a calculation with a defined result.



<a name="loiobcbb7ba0f4f2495ca954132382226929__sql_function_sign_1sql_function_sign_examples"/>

## Example

The following example uses the NDIV0 function to allow the revenue calculation to complete without a divide by zero error:

```
SELECT Revenue, Quantity, NDIV0(Revenue, Quantity) as AverageRevenue FROM DUMMY;
```


<table>
<tr>
<th valign="top">

Revenue



</th>
<th valign="top">

Quantity



</th>
<th valign="top">

AverageRevenue



</th>
</tr>
<tr>
<td valign="top">

1000



</td>
<td valign="top">

4



</td>
<td valign="top">

250



</td>
</tr>
<tr>
<td valign="top">

2000



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

2500



</td>
<td valign="top">

0



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

3000



</td>
<td valign="top">

5



</td>
<td valign="top">

600



</td>
</tr>
</table>

