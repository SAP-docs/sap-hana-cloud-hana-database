<!-- loio49d7752679f643539eaddcf4a2d7cb8e -->

# SUBARRAY Function \(Array\)

Returns a subset of values from the specified array beginning from the specified start position.



## Syntax

```
SUBARRAY(<array_value_expression>, <start_position> , <length>)
```



## Description


<dl>
<dt><b>

*<array\_value\_expression\>*

</b></dt>
<dd>

Specifies the array that the function returns the subset of values for.



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Specifies where in the array the subset of values begins.



</dd><dt><b>

*<length\>*

</b></dt>
<dd>

Determines the number of values.



</dd>
</dl>

Returns a values set of *<array\_value\_expression\>* starting from the *<start\_position\>* within the string.

If *<start\_position\>* is less than or equal to 0, then it is considered as 1.

If the *<length\>* is less than or equal to 0, or it is greater than the remaining part of *<array\_value\_expression\>*, then SUBARRAY returns the remaining part from the *<start\_position\>*.



## Example

The following example returns subsets from the specified array:

```
CREATE COLUMN TABLE ARRAY_TEST (IDX INT, VAL INT ARRAY);
INSERT INTO ARRAY_TEST VALUES (1, ARRAY(1, 2, 3));
INSERT INTO ARRAY_TEST VALUES (2, ARRAY(10, 20, 30, 40));
```

The example below generates a subarray that begins with 1 and has a length of 2:

```
SELECT SUBARRAY(VAL, 1, 2) "subarray" FROM ARRAY_TEST;
```

The statement above returns the following results:


<table>
<tr>
<th valign="top">

Subarray



</th>
</tr>
<tr>
<td valign="top">

1, 2



</td>
</tr>
<tr>
<td valign="top">

10, 20



</td>
</tr>
<tr>
<td valign="top">

1, 2



</td>
</tr>
<tr>
<td valign="top">

10, 20



</td>
</tr>
</table>

The example below generates a subarray beginning with 1 and with a length of 10:

```
SELECT SUBARRAY(VAL, 1, 10) "subarray" FROM ARRAY_TEST;
```

The statement above returns the following results:


<table>
<tr>
<th valign="top">

Subarray



</th>
</tr>
<tr>
<td valign="top">

1, 2, 3



</td>
</tr>
<tr>
<td valign="top">

10, 20, 30, 40



</td>
</tr>
<tr>
<td valign="top">

1, 2, 3



</td>
</tr>
<tr>
<td valign="top">

10, 20, 30, 40



</td>
</tr>
<tr>
<td valign="top">

1, 2, 3



</td>
</tr>
<tr>
<td valign="top">

10, 20, 30, 40



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

