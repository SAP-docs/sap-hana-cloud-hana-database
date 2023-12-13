<!-- loio20d6169a75191014892db922f94abe41 -->

# DELETE Statement \(Data Manipulation\)

Deletes records from a table where a specified condition is met.



<a name="loio20d6169a75191014892db922f94abe41__sql_delete_1sql_delete_syntax"/>

## Syntax

```
DELETE FROM <table_name> [ <partition_restriction> ] 
   [ FOR PORTION OF APPLICATION_TIME FROM <from_value> TO <to_value> ]
   [ WHERE <condition> ] [ <hint_clause> ]
```



<a name="loio20d6169a75191014892db922f94abe41__sql_delete_1sql_delete_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

FROM *<table\_name\>*

</b></dt>
<dd>

Specifies the table name where the deletion is to occur, with optional schema name.

```
<table_name> ::= [[<database_name>.][<schema_name>.]]<identifier>
 
<schema_name> ::= <unicode_name>
```

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

For a partitioned table, *<partition\_restriction\>* specifies the partition in which the target rows are located.

```
<partition_restriction> ::= PARTITION ( <partition_number> )

<partition_number> ::= <unsigned_integer>
```

If you do not specify a partition restriction, then the database checks all partitions for the delete. But if there is a partition restriction, then only the rows in the specified partition are deleted. Use the TABLE\_PARTITIONS system view to determine the partition number.



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
 | CURRENT OF <cursor>
```

WHERE CURRENT OF *<cursor\>* specifies to perform the delete at the current position in the cursor.

For more information on *<predicate\>*, see the Predicates topic in this guide.



</dd><dt><b>

*<hint\_clause\>*

</b></dt>
<dd>

Specifies the hint clause. For information on specifying hints, see the HINT clause of the SELECT statement.



</dd><dt><b>

FOR PORTION OF APPLICATION\_TIME

</b></dt>
<dd>

Deletes rows that are fully contained within the given time period. FROM and TO values for partially overlapping rows will be adjusted accordingly.



</dd>
</dl>



<a name="loio20d6169a75191014892db922f94abe41__sql_delete_1sql_delete_description"/>

## Description

If the WHERE clause is omitted, then DELETE removes all records from a table.



<a name="loio20d6169a75191014892db922f94abe41__sql_delete_1sql_delete_examples"/>

## Examples

This example deletes values equal to 1 from table T.

Create a table T and insert some data.

```
CREATE ROW TABLE T (KEY INT PRIMARY KEY, VAL INT);
               INSERT INTO T VALUES (1, 1);
               INSERT INTO T VALUES (2, 2);
               INSERT INTO T VALUES (3, 3);
```

Delete from table T where the key column is equal to 1;

```
DELETE FROM T WHERE KEY = 1;
```

After executing the above query, the contents of table T are as follows, showing that one row was deleted from the table:


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

3

</td>
</tr>
</table>

This example deletes partition 1 from table T1.

```
CREATE COLUMN TABLE T1 (a int, b int) PARTITION BY RANGE (a) 
     (PARTITION 0 <= VALUES < 10, PARTITION OTHERS);

INSERT INTO T1 PARTITION(1) VALUES(1,50);

DELETE FROM T1 PARTITION(1);
```

The following statements provide an example of updating and deleting multiple tables \(currently only COLUMN tables are supported\) through an updatable cursor. In this case, you must specify columns of tables to be locked using FOR UPDATE OF within the cursor's SELECT statement. DML execution using updatable cursor is allowed just one time per row.

```
CREATE COLUMN TABLE employees (employee_id INTEGER, employee_name NVARCHAR(30), department_id INTEGER);
INSERT INTO employees VALUES (1, 'John', 1);
INSERT INTO employees VALUES (2, 'Sam', 2);
INSERT INTO employees VALUES (3, 'Julie', 3);
INSERT INTO employees VALUES (4, 'Kate', 4);

CREATE COLUMN TABLE departments (department_id INTEGER, department_name NVARCHAR(20));
INSERT INTO departments VALUES (1, 'Development');
INSERT INTO departments VALUES (2, 'Operation');
INSERT INTO departments VALUES (3, 'HR');
INSERT INTO departments VALUES (4, 'Security');

DO BEGIN
      DECLARE CURSOR cur FOR SELECT employees.employee_name, departments.department_name
      FROM employees, departments WHERE employees.department_id = departments.department_id
      FOR UPDATE OF employees.employee_id, departments.department_id;
      FOR r AS cur DO
      IF r.department_name = 'Development' THEN
      UPDATE employees SET employee_id = employee_id + 10000, department_id = department_id + 100
      WHERE CURRENT OF cur;
      UPDATE departments SET department_id = department_id + 100
      WHERE CURRENT OF cur;
      ELSEIF r.department_name = 'HR' THEN
      DELETE FROM employees WHERE CURRENT OF cur;
      DELETE FROM departments WHERE CURRENT OF cur;
      END IF;
      END FOR;
END;
```



This example creates a table, populates it with data and then deletes rows fully contained withing the date range '2018-8-4' to '2018-8-8'. The VALIDFROM and VALIDTO values of the partially overlapping rows are updated accordingly.

```
CREATE COLUMN TABLE T1(VALIDFROM DATE NOT NULL, VALIDTO DATE NOT NULL, PKEY INT, VALUE INT , PERIOD FOR APPLICATION_TIME(VALIDFROM, VALIDTO));
INSERT INTO T1 VALUES('2018-8-1', '2018-8-3', 1, 9494);
INSERT INTO T1 VALUES('2018-8-3', '2018-8-5', 1, 20);
INSERT INTO T1 VALUES('2018-8-5', '2018-8-7', 1, 30);
INSERT INTO T1 VALUES('2018-8-7', '2018-8-9', 1, 40);
delete from t1 for portion of application_time from '2018-8-4' to '2018-8-8' where pkey = 1;
select * from t1 order by validfrom, validto;
-- (‘2018-8-1’, ’2018-8-3’, 1, 9494) -- untouched row
-- (‘2018-8-3’, ‘2018-8-4’, 1, 20) –validto value updated accordingly for partially overlapping row
-- (‘2018-8-8’, ‘2018-8-9’, 1, 40) –validfrom value updated accordingly for partially overlapping row


```

```
INSERT INTO T1 VALUES('2018-8-1', '2018-8-3', 1, 9494);
INSERT INTO T1 VALUES('2018-8-3', '2018-8-5', 1, 20);
INSERT INTO T1 VALUES('2018-8-5', '2018-8-7', 1, 30);
INSERT INTO T1 VALUES('2018-8-7', '2018-8-9', 1, 40);

```

```
DELETE FROM T1 FOR PORTION OF APPLICATION_TIME FROM '2018-8-4' TO '2018-8-8' WHERE PKEY = 1;

```

```
SELECT * FRP, T1 ORDER BY VALIDFROM, VALIDTO;

-- (‘2018-8-1’, ’2018-8-3’, 1, 9494) - Row isunchanged
-- (‘2018-8-3’, ‘2018-8-4’, 1, 20) – VALIDTO value is updated accordingly for partially overlapping row
-- (‘2018-8-8’, ‘2018-8-9’, 1, 40) – VALIDFROM value updated accordingly for partially overlapping row

```

**Related Information**  


[TABLE\_PARTITIONS System View](../../020-System-Views-Reference/021-System-Views/table-partitions-system-view-c81d9be.md "Partition-specific information for partitioned tables.")

[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

[Predicates](../predicates-20a2ab2.md "")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[HINTS System View](../../020-System-Views-Reference/021-System-Views/hints-system-view-f55ce8e.md "Provides all available hints to be used in WITH HINT clauses.")

[HINT Details](hint-details-4ba9edc.md "The SQL Optimizer usually determines the access path (for example, index search versus table scan) on the basis of the costs (Cost-Based Optimizer). You can override the SQL Optimizer choice by explicitly specifying hints in the query that enforces a certain access path.")

