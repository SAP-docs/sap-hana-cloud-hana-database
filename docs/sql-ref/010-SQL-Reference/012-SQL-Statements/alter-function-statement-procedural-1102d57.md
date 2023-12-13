<!-- loio1102d570f16a4925a706f20285870350 -->

# ALTER FUNCTION Statement \(Procedural\)

Modifies a user-defined function.



<a name="loio1102d570f16a4925a706f20285870350__sql_create_function_1sql_create_function_syntax"/>

## Syntax

```
ALTER FUNCTION <function_name> 
 { [ ( <input_parameter_clause> ) ] 
   [ RETURNS <return_type> ] 
   [ LANGUAGE <lang> ] 
   [ SQL SECURITY { DEFINER | INVOKER } ] 
   [ DEFAULT SCHEMA <default_schema_name> ]
   [ <variable_cache_clause> ]
   [ DETERMINISTIC ] 
   [ WITH ENCRYPTION ] 
   AS
     BEGIN
      <statement_body>
     END 
 | ALTER FUNCTION <function_name> ENCRYPTION ON }
```



<a name="loio1102d570f16a4925a706f20285870350__sql_create_function_1sql_create_function_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<function\_name\>*

</b></dt>
<dd>

Specifies the identifier of the function to be altered, with optional schema name.



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

WITH ENCRYPTION

</b></dt>
<dd>

Encrypts the definition of the function. You cannot decrypt the definition later.



</dd><dt><b>

*<variable\_cache\_clause\>*

</b></dt>
<dd>

Modifies variable cache settings.

```
<variable_cache_clause> ::= { 
   <add_variable_cache_option> 
   | <alter_variable_cache_option>
   | <drop_variable_cache_option>
 }
```


<dl>
<dt><b>

*<add\_variable\_cache\>*

</b></dt>
<dd>

Adds variable cache settings.

```
<add_variable_cache> ::= ADD VARIABLE CACHE ON { <variable_entry_with_mode_list> | <variable_entry_without_mode_list> }

<variable_entry_with_mode_list> ::= <variable_entry_with_mode>  [, <variable_entry_with_mode> [,...] ]
<variable_entry_without_mode_list> ::= { <variable_name> | <variable_list_clustered> }
<variable_entry_with_mode> ::= <variable_entry enable_mode>
<variable_entry> ::= { <variable_name> | <variable_name_clustered_list> }
<variable_name_clustered_list> ::= ( <variable_name> [, <variable_name> [,...] ] )
<enable_mode> ::= { ENABLE | DISABLE }
```



</dd><dt><b>

*<alter\_variable\_cache\>*

</b></dt>
<dd>

Alters variable cache settings.

```
<alter_variable_cache> ::= ALTER VARIABLE CACHE ON <variable_entry_with_mode_list>

<variable_entry_with_mode_list> ::= <variable_entry_with_mode>  [, <variable_entry_with_mode> [,...] ]
<variable_entry_with_mode> ::= <variable_entry> <enable_mode>
<variable_entry> ::= { <variable_name> | <variable_name_clustered_list> }
<variable_name_clustered_list> ::= ( <variable_name> [, <variable_name> [,...] ] ) 
<enable_mode> ::= { ENABLE | DISABLE }
```



</dd><dt><b>

*<drop\_variable\_cache\>*

</b></dt>
<dd>

Drops one or all variable cache settings.

```
<drop_variable_cache> ::= DROP VARIABLE CACHE { ON <variable_list> | ALL }<
variable_list> ::= <variable_name> [, <variable_name> [,...] ]
```



</dd>
</dl>



</dd><dt><b>

*<statement\_body\>*

</b></dt>
<dd>

Defines the main body of the function. See the CREATE FUNCTION statement for more information on what *<statement\_body\>* can contain. [CREATE FUNCTION Statement \(Procedural\)](create-function-statement-procedural-20d42e7.md)



</dd>
</dl>



<a name="loio1102d570f16a4925a706f20285870350__sql_create_function_1sql_create_function_description"/>

## Description

The RESULT CACHE stores query execution results on the table function to improve query performance when a query is subsequently executed on the same table. With this ALTER FUNCTION command, the result cache can be added to the table function.

Use ALTER FUNCTION *<function\_name\>* ENCRYPTION ON to encrypt the contents of a function without changing *<statement\_body\>*. You cannot undo this change.

See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* guide for more information about creating and modifying user-defined functions.



<a name="loio1102d570f16a4925a706f20285870350__section_apm_lgh_5rb"/>

## Permissions

To alter a function, you must have the ALTER object privilege on the function or the schema in which it is located.



<a name="loio1102d570f16a4925a706f20285870350__section_udz_hyz_g1b"/>

## Examples

Create a table, Tab, and table function `function_a` that selects all records from table `Tab`.

```
CREATE ROW TABLE Tab (COL1 INT PRIMARY KEY, COL2 INT);
CREATE FUNCTION function_a RETURNS TABLE (COL1 INT, COL2 INT) AS 
BEGIN 
   RETURN SELECT * FROM Tab; 
END;
```

Add a static result cache to the `function_a` function with a retention of 10:

```
ALTER FUNCTION function_a ADD STATIC CACHE RETENTION 10;
```

Change the retention value of the result cache of the `function_a` function to 20.

```
ALTER FUNCTION function_a ALTER CACHE RETENTION 20;
```

Restrict the cache entry location for `function_a` to the \(fictitious\) indexserver `lbsrv18:31576`.

```
ALTER FUNCTION function_a ALTER CACHE ADD AT LOCATION 'lbsrv18:31576';
```

Remove the location specifications so that there are no restrictions on the cache entry location for `function_a`.

```
ALTER FUNCTION function_a ALTER CACHE DROP AT LOCATION 'lbsrv18:31576';
```

Drop the result cache of table function `function_a`.

```
ALTER FUNCTION function_a DROP CACHE;
```

**Related Information**  


[CREATE FUNCTION Statement \(Procedural\)](create-function-statement-procedural-20d42e7.md "Creates a user-defined function.")

[ALTER FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/906c179f2d62418b957c801aa2c99e62.html "") :arrow_upper_right:

[CREATE FUNCTION](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_4_QRC/en-US/2fc6d7beebd14c579457092e91519082.html "This SQL statement creates read-only user-defined functions that are free of side effects. This means that neither DDL, nor DML statements (INSERT, UPDATE, and DELETE) are allowed in the function body. All functions or procedures selected or called from the body of the function must be read-only.") :arrow_upper_right:

[M\_SQLSCRIPT\_VARIABLE\_CACHE System view](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-variable-cache-system-view-9fb8ca5.md "Provides runtime information about procedures and functions that have variable caches defined.")

[Predicates](../predicates-20a2ab2.md "")

[CREATE TYPE Statement \(Procedural\)](create-type-statement-procedural-20d5c1e.md "Creates a user-defined type")

