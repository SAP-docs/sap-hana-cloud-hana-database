<!-- loio20fc06a7751910149892c0d09be21a38 -->

# REPLACE Statement \(Data Manipulation\)

Updates rows in a table or inserts new rows. This UPSERT and REPLACE statements are synonymous and have identical syntax and purpose.



<a name="loio20fc06a7751910149892c0d09be21a38__sql_replace_upsert_1sql_replace_upsert_syntax"/>

## Syntax

```
REPLACE <table_name> [ <column_list_clause> ]
   { 
     <value_list_clause> [ WHERE <condition> | WITH PRIMARY KEY ]
     | <subquery> 
   }
```



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



<a name="loio20fc06a7751910149892c0d09be21a38__sql_replace_upsert_1sql_command_description"/>

## Description

When this command is used without a subquery, it functions in a similar way to the UPDATE statement. The difference with this command is that when the WHERE clause condition is false it inserts a new record into the table.

When this command is used with a table that has a primary key, the primary key column must be included in the column list. Columns defined with NOT NULL and without a default specification also have to be included in the column list. Columns that are not specified are filled with a default value or NULL.

The UPSERT \(or REPLACE\) statement with a subquery operates like the INSERT statement. The exception with this command is that, if an existing row in the table has the same primary key value as a new row, the row is updated with the returned record from the subquery. If the table does not have a primary key, then the command functions in an equivalent way to an INSERT statement as an index cannot be used to check for row duplication.



<a name="loio20fc06a7751910149892c0d09be21a38__section_xdb_vdt_kfb"/>

## Examples

See the UPSERT statement for examples of how to update rows using the REPLACE/UPSERT statements.

**Related Information**  


[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

[UPSERT Statement \(Data Manipulation\)](upsert-statement-data-manipulation-ea8b677.md "Updates rows in a table or inserts new rows. This UPSERT and REPLACE statements are synonymous and have similar syntax and purpose.")

[UPDATE Statement \(Data Manipulation\)](update-statement-data-manipulation-20ff268.md "Changes the values of the records of a table.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Predicates](../predicates-20a2ab2.md "")

[EXPLAIN\_PLAN\_TABLE System View](../../020-System-Views-Reference/021-System-Views/explain-plan-table-system-view-20a3dba.md "Provides information about SQL query plan explanation results.")

[M\_SQL\_PLAN\_CACHE System View](../../020-System-Views-Reference/022-Monitoring-Views/m-sql-plan-cache-system-view-20c57b8.md "Provides statistics for an individual execution plan.")

