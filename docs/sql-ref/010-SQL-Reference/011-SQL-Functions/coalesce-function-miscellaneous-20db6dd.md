<!-- loio20db6dd7751910149105978452f92bbd -->

# COALESCE Function \(Miscellaneous\)

Returns the first non-NULL expression from a specified list.



<a name="loio20db6dd7751910149105978452f92bbd__sql_function_coalesce_1sql_function_coalesce_syntax"/>

## Syntax

```
COALESCE(<expression_list>)
```



## Syntax Elements


<dl>
<dt><b>

*<expression\_list\>*

</b></dt>
<dd>

Specifies the expressions to return the first non-NULL expression from.



</dd>
</dl>



<a name="loio20db6dd7751910149105978452f92bbd__sql_function_coalesce_1sql_function_coalesce_description"/>

## Description

Returns the first non-NULL expression from a list. At least two expressions must be contained in *<expression\_list\>*, and all expressions must be comparable. The result is NULL if all the expressions are NULL.



<a name="loio20db6dd7751910149105978452f92bbd__sql_function_coalesce_1sql_function_coalesce_examples"/>

## Example

```
CREATE ROW TABLE coalesce_example (ID INT PRIMARY KEY, A REAL, B REAL);
 INSERT INTO coalesce_example VALUES(1, 100, 80);
 INSERT INTO coalesce_example VALUES(2, NULL, 63);
 INSERT INTO coalesce_example VALUES(3, NULL, NULL);

 SELECT id, a, b, COALESCE (a, b*1.1, 50.0) "coalesce" FROM coalesce_example;
```

The example above returns the results below:


<table>
<tr>
<th valign="top">

ID



</th>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
<th valign="top">

coalesce



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

100.0



</td>
<td valign="top">

80.0



</td>
<td valign="top">

100.0



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

NULL



</td>
<td valign="top">

63.0



</td>
<td valign="top">

69.30000305175781



</td>
</tr>
<tr>
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

50.0



</td>
</tr>
</table>

**Related Information**  


[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

