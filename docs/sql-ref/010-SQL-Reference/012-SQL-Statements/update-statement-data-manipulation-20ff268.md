<!-- loio20ff268675191014964add3d17700909 -->

# UPDATE Statement \(Data Manipulation\)

Changes the values of the records of a table.



<a name="loio20ff268675191014964add3d17700909__sql_update_1sql_update_syntax"/>

## Syntax

```
UPDATE [ <top_clause> ] <table_name> [ AS <alias_name> ] 
   [ FOR PORTION OF APPLICATION_TIME <from_to_spec> ]
   [ <partition_restriction > ]
   <set_clause>
   [ WHERE <condition> ]
   [ <hint_clause> ]
```



<a name="loio20ff268675191014964add3d17700909__sql_update_1sql_update_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<top\_clause\>*

</b></dt>
<dd>

Limits the number of updated records \(for example, for chunkwise updates\).

```
<top_clause> ::= TOP <unsigned_integer>
```

*<unsigned\_integer\>* defines the number of records updated in one chunk.



</dd><dt><b>

*<table\_name\>*

</b></dt>
<dd>

Specifies the table where the UPDATE is performed, with the optional schema name.

```
<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd><dt><b>

*<alias\_name\>*

</b></dt>
<dd>

Specifies the alias that can be used to refer to the table defined by *<table\_name\>*.

```
<alias_name> ::= <identifier>
```



</dd><dt><b>

FOR PORTION OF APPLICATION\_TIME

</b></dt>
<dd>

For use with application-time period tables, this clause specifies that the update be limited to the specified period of time between *<valid\_from\>* and *<valid\_to\>*, inclusively.

```
FOR PORTION OF APPLICATION_TIME <from_to_spec>

<from_to_spec> ::= FROM <valid_from> TO <valid_to>
```

*<valid\_from\>* and *<valid\_to\>* are date values found in the application-time period table specified for *<table\_name\>*.



</dd><dt><b>

*<partition\_restriction\>*

</b></dt>
<dd>

For a partitioned table, *<partition\_restriction\>* specifies the partition in which the target updated rows are located.

```
<partition_restriction> ::= PARTITION ( <partition_number> )

<partition_number> ::= <unsigned_integer>
```

If you do not specify a partition restriction, then the database checks all partitions for the update. But if there is partition restriction, only the rows in specified partition are updated.

Limitations:

-   An UPDATE statement with a partition restriction is blocked if the following are true:

    -   Partitioning key column update

    -   UNIQUE constraint column update

    -   PRIMARY KEY column update


-   Updates that change the updated rows partition are not allowed.




</dd><dt><b>

*<set\_clause\>*

</b></dt>
<dd>

Specifies the column names and associated values to be set by the update statement.

```
<set_clause> ::= 
 SET {<column_name> = <expression> 
 | ( <with_clause> <subquery> ) },...
```

For the definitions of the *<with\_clause\>* and *<subquery\>*, see the SELECT statement. The *<with\_clause\>* can be used with column names, not with column lists.



</dd><dt><b>

WHERE *<condition\>*

</b></dt>
<dd>

Specifies the conditions when the command should be performed.

```
<condition> ::= 
 <condition> OR <condition>
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>
 | CURRENT OF <cursor>
```

WHERE CURRENT OF *<cursor\>* specifies to perform the update at the current position in the cursor.

For more information on *<predicate\>*, see the Predicates topic in this guide.



</dd><dt><b>

*<hint\_clause\>*

</b></dt>
<dd>

For information on hints, see the HINT clause in the SELECT statement.



</dd>
</dl>



<a name="loio20ff268675191014964add3d17700909__sql_update_1sql_update_description"/>

## Description

If the WHERE condition is used and is true for a specific row, then the an update is performed on that row. If the WHERE clause is omitted, then the UPDATE command updates all records of a table.



<a name="loio20ff268675191014964add3d17700909__sql_update_1sql_update_examples"/>

## Examples

Create table T, and insert two rows into it.

```
CREATE ROW TABLE T (KEY INT PRIMARY KEY, VAL INT);
 INSERT INTO T VALUES (1, 1);
 INSERT INTO T VALUES (2, 2);
```

Update the rows of table T if the condition in the WHERE clause is true.

```
UPDATE T SET VAL = VAL + 1 WHERE KEY = 1;
SELECT * FROM T;
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

2



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

This example shows how to update all rows of the table by omitting the WHERE clause.

```
UPDATE T SET VAL = KEY + 10;
SELECT * FROM T;
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

11



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

12



</td>
</tr>
</table>

Create table T2, and insert two rows into it.

```
CREATE ROW TABLE T2 (KEY INT PRIMARY KEY, VAR INT);
 INSERT INTO T2 VALUES (1, 2);
 INSERT INTO T2 VALUES (3, 6);
```

Update a chunk of 100,000 records of the table testtab that contain 'XXX' in the request column and the value 0 in the updated column. For each row processed, the updated column is set to 1.

```
update top 100000 testtab set updated = 1 where request = 'XXX' and updated = 0
```

UPDATE a table with an array value construction by enumeration .

```
UPDATE T1 SET C1 = ARRAY ( 11, 12, 13, 14 ) WHERE ID = 1
```

UPDATE a table with an array value construction by query.

```
UPDATE T1 SET C1 = ARRAY( SELECT C1 FROM T0 ) WHERE ID = 1
```

The following statements provide an example of updating a single table using updatable cursor:

```
CREATE COLUMN TABLE employees (employee_id INTEGER, employee_name NVARCHAR(30));
INSERT INTO employees VALUES (1, 'John');
INSERT INTO employees VALUES (20010, 'Sam');
INSERT INTO employees VALUES (21, 'Julie');
INSERT INTO employees VALUES (10005, 'Kate');

DO BEGIN
    DECLARE CURSOR cur FOR SELECT * FROM employees FOR UPDATE;
    FOR r AS cur DO
        IF r.employee_id < 10000 THEN
            UPDATE employees SET employee_id = employee_id + 10000
            WHERE CURRENT OF cur;
        ELSE
            DELETE FROM employees WHERE CURRENT OF cur;
        END IF;
  END FOR;
END;
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

In this example, suppose you have the following application-period time table, TAB01, that you want to update:


<table>
<tr>
<th valign="top">

ValidFrom



</th>
<th valign="top">

ValidTo



</th>
<th valign="top">

PKEY



</th>
<th valign="top">

Value



</th>
</tr>
<tr>
<td valign="top">

2018-08-01



</td>
<td valign="top">

2018-08-15



</td>
<td valign="top">

1



</td>
<td valign="top">

9494



</td>
</tr>
<tr>
<td valign="top">

2018-08-15



</td>
<td valign="top">

2018-08-31



</td>
<td valign="top">

1



</td>
<td valign="top">

20



</td>
</tr>
<tr>
<td valign="top">

2018-08-31



</td>
<td valign="top">

2018-09-10



</td>
<td valign="top">

1



</td>
<td valign="top">

30



</td>
</tr>
<tr>
<td valign="top">

2018-09-10



</td>
<td valign="top">

9999-12-31



</td>
<td valign="top">

1



</td>
<td valign="top">

40



</td>
</tr>
</table>

When you execute the following UPDATE statement, the values are updated according to the description in the Comment column of table that follows:

```
UPDATE TAB01 FOR PORTION OF '2018-08-20' AND '2018-10-20' SET VALUE=42 WHERE PKEY=1;
```


<table>
<tr>
<th valign="top">

ValidFrom



</th>
<th valign="top">

ValidTo



</th>
<th valign="top">

PKEY



</th>
<th valign="top">

VALUE



</th>
<th valign="top">

Comment



</th>
</tr>
<tr>
<td valign="top">

2018-08-01



</td>
<td valign="top">

2018-08-15



</td>
<td valign="top">

1



</td>
<td valign="top">

9394



</td>
<td valign="top">

Not modified \(outside of portion interval\)



</td>
</tr>
<tr>
<td valign="top">

2018-08-15



</td>
<td valign="top">

2018-08-20



</td>
<td valign="top">

1



</td>
<td valign="top">

20



</td>
<td valign="top">

Newly inserted record \(case partial overlap\)



</td>
</tr>
<tr>
<td valign="top">

2018-08-20



</td>
<td valign="top">

2018-08-31



</td>
<td valign="top">

1



</td>
<td valign="top">

42



</td>
<td valign="top">

Validfrom and Value were updated \(case partial overlap\)



</td>
</tr>
<tr>
<td valign="top">

2018-08-31



</td>
<td valign="top">

2018-09-10



</td>
<td valign="top">

1



</td>
<td valign="top">

42



</td>
<td valign="top">

Only Value was updated \(case full overlap\)



</td>
</tr>
<tr>
<td valign="top">

2018-09-10



</td>
<td valign="top">

2018-10-20



</td>
<td valign="top">

1



</td>
<td valign="top">

42



</td>
<td valign="top">

Validto and value were updated \(case partial overlap\)



</td>
</tr>
<tr>
<td valign="top">

2018-10-20



</td>
<td valign="top">

9999-12-31



</td>
<td valign="top">

1



</td>
<td valign="top">

40



</td>
<td valign="top">

Newly inserted record \(case partial overlap\)



</td>
</tr>
</table>

**Related Information**  


[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[Predicates](../predicates-20a2ab2.md "")

