<!-- loioea8b6773be584203bcd99da76844c5ed -->

# UPSERT Statement \(Data Manipulation\)

Updates rows in a table or inserts new rows. This UPSERT and REPLACE statements are synonymous and have similar syntax and purpose.



<a name="loioea8b6773be584203bcd99da76844c5ed__sql_replace_upsert_1sql_replace_upsert_syntax"/>

## Syntax

```
UPSERT <table_name> [ <partition_restriction> ] [ <column_list_clause> ] 
   { 
     <value_list_clause> [ WHERE <condition> | WITH PRIMARY KEY ]
     | <subquery>
   }
```



<a name="loioea8b6773be584203bcd99da76844c5ed__section_dvt_qkh_2gb"/>

## Syntax Elements


<dl>
<dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table to update, with the optional schema name.

```
<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd>
<dd>

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<column\_list\_clause\>*

</b></dt>
<dd>

Specifies a list of column identifiers, ordered in the order of values in the *<value\_list\_clause\>* or *<subquery\>*.

```
<column_list_clause> ::= ( <column_name> [,…] )

<column_name> ::= <identifier>
```



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

For a partitioned table, *<partition\_restriction\>* specifies the partition in which the target rows are located.

```
<partition_restriction> ::= PARTITION ( <<partition_number> )

<partition_number> ::= <unsigned_integer>
```

If you do not specify a partition restriction, then the database checks all partitions for the update. But if there is a partition restriction, then only the rows in the specified partition are updated. Use the TABLE\_PARTITIONS system view to determine the partition number.



</dd><dt><b>

*<value\_list\_clause\>*

</b></dt>
<dd>

Specifies a list of values, or expressions evaluating to values, to be inserted or updated into the table.

```
<value_list_clause> ::= VALUES ( <expression> [,…] )
```



</dd><dt><b>

WHERE *<condition\>*

</b></dt>
<dd>

Specifies the conditions where the command should be performed.

```
<condition> ::= 
 <condition> OR <condition>
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>
```



</dd><dt><b>

WITH PRIMARY KEY

</b></dt>
<dd>

Uses the primary key value in the *<value\_list\_clause\>* to define the row to act upon.



</dd><dt><b>

*<subquery\>*

</b></dt>
<dd>

For information on subqueries, see the SELECT statement.



</dd>
</dl>



## Description

When this command is used without a subquery, it functions in a similar way to the UPDATE statement. The difference with this command is that when the WHERE clause condition is false it inserts a new record into the table.

When this command is used with a table that has a primary key, the primary key column must be included in the column list. Columns defined with NOT NULL and without a default specification also have to be included in the column list. Columns that are not specified are filled with a default value or NULL.

The UPSERT \(or REPLACE\) statement with a subquery operates like the INSERT statement. The exception with this command is that, if an existing row in the table has the same primary key value as a new row, the row is updated with the returned record from the subquery. If the table does not have a primary key, then the command functions in an equivalent way to an INSERT statement as an index cannot be used to check for row duplication.



<a name="loioea8b6773be584203bcd99da76844c5ed__sql_replace_upsert_1sql_upsert_replace_examples"/>

## Example

Create table T.

```
CREATE ROW TABLE T (KEY INT PRIMARY KEY, VAL INT);
```

Insert a new value.

```
UPSERT T VALUES (1, 1);
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
</table>

Insert a new value if the condition in the WHERE clause is false or update the current row values if WHERE evaluates to true.

```
UPSERT T VALUES (2, 2) WHERE KEY = 2;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
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

2



</td>
</tr>
</table>

Update the table row where KEY is equal to 1.

```
UPSERT T VALUES (1, 9) WHERE KEY = 1;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

9



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
</table>

Use the "WITH PRIMARY KEY" keyword to update the table using the primary key value in the VALUES clause.

```
UPSERT T VALUES (1, 8) WITH PRIMARY KEY;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

8



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
</table>

Insert values using a subquery.

```
UPSERT T SELECT KEY + 2, VAL FROM T;
```


<table>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

VAL



</td>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

8



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

3



</td>
<td valign="top">

8



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

2



</td>
</tr>
</table>

UPSERT a table with an array value construction by enumeration.

```
UPSERT T1 VALUES ( 1, ARRAY ( 21, 22, 23, 24 ) ) WHERE ID = 1;
```

UPSERT a table with an array value construction by query.

```
UPSERT T1 VALUES ( 1, ARRAY ( SELECT C1 FROM T0 ) ) WHERE ID = 1;
```

UPSERT values into partition 1 of table T1 and then upsert values from table T1 to partition 1 in table T2.

```
CREATE COLUMN TABLE T1 (a int, b int) PARTITION BY RANGE (a) 
     (PARTITION 0 <= VALUES < 10, PARTITION OTHERS);
CREATE COLUMN TABLE T2 (a int, b int) PARTITION BY RANGE (a) 
     (PARTITION 0 <= VALUES < 10, PARTITION OTHERS);

INSERT INTO T1 PARTITION(1) VALUES(1,50);

UPSERT T1 PARTITION(1) VALUES(1,20);
UPSERT T2 PARTITION(1) SELECT * FROM T1;

Select * from T2;
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

20



</td>
</tr>
</table>

**Related Information**  


[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[REPLACE Statement \(Data Manipulation\)](replace-statement-data-manipulation-20fc06a.md "Updates rows in a table or inserts new rows. This UPSERT and REPLACE statements are synonymous and have identical syntax and purpose.")

[UPDATE Statement \(Data Manipulation\)](update-statement-data-manipulation-20ff268.md "Changes the values of the records of a table.")

[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

