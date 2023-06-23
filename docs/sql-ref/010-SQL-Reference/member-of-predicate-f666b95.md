<!-- loiof666b950e5d34f84bb5b6f125e7e85c4 -->

# MEMBER OF Predicate

Determines whether a value is a member of an array.



## Syntax

```
<expression> [NOT] MEMBER OF <array_value_expression>
```



## Description

Determines whether a value is a member of an array.



## Example

The following statements create a table and insert arrays into it:

```
CREATE COLUMN TABLE ARRAY_TEST (IDX INT, VAL INT ARRAY);
INSERT INTO ARRAY_TEST VALUES (1, ARRAY(1, 2, 3));
INSERT INTO ARRAY_TEST VALUES (2, ARRAY(10, 20, 30, 40));
INSERT INTO ARRAY_TEST VALUES (3, ARRAY(10, 20, 30, 40));
INSERT INTO ARRAY_TEST VALUES (4, ARRAY(80, 90, 100, 110));
```

The following statement tests for arrays where 10 is a member, and returns the IDX values for the qualifying arrays.

```
SELECT IDX FROM ARRAY_TEST WHERE 10 MEMBER OF VAL;
```


<table>
<tr>
<th valign="top">

IDX



</th>
</tr>
<tr>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

3



</td>
</tr>
</table>

The following statement tests for arrays where 10 is not a member, and returns the IDX values for the qualifying arrays.

```
SELECT IDX FROM ARRAY_TEST WHERE 10 NOT MEMBER OF VAL;
```


<table>
<tr>
<th valign="top">

IDX



</th>
</tr>
<tr>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

4



</td>
</tr>
</table>

