<!-- loioa924ee1e98ab435a874efa32e6f0ae14 -->

# STRING\_AGG Function \(Aggregate\)

Returns the concatenation string of the specified expression.



## Syntax

```
STRING_AGG( <expression>[, <delimiter> ] [ <order_by_clause> ] )
```



## Syntax Elements


<dl>
<dt><b>

*<expression\>*

</b></dt>
<dd>

Specifies an NVARCHAR expression with values to be concatenated. If the input values are a different data type than NVARCHAR, then implicit casting is attempted.

For example, if the NUM column has five integer values \(1, 2, 3, 4, 5\), then STRING\_AGG\("NUM",0\) returns 102030405.



</dd><dt><b>

*<delimiter\>*

</b></dt>
<dd>

Specifies the character to use as a delimiter when aggregating values.



</dd><dt><b>

*<order\_by\_clause\>*

</b></dt>
<dd>

Specifies the sort order of the input rows.

```
<order_by_clause> ::= ORDER BY <order_by_expression> [, <order_by_expression> [,...] ]

<order_by_expression> ::= 
 <column_name> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 
 | <column_position> [ <collate_clause> ] [ ASC | DESC ] [ NULLS FIRST | NULLS LAST ] 

<collate_clause> ::= COLLATE <collation_name>
```

*<collate\_clause\>* specifies the collation to use for ordering values in the results. *<collate\_clause\>* can only be used on columns defined as NVARCHAR \(or VARCHAR, which is a synonym for NVARCHAR\).*<collation\_name\>* is one of the supported collation names listed in the COLLATIONS system view.



</dd>
</dl>



## Description

NULL values are treated as empty strings.

The default ordering is ASC NULLS FIRST. If DESC is specified, then the ORDER BY expression becomes DESC NULLS LAST.



The example below creates table r1 and populate it with data.

```
CREATE ROW TABLE r1(a INT, str NVARCHAR(20), grp INT);

INSERT INTO r1 VALUES (3,'str2',0);
INSERT INTO r1 VALUES (0,'str1',0);
INSERT INTO r1 VALUES (NULL,'NULL',0);
INSERT INTO r1 VALUES (5,'str3',0);
INSERT INTO r1 VALUES (3,'val3',1);
INSERT INTO r1 VALUES (6,'val6',1);
INSERT INTO r1 VALUES (NULL,'NULL',1);
INSERT INTO r1 VALUES (1,'val1',1);
```

Execute the following statement to return the concatenation string of each record from table r1 in ascending order.

```
SELECT grp, STRING_AGG(str,','ORDER BY a)AS agg FROM R1 GROUP BY grp;
```

The statement above returns the following results.


<table>
<tr>
<th valign="top">

GRP



</th>
<th valign="top">

AGG



</th>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

NULL,str1,str2,str3



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

NULL,val1,val3,val6



</td>
</tr>
</table>

Execute the following statement to return the concatenation string of each record from table r1 in descending order.

```
SELECT grp, STRING_AGG(str,','ORDER BY a DESC) AS agg FROM r1 GROUP BY grp;
```

The statement above returns the following results.


<table>
<tr>
<th valign="top">

GRP



</th>
<th valign="top">

AGG



</th>
</tr>
<tr>
<td valign="top">

0



</td>
<td valign="top">

str3,str2,str1,NULL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

val6,val3,val1,NULL



</td>
</tr>
</table>

**Related Information**  


[Aggregate Functions](aggregate-functions-6fff7f0.md "Aggregate functions are analytic functions that calculate an aggregate value based on a group of rows.")

[COLLATIONS System View](../../020-System-Views-Reference/021-System-Views/collations-system-view-57ff6fd.md "Provides the list of collations that can be specified in an ORDER BY clause.")

