<!-- loio3226201f95764a57810dd256c9524d56 -->

# MERGE INTO Statement \(Data Manipulation\)

Merges data into an existing column store table.



<a name="loio3226201f95764a57810dd256c9524d56__sql_merge_delta_1sql_merge_delta_syntax"/>

## Syntax

```
MERGE INTO <target_table> [ <partition_restriction> ] [ [ AS ] <alias> ]
 USING <table_reference>
 ON <search_condition> <merge_operation_specification>
```



<a name="loio3226201f95764a57810dd256c9524d56__sql_merge_delta_1sql_merge_delta_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<target\_table\>*

</b></dt>
<dd>

Specifies the target table \(identifier\) on which to perform the merge operation.



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

For a partitioned table, *<partition\_restriction\>* specifies the partition number in which the target rows are located.

```
<partition_restriction> ::= PARTITION ( <partition_number> )

<partition_number> ::= <unsigned_integer>
```

If you do not specify a partition restriction, then the database checks all partitions for the merge. But if there is a partition restriction, then only the rows in the specified partition are merged. Use the TABLE\_PARTITIONS system view to determine the partition number.



</dd><dt><b>

AS *<alias\>*

</b></dt>
<dd>

Specifies the alias to be used to refer to the table defined by *<target\_table\>*.



</dd><dt><b>

USING *<table\_reference\>*

</b></dt>
<dd>

Specifies the source \(identifier\) of the data to be updated or inserted. *<table\_reference\>* can be a regular or derived table.



</dd><dt><b>

*<search\_condition\>*

</b></dt>
<dd>

Specifies the criteria to use for matching values between *<table\_reference\>* and *<target\_table\>*.



</dd><dt><b>

*<merge\_operation\_specification\>*

</b></dt>
<dd>

Specifies merge operations to perform on *<table\_reference\>*.

```
<merge_operation_specification> ::=
 { <when_matched_clause>
 | <when_not_matched_clause>
 | <when_matched_clause> <when_not_matched_clause> }
```

*<when\_matched\_clause\>* must precede *<when\_not\_matched\_clause\>* if you specify both; otherwise, an error is returned.


<dl>
<dt><b>

*<when\_matched\_clause\>*

</b></dt>
<dd>

Specifies the update to perform when values match.

```
<when_matched_clause> ::=
 WHEN MATCHED [ AND <search_condition> ] THEN <when_matched_specification>

<when_matched_specification> ::=
 <update_specification>
 | <delete_specification>

<update_specification> ::= UPDATE SET <set_clause_list>

<delete_specification> ::= DELETE
```



</dd><dt><b>

*<when\_not\_matched\_clause\>*

</b></dt>
<dd>

Specifies the insert to perform when values do not match.

```
<when_not_matched_clause> ::=
 WHEN NOT MATCHED [ AND <search_condition> ] THEN <when_not_matched_specification>

<when_not_matched_specification> ::=
 INSERT [ ( <insert_column_list> ) ] VALUES <insert_value_list>

<insert_value_list> ::=
 ( <insert_value_element> [ {, <insert_value_element> } … ] )

<insert_value_element> ::=
 <value_expression>
 | <contextually_typed_value_specification>
```



</dd>
</dl>



</dd>
</dl>



<a name="loio3226201f95764a57810dd256c9524d56__sql_merge_delta_1sql_merge_delta_description"/>

## Description

A MERGE INTO statement conditionally updates the rows of a table and/or inserts new rows into a table. The MERGE INTO statement differs from the REPLACE statement in the following ways:

-   You must specify a data source.

-   You can omit the update or the insert specifications.


When you specify the WHEN MATCHED clause, a row must satisfy the join condition to be updated or deleted. If you specify the optional AND *<search\_condition\>* THEN … clause, then a row must match both the join condition and the *<search\_condition\>* to be updated or deleted.

When you specify the WHEN NOT MATCHED clause, a row must *not* satisfy the join condition to be updated or deleted. If you specify the optional AND *<search condition\>* THEN INSERT … clause, then a row must *not* satisfy the join condition but match the search condition to be inserted.

The existing SAP HANA *<update\_from\>* syntax can also be replaced by the MERGE INTO statement by omitting the MERGE WHEN NOT MATCHED clause.



<a name="loio3226201f95764a57810dd256c9524d56__sql_merge_delta_1sql_merge_delta_examples"/>

## Examples

The following example shows a simple merge operation:

```
CREATE SCHEMA "my_schema";
DROP TABLE "my_schema".t1;
DROP TABLE "my_schema".t2;
CREATE ROW TABLE "my_schema".t1 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t1 VALUES(1,1);
CREATE ROW TABLE "my_schema".t2 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t2 VALUES(1,2);
INSERT INTO "my_schema".t2 VALUES(2,3);

MERGE INTO "my_schema".t1 USING "my_schema".t2 ON "my_schema".t1.a = "my_schema".t2.a
 WHEN MATCHED THEN UPDATE SET "my_schema".t1.b = "my_schema".t2.b
 WHEN NOT MATCHED THEN INSERT VALUES("my_schema".t2.a, "my_schema".t2.b);

SELECT * FROM "my_schema".t1;
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

3



</td>
</tr>
</table>

The following merge example is equivalent to executing `UPDATE t1 FROM t1,t2 SET b = t2.b WHERE t1.a = t2.a;`

```
CREATE SCHEMA "my_schema";
DROP TABLE "my_schema".t1;
DROP TABLE "my_schema".t2;
CREATE ROW TABLE "my_schema".t1 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t1 VALUES(1,1);
CREATE ROW TABLE "my_schema".t2 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t2 VALUES(1,2);
INSERT INTO "my_schema".t2 VALUES(2,3);

MERGE INTO "my_schema".t1 USING "my_schema".t2 ON "my_schema".t1.a = "my_schema".t2.a
 WHEN MATCHED THEN UPDATE SET t1.b = "my_schema".t2.b;

SELECT * FROM "my_schema".t1; 
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2



</td>
</tr>
</table>

The following example only inserts values:

```
CREATE SCHEMA "my_schema";
DROP TABLE "my_schema".t1;
DROP TABLE "my_schema".t2;
CREATE ROW TABLE "my_schema"t1 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t1 VALUES(1,1);
CREATE ROW TABLE "my_schema".t2 (a INTEGER, b INTEGER);
INSERT INTO "my_schema".t2 VALUES(1,2);
INSERT INTO "my_schema".t2 VALUES(2,3);

MERGE INTO "my_schema".t1 USING "my_schema".t2 ON "my_schema".t1.a = "my_schema".t2.a
 WHEN NOT MATCHED THEN INSERT VALUES("my_schema".t2.a, "my_schema".t2.b);

SELECT * FROM "my_schema".t1;
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

3



</td>
</tr>
</table>

The following example deletes matched rows and returns an empty result:

```
CREATE ROW TABLE T1 (A INTEGER, B INTEGER);

INSERT INTO T1 VALUES (1,0);
INSERT INTO T1 VALUES (2,0);

CREATE ROW TABLE T2 (A INTEGER, B INTEGER);

INSERT INTO T2 VALUES (1,1);
INSERT INTO T2 VALUES (2,2);
INSERT INTO T2 VALUES (3,3);
INSERT INTO T2 VALUES (4,4);

MERGE INTO T1 USING T2 ON T1.A = T2.A
 WHEN MATCHED THEN DELETE;

SELECT * FROM T1;
```

The following example has search conditions applied and returns the table below:

```
CREATE COLUMN TABLE T1 (A INTEGER, B INTEGER);

INSERT INTO T1 VALUES (1,0);
INSERT INTO T1 VALUES (2,0);

CREATE COLUMN TABLE T2 (A INTEGER, B INTEGER);

INSERT INTO T2 VALUES (1,1);
INSERT INTO T2 VALUES (2,2);
INSERT INTO T2 VALUES (3,3);
INSERT INTO T2 VALUES (4,4);

MERGE INTO T1 USING T2 ON T1.A = T2.A
 WHEN MATCHED AND T1.A > 1 THEN UPDATE SET B = T2.B
 WHEN NOT MATCHED AND T2.A > 3 THEN INSERT VALUES (T2.A, T2.B);

SELECT * FROM T1;
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

0



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

4



</td>
</tr>
</table>

The following example inserts data into specific partitions in tables T1 and T2 and then merges data matched data in table T2 into partition 1 on table T1:

```
CREATE COLUMN TABLE T1 (a INT, b INT) PARTITION BY RANGE(a) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS);
CREATE COLUMN TABLE T2 (a INT, b INT) PARTITION BY RANGE(a) (PARTITION 0 <= VALUES < 10, PARTITION OTHERS);

INSERT INTO T1 PARTITION(1) VALUES(1, 1);
INSERT INTO T1 PARTITION(2) VALUES(10, 1);
INSERT INTO T2 PARTITION(2) VALUES(10, 1);

MERGE INTO T1 PARTITION(1) USING T2 ON T1.b = T2.b
    WHEN MATCHED THEN UPDATE SET T1.b = 2
    WHEN NOT MATCHED THEN INSERT VALUES (10, 1)

SELECT * from T1;
```


<table>
<tr>
<th valign="top">

A



</th>
<th valign="top">

B



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

2



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

1



</td>
</tr>
</table>

The following example executes a merge using a referenced table.

```
CREATE TABLE test2(id INT, c VARCHAR(10), d TIMESTAMP);
CREATE TABLE test (id INT, c VARCHAR(10), d TIMESTAMP);
MERGE INTO test2 
   USING (SELECT * FROM test) AS t1 
   ON t1.id = test2.id 
   WHEN MATCHED THEN
   UPDATE SET
   d = CURRENT_TIMESTAMP,
   c = t1.c;
```

**Related Information**  


[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

