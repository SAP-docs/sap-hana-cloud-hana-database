<!-- loio20d42e77751910149f0ff6b879b1290f -->

# CREATE FUNCTION Statement \(Procedural\)

Creates a user-defined function.



Syntax

```
CREATE [ OR REPLACE ] FUNCTION <function_name> 
   [ ( <input_parameter_clause> ) ] 
    RETURNS <return_type>
   [ LANGUAGE <lang> ]
   [ SQL SECURITY { DEFINER | INVOKER } ] 
   [ DEFAULT SCHEMA <default_schema_name> ]
   [ <variable_cache_clause> ]
   [ DETERMINISTIC ] 
   [ WITH ENCRYPTION ]
   AS
     { BEGIN 
        <statement_body> 
     END [ <cache_clause> ]
     | HEADER ONLY }
```



<a name="loio20d42e77751910149f0ff6b879b1290f__sql_create_function_1sql_create_function_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<function\_name\>*

</b></dt>
<dd>

Specifies the function name, and optionally, a schema name.

```
<function_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<input\_parameter\_clause\>*

</b></dt>
<dd>

Specifies the input parameters for the function.

```
<input_parameter_clause> ::= <parameter> [,...] ]

<parameter> ::= [ IN ] <param_name> <data_type>

<param_name> ::= <identifier>
<data_type> ::= 
    <sql_type> [ ARRAY ] 
    | <table_type> 
    | <table_type_definition>
    | <any_table_type>
```

Scalar user-defined functions support primitive SQL types as well as table parameters \(actual physical tables\), views, and table variables. Table user-defined functions support table types as input.


<dl>
<dt><b>

*<sql\_type\>* \[ ARRAY \]

</b></dt>
<dd>

Specifies the SQL type. Use the optional ARRAY keyword with *<sql\_type\>* if the parameter is an array.

```
<sql_type> ::=
 DATE
 | TIME
 | TIMESTAMP
 | SECONDDATE
 | TINYINT
 | SMALLINT
 | INTEGER
 | BIGINT
 | DECIMAL
 | SMALLDECIMAL
 | REAL
 | DOUBLE
 | NVARCHAR
 | VARBINARY
 | CLOB
 | NCLOB
 | BLOB
```

Scalar user-defined functions do not support VARBINARY, CLOB, NCLOB, or BLOB types.



</dd><dt><b>

*<table\_type\>*

</b></dt>
<dd>

Specifies a table type that was previously defined with the CREATE TYPE command.

```
<table_type> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<table\_type\_definition\>*

</b></dt>
<dd>

Specifies a table type that is implicitly defined within the signature.

```
<table_type_definition> ::= TABLE (<column_list_definition>)

<column_list_definition> ::= <column_elem>[, <column_elem> [,…] ] 

<column_elem> ::= <column_name> <data_type>

<column_name> ::= <identifier>
```



</dd><dt><b>

*<any\_table\_type\>*

</b></dt>
<dd>

Defines the table type at DDL time or query compilation time.

```
<any_table_type> ::= TABLE(...)
```

The syntax of *<any\_table\_type\>* requires you to explicitly specify **TABLE\(…\)** \(for example, <code>CREATE FUNCTION anyfunc_in (IN itab <b>TABLE(...)</b>, outtab <b>TABLE(...)</b> ) AS BEGIN…</code>\).



</dd>
</dl>



</dd><dt><b>

RETURNS *<return\_type\>*

</b></dt>
<dd>

Specifies the return type.

```
<return_type> ::= { <return_parameter_list> | <return_table_type> }
```

Scalar functions must return scalar values specified in *<return\_parameter\_list\>*. Table functions must return a table whose type is defined by *<return\_table\_type\>*.


<dl>
<dt><b>

*<return\_parameter\_list\>*

</b></dt>
<dd>

Specifies the output parameters. Use the optional ARRAY keyword for *<sql\_type\>* if the return parameter is an array.

```
<return_parameter_list> ::= <return_parameter>[, <return_parameter> [,…] ]

<return_parameter> ::= <parameter_name> <sql_type> [ ARRAY ]
```



</dd><dt><b>

*<return\_table\_type\>*

</b></dt>
<dd>

Specifies the structure of the returned table data.

```
<return_table_type> ::= TABLE ( <ret_column_list> )
```



</dd><dt><b>

*<ret\_column\_list\>*

</b></dt>
<dd>

Specifies the list of columns returned from the function.

```
<ret_column_list> ::= <ret_column_elem>[, <ret_column_elem> [,…] ]
```



</dd><dt><b>

*<ret\_column\_elem\>*

</b></dt>
<dd>

Specifies the name of the column element with its associated data type.

```
<ret_column_elem> ::= <column_name> <sql_type> 

<column_name> ::= <identifier>
```



</dd>
</dl>



</dd><dt><b>

LANGUAGE *<lang\>*

</b></dt>
<dd>

Specifies the programming language used in the function.

```
LANGUAGE <lang>

<lang> ::= SQLSCRIPT
```

You can only use SQLScript functions.



</dd><dt><b>

SQL SECURITY \{ DEFINER | INVOKER \}

</b></dt>
<dd>

Specifies the security mode of the function.


<dl>
<dt><b>

DEFINER

</b></dt>
<dd>

Specifies that the function is executed with the privileges of the definer of the function. DEFINER is the default for table user-defined functions.



</dd><dt><b>

INVOKER

</b></dt>
<dd>

Specifies that the function is executed with the privileges of the invoker of the function. Invoker is the default for scalar user-defined functions.



</dd>
</dl>



</dd><dt><b>

*<default\_schema\_name\>*

</b></dt>
<dd>

Specifies the schema for unqualified objects in the function body.

```
<default_schema_name> ::= <identifier>
```

If *<default\_schema\_name\>* is not specified, then the *<current\_schema\>* of the session is used.



</dd><dt><b>

DETERMINISTIC

</b></dt>
<dd>

DETERMINISTIC applies to scalar-functions. Signifies that the SQLScript function returns the same result any time it is called with the same input parameters.



</dd><dt><b>

*<cache\_clause\>*

</b></dt>
<dd>

Caches the result of a table function with an optional projection list and filter conditions.

Using a static result cache may result in stale data, and specifying a retention period ensures that data does not exceed the specified RETENTION period. Data that exceeds the retention period is refreshed and up-to-date data is returned.

```
<cache_clause> ::= WITH [ STATIC ] CACHE [ NAME <cache_name> ]
   [ RETENTION <minute_value> ]
   [ OF <projection_list> ] 
   [ FILTER <filter_condition> ]
   [ <location_clause> ]
```


<dl>
<dt><b>

*<cache\_name\>*

</b></dt>
<dd>

Specifies a unique name for the result cache.

```
<cache_name> ::= <identifier>
```

Multiple result caches for the same function are supported, but the properties of each result cache must be unique. If the cache name is not not specified, an auto-generated result cache name is used \(\_SYS\_CACHE\#*<function\_name\>*\).



</dd><dt><b>

*<minute\_value\>*

</b></dt>
<dd>

Specifies the result cache retention period.

```
<minute_value> ::= <unsigned_integer>
```

Only stale data access that does not exceed the specified RETENTION period is allowed. For outdated data that exceeds the RETENTION period, internally the result cache is refreshed and up-to-date data is returned.



</dd><dt><b>

*<projection\_list\>*

</b></dt>
<dd>

Specifies a result cached projection list to reduce the amount of cached data.

```
<projection_list> ::= <projection_name> [, <projection_name> [,...] ]

<projection_name> ::= <column_name> 
 | <aggr_type>(<column_name>)

<aggr_type> ::= { SUM | MIN | MAX | COUNT | AVG }
```

If a column that is not part of the projection list is requested or included in the WHERE clause, then the result cache cannot be exploited. In addition, you can direct an aggregation type of a specific column. If the column is specified, then the result cache includes aggregated results of that column and returns aggregated results only.



</dd><dt><b>

*<filter\_condition\>*

</b></dt>
<dd>

Specifies a filter condition to reduce the amount of cached data.

```
<filter_condition> ::=
 <condition> OR <condition> 
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>

   
<predicate> ::= 
 <comparison_predicate>
 | <range_predicate>
 | <in_predicate> 
 | <like_predicate> 
 | <null_predicate>
 
<comparison_predicate> ::= 
 <table_expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( <table_expression_list> )
 
<range_predicate> ::= 
 <table_expression> [ NOT ] BETWEEN <table_expression> AND <table_expression>
 
<in_predicate> ::= 
 <table_expression> [ NOT ] IN ( <table_expression_list> )
 

<like_predicate> ::= 
 <table_expression> [ NOT ] LIKE <table_expression> [ ESCAPE <table_expression> ]
 
<null_predicate> ::= 
 <table_expression> IS [ NOT ] NULL

<table_expression_list> ::= <table_expression> [, <table_expression> [,… ] ]
```

Only filtered results are cached. Predicates with subqueries are not supported. All forms of non-parameterized query filters are supported. For parameterized query filters, only conjunctive forms are supported.



</dd><dt><b>

*<location\_clause\>*

</b></dt>
<dd>

Specifies the location for the result cache entry.

*<variable\_cache\_clause\>*

```
<location_clause> ::= AT [LOCATION] '<hostname>:<port_number>'[, ...]
```



</dd>
</dl>



</dd><dt><b>

*<variable\_cache\_clause\>*

</b></dt>
<dd>

Caches variable values during execution time so that they do not need to be re-resolved as the operations in *<statement\_body\>* are executed. Caching a variable removes the risk that its value will change each time it is resolved.

```
<variable_cache_clause> ::= VARIABLE CACHE ON { <variable_entry_with_mode_list> | <variable_entry_without_mode_list> }

<variable_entry_with_mode_list> ::= <variable_entry_with_mode>  [, <variable_entry_with_mode> [,...] ]
<variable_entry_with_mode> ::= <variable_entry enable_mode>
<variable_entry> ::= { <variable_name> | <variable_name_clustered_list> }
<variable_name_clustered_list> ::= ( <variable_name> [, <variable_name> [,...] ] )
<enable_mode> ::= { ENABLE | DISABLE }                 
<variable_entry_without_mode_list> ::= <variable_entry> [, <variable_entry> [,...] ]
```



</dd><dt><b>

WITH ENCRYPTION

</b></dt>
<dd>

Encrypts the definition of the function. You cannot decrypt the definition later.



</dd><dt><b>

*<statement\_body\>*

</b></dt>
<dd>

Specifies the main body of the table functions and scalar functions.

```
<statement_body> ::=
 [ <func_using_list> ] [ <func_decl_list> ] [ <func_handler_list> ] <func_stmt_list>
```

Since the function is flagged as read-only, neither DDL or DML statements \(INSERT, UPDATE, and DELETE\) are allowed in the function body. Scalar functions support table-typed input variables and table cell assignments. Other table operations are not supported.

For more information on *<func\_using\_list\>*, *<func\_decl\_list\>*, *<func\_handler\_list\>*, and *<func\_stmt\_list\>*, see the corresponding*<proc\_using\_list\>*, *<proc\_decl\_list\>*, *<proc\_handler\_list\>*, and *<proc\_stmt\_list\>* clause in the CREATE PROCEDURE Statement \(Procedure\).



</dd>
</dl>



<a name="loio20d42e77751910149f0ff6b879b1290f__sql_create_function_1sql_create_function_description"/>

## Description

The CREATE FUNCTION statement creates read-only functions that are free of side effects. Neither DDL or DML statements \(INSERT, UPDATE, and DELETE\) are allowed in the function body. Also, other functions or procedures selected/called from the body of the function must be read only.

There are two kinds of user-defined function \(UDF\): table and scalar. They differ by input/output parameter, supported functionality in the body, and the way that they are consumed in SQL statements.

User-defined functions are read-only functions that are free of side effects: DDL or DML statements are not allowed within the function body.

When you specify HEADER ONLY, only the properties of the function are created along with the OID and no function dependencies exist. Once the headers are replaced with full function definitions, dependencies are created while the function OID remains the same. Dependencies appear in the OBJECT\_DEPENDENCIES system view. HEADER ONLY is useful when you need to create dependent functions.

**Notes on CREATE OR REPLACE behavior:**

-   The behavior of CREATE OR REPLACE depends on the existence of a pre-defined function: If there is no existing function, then it behaves like CREATE FUNCTION; otherwise, it behaves like ALTER FUNCTION.

-   You must explicitly set all parameters where the desired setting is different from the default \(for example, settings for procedure language, default schema, whether the procedure is deterministic or encrypted, sequential execution options, and so on\). Everything not specified in a CREATE OR REPLACE FUNCTION statement is reset to its default.

-   If you specify the security mode or route options, then the behavior depends on the existence of a pre-defined function: If there is no existing function, then the operation succeeds \(the function is created\). If the function exists and the security mode is different, then an error is returned.

-   CREATE OR REPLACE does not change any DDL settings for the function, such as grant privileges, dependent objects, and so on.


See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* guide for more information about creating and modifying user-defined functions.



<a name="loio20d42e77751910149f0ff6b879b1290f__section_hl3_yhh_5rb"/>

## Permissions

You must have the CREATE ANY privilege on the schema in which the function is created.



<a name="loio20d42e77751910149f0ff6b879b1290f__sql_create_function_1sql_create_function_examples"/>

## Examples

Create a table function called `Scale`.

```
CREATE FUNCTION Scale (val INT)
 RETURNS TABLE (a INT, b INT) LANGUAGE SQLSCRIPT AS
 BEGIN
     RETURN SELECT a, :val * b AS  b FROM mytab;
 END;
```

Use the `func_add_mul` function like a table. For example:

```
SELECT * FROM Scale(10);
SELECT * FROM Scale(10) AS a, Scale(10) AS b WHERE a.a =  b.a;
```

Create a scalar function called `func_add_mul`.

```
CREATE FUNCTION func_add_mul(x Double, y Double) 
 RETURNS result_add Double, result_mul Double 
 LANGUAGE SQLSCRIPT READS SQL DATA AS
 BEGIN
     result_add = :x + :y;
     result_mul = :x * :y;
 END;
```

Use the `func_add_mul` function like a built-in function. For example:

```
CREATE ROW TABLE TAB (a Double, b Double);
 INSERT INTO TAB VALUES (1.0, 2.0);
 INSERT INTO TAB VALUES (3.0, 4.0);
 
SELECT a, b, func_add_mul(a, b).result_add AS ADD, func_add_mul(a, b).result_mul AS MUL FROM TAB ORDER BY a;
```

The SELECT statement returns the following results:


<table>
<tr>
<th valign="top">

A

</th>
<th valign="top">

B

</th>
<th valign="top">

ADD

</th>
<th valign="top">

MUL

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

2

</td>
<td valign="top">

3

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

4

</td>
<td valign="top">

7

</td>
<td valign="top">

12

</td>
</tr>
</table>

Create a function called `func_mul` that is assigned to a scalar variable in the `func_mul_wrapper` function.

```
CREATE FUNCTION func_mul(input1 INT)
 RETURNS output1 INT LANGUAGE SQLSCRIPT AS
 BEGIN
     output1 = :input1 * :input1;
 END;

 CREATE FUNCTION func_mul_wrapper(input1 INT)
 RETURNS output1 INT LANGUAGE SQLSCRIPT AS
 BEGIN
     output1 = func_mul(:input1);
 END;

 SELECT func_mul_wrapper(2) as RESULT FROM DUMMY;
```

The SELECT statement returns 4.

Create a function called `FuncHeader` as HEADER ONLY. Later, you use ALTER FUNCTION to replace the header with the full function definitions.

```
CREATE FUNCTION FuncHeader (input1 integer) RETURNS  output1  integer AS HEADER ONLY;

ALTER FUNCTION FuncHeader (input1 integer) RETURNS  output1  integer 
AS
BEGIN 
  output1 = :input1 * :input1;
END;
```

Create a table function called `FUNC` with a static result cache,

```
CREATE FUNCTION FUNC RETURNS TABLE (COL1 INT, COL2 INT) AS
BEGIN
    RETURN SELECT * FROM TAB;
END
WITH CACHE RETENTION 10;
```

**Related Information**  


[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[ALTER FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/906c179f2d62418b957c801aa2c99e62.html "") :arrow_upper_right:

[CREATE FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/2fc6d7beebd14c579457092e91519082.html "This SQL statement creates read-only user-defined functions that are free of side effects. This means that neither DDL, nor DML statements (INSERT, UPDATE, and DELETE) are allowed in the function body. All functions or procedures selected or called from the body of the function must be read-only.") :arrow_upper_right:

[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

[M\_SQLSCRIPT\_VARIABLE\_CACHE System view](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-variable-cache-system-view-9fb8ca5.md "Provides runtime information about procedures and functions that have variable caches defined.")

[CREATE TYPE Statement \(Procedural\)](create-type-statement-procedural-20d5c1e.md "Creates a user-defined type")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[Predicates](../predicates-20a2ab2.md "")

[OBJECT\_DEPENDENCIES System View](../../020-System-Views-Reference/021-System-Views/object-dependencies-system-view-20cbd12.md "Provides information about the dependencies between objects, such as which views refer to a specific table.")

