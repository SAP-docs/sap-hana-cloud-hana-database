<!-- loio20e6a27575191014bd54a07fd86c585d -->

# ROUND Function \(Numeric\)

Rounds the specified argument to the specified amount of places after the decimal point.



<a name="loio20e6a27575191014bd54a07fd86c585d__sql_function_round_1sql_function_round_syntax"/>

## Syntax

```
ROUND(<number> [, <position> [, <rounding_mode>]])
```



## Syntax Elements


<dl>
<dt><b>

*<number\>*

</b></dt>
<dd>

Specifies the numeric argument to round.



</dd><dt><b>

*<position\>*

</b></dt>
<dd>

Specifies the amount of places after the decimal point to round *<number\>* to. The default value is 0. A positive or negative integer rounds to the specified position to the right or left of the decimal point, respectively.



</dd><dt><b>

*<rounding\_mode\>*

</b></dt>
<dd>

Defines how the rounding should be carried out.

```
<rounding_mode> ::= 
ROUND_HALF_UP
| ROUND_HALF_DOWN
| ROUND_HALF_EVEN
| ROUND_UP
| ROUND_DOWN
| ROUND_CEILING
| ROUND_FLOOR
```


<dl>
<dt><b>

ROUND\_HALF\_UP

</b></dt>
<dd>

The value is rounded up to the next round figure. This is the default.

If the value falls precisely halfway between two rounded values, it is rounded up away from zero \(as is done in commercial rounding\).



</dd><dt><b>

ROUND\_HALF\_DOWN

</b></dt>
<dd>

The value is rounded down to the next round figure. If the value falls precisely halfway between two round values, it is rounded down towards zero.



</dd><dt><b>

ROUND\_HALF\_EVEN

</b></dt>
<dd>

The value is rounded to the next round figure. If the value falls precisely halfway between two rounded values, it is rounded to the value whose last decimal place is an even number.



</dd><dt><b>

ROUND\_UP

</b></dt>
<dd>

The value is always rounded away from zero, to the larger round figure.



</dd><dt><b>

ROUND\_DOWN

</b></dt>
<dd>

The value is always rounded towards zero, to the smaller round figure.



</dd><dt><b>

ROUND\_CEILING

</b></dt>
<dd>

The value is always rounded in a positive direction, to the larger value.



</dd><dt><b>

ROUND\_FLOOR

</b></dt>
<dd>

The value is always rounded in a negative direction, to the smaller value.



</dd>
</dl>



</dd>
</dl>



<a name="loio20e6a27575191014bd54a07fd86c585d__sql_function_round_1sql_function_round_description"/>

## Description

Rounds argument *<n\>* to the specified amount of places \(*<pos\>*\) after the decimal point.

When using ROUND with floating point types, REAL and DOUBLE, the precision of the numeric representation can affect the result. In this case, the actual number of digits after the decimal point is influenced by the precision of the type used. For example, the result of the following statement is `399.7099914550781` not `399.71`:

```
SELECT ROUND(TO_REAL(399.71429443359375),2) from DUMMY;
```



<a name="loio20e6a27575191014bd54a07fd86c585d__sql_function_round_1sql_function_round_examples"/>

## Examples

The following example returns the value ***16.2***:

```
SELECT ROUND (16.16, 1) "round" FROM DUMMY;
```

The following example returns the value ***20*** :

```
SELECT ROUND (16.16, -1) "round" FROM DUMMY;
```

The following example returns the value ***438.8***:

```
SELECT ROUND( 438.75, 1, ROUND_HALF_UP) "round" FROM DUMMY;
```

The following example returns the value ***438.7***:

```
SELECT ROUND( 438.75, 1, ROUND_HALF_DOWN) "round" FROM DUMMY;
```

The following example returns the value ***438.8***:

```
SELECT ROUND( 438.75, 1, ROUND_HALF_EVEN) "round" FROM DUMMY;
```

The following example returns the value ***438.8***:

```
SELECT ROUND( 438.71, 1, ROUND_UP) "round" FROM DUMMY;
```

The following example returns the value ***438.7***:

```
SELECT ROUND( 438.79, 1, ROUND_DOWN) "round" FROM DUMMY;
```

The following example returns the value ***438.8***:

```
SELECT ROUND( 438.75, 1, ROUND_CEILING) "round" FROM DUMMY;
```

The following example shows the difference when specifying a positive and negative integer for *<pos\>*:

```

SELECT ROUND(1234.1234, 1)"round" FROM DUMMY;  ==> 1234.1000
SELECT ROUND(1234.1234, -1)"round" FROM DUMMY; ==> 1230.0000

```

**Related Information**  


[Numeric Data Types](../numeric-data-types-4ee2f26.md "Numeric data types are used to store numeric information.")

