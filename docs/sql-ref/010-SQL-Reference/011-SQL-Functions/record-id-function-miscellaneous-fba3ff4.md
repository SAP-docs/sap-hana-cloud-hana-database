<!-- loiofba3ff40198c4504b3693ad376e2bfbf -->

# RECORD\_ID Function \(Miscellaneous\)

Generates an ID for each row of the results.



<a name="loiofba3ff40198c4504b3693ad376e2bfbf__section_bwg_ttx_fcb"/>

## Syntax

```
RECORD_ID( <table> )
```



<a name="loiofba3ff40198c4504b3693ad376e2bfbf__section_wdh_ttx_fcb"/>

## Syntax Elements


<dl>
<dt><b>

*<table\>*

</b></dt>
<dd>

Specifies the column store or row store table to generate row IDs for.

*<t\>* should be located in the FROM clause that is syntactically closest, and cannot be a temporary table, derived table, or any other type of subquery. For example, these syntaxes are supported:

```
SELECT RECORD_ID(t) FROM t;
SELECT RECORD_ID(tab) FROM t AS tab;
```

However, these syntaxes are not supported:

```
SELECT RECORD_ID(v) FROM (SELECT * FROM t) AS v;
SELECT a, RECORD_ID(st) FROM (SELECT * FROM t) AS st;
```



</dd>
</dl>



<a name="loiofba3ff40198c4504b3693ad376e2bfbf__section_mkh_ttx_fcb"/>

## Description

Returns a result set with a unique BIGINT value for each row of the results. These values remain valid for the current transaction.



<a name="loiofba3ff40198c4504b3693ad376e2bfbf__section_c5h_ttx_fcb"/>

## Examples

The following example shows the use of the RECORD\_ID function to select a value from a specified row ID:

```
CREATE COLUMN TABLE T1 (column1 INT);
INSERT INTO T1 VALUES (5);
INSERT INTO T1 VALUES (10);
SELECT RECORD_ID(T1) AS RECORD_ID FROM T1;
```

The SELECT query returns the following result:


<table>
<tr>
<th valign="top">

RECORD\_ID

</th>
</tr>
<tr>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

2

</td>
</tr>
</table>

This SELECT query returns the following result:

```
SELECT * FROM T1 WHERE RECORD_ID(T1) = 2;
```


<table>
<tr>
<th valign="top">

COLUMN1

</th>
</tr>
<tr>
<td valign="top">

10

</td>
</tr>
</table>

