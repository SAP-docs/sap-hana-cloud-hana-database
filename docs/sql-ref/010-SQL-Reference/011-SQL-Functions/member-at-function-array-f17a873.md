<!-- loiof17a873883164d958449a94af689895e -->

# MEMBER\_AT Function \(Array\)

Returns values from a specified array position.



## Syntax

```
MEMBER_AT(<array_value_expression>, <position> [, <default_value>])
```



## Description

Accesses an array element at the specified ordinal position and returns the value.

*<default\_value\>* indicates the value to return if *<position\>* is greater than the cardinality of the *<array\_value\_expression\>*. If *<default\_value\>* is not specified, and *<position\>* is greater than the cardinality of the *<array\_value\_expression\>*. then NULL is returned.



## Example

The following example creates a table and inserts arrays into it:

```
CREATE COLUMN TABLE ARRAY_TEST (IDX INT, VAL INT ARRAY);
INSERT INTO ARRAY_TEST VALUES (1, ARRAY(1, 2, 3));
INSERT INTO ARRAY_TEST VALUES (2, ARRAY(10, 20, 30, 40));
```

The following example returns the value in position 4 of each array in the table. The first array does not have a position 4, so NULL is returned:

```
SELECT MEMBER_AT(VAL, 4) "member_at" FROM ARRAY_TEST;
```


<table>
<tr>
<th valign="top">

member\_at



</th>
</tr>
<tr>
<td valign="top">

?



</td>
</tr>
<tr>
<td valign="top">

40



</td>
</tr>
</table>

The following example returns the value in position 4 of each array in the table. The first array does not have a position 4, so 1 is returned *<position\>* is greater than the cardinality of the array:

```
SELECT MEMBER_AT(VAL, 4, 1) "member_at" FROM ARRAY_TEST;
```


<table>
<tr>
<th valign="top">

member\_at



</th>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

40



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

