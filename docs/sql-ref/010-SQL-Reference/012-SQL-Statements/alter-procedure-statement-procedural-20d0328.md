<!-- loio20d0328875191014964a9059637c7f5f -->

# ALTER PROCEDURE Statement \(Procedural\)

Alters a procedure or manually triggers a recompilation of a procedure by generating an updated execution plan.



<a name="loio20d0328875191014964a9059637c7f5f__sql_alter_procedure_recompile_1sql_alter_procedure_recompile_syntax"/>

## Syntax

```
ALTER PROCEDURE <proc_name> 
 { [ ( <input_output_parameter_clause> ) ] 
   [ LANGUAGE <lang> ] 
   [ SQL SECURITY { DEFINER | INVOKER } ]
   [ DEFAULT SCHEMA <default_schema_name> ]
   [ READS SQL DATA ] 
   [ <variable_cache_clause> ]
   [ DETERMINISTIC ] 
   [ WITH ENCRYPTION ] 
   [ AUTOCOMMIT DDL { ON | OFF } }
    AS
     BEGIN  [ SEQUENTIAL EXECUTION ]
       <statement_body>
     END }
 | ALTER PROCEDURE <proc_name> ENCRYPTION ON
```



<a name="loio20d0328875191014964a9059637c7f5f__sql_alter_procedure_recompile_1sql_alter_procedure_recompile_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<proc\_name\>*

</b></dt>
<dd>

The procedure name, with optional schema name.

```
<proc_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<input\_output\_parameter\_clause\>*

</b></dt>
<dd>

Specifies the input and output parameters for the procedure.

```
<input_output_parameter_clause> ::= <parameter> [,...]

<parameter> ::= [ IN | OUT | INOUT ] <param_name> <data_or_table_type>

<data_or_table_type> ::=  
   { <sql_type> [ DEFAULT <constant> ] [ ARRAY ] 
   | <table_type> 
   | <table_type_definition>
   | <any_table_type> }
```

The default *<parameter\>* is IN. Input and output parameters must be explicitly typed; un-typed tables are not supported.

The input and output parameters of a procedure can have any of the primitive SQL types or a table type. INOUT parameters can only be of scalar type.


<dl>
<dt><b>

*<sql\_type\>* \[ DEFAULT *<constant\>* \] \[ ARRAY \]

</b></dt>
<dd>

Specifies the data type of the variable.

```
<sql_type> ::= 
   { DATE
   | TIME
   | SECONDDATE
   | TIMESTAMP
   | TINYINT
   | SMALLINT
   | INTEGER
   | BIGINT
   | SMALLDECIMAL
   | REAL
   | DOUBLE
   | NVARCHAR [ (<unsigned_integer>) ]
   | VARBINARY [ (<unsigned_integer>) ]
   | DECIMAL [ (<unsigned_integer> [, <unsigned_integer> ]) ] }
```

Only for use with IN parameters, use the optional DEFAULT option when you want to specify a default and a constant is correct for the data type. For example, you cannot specify a constant as a default for an ARRAY.

Use the optional ARRAY option when the parameter is an array.



</dd><dt><b>

*<table\_type\>*

</b></dt>
<dd>

Specifies a table type that was previously defined with the CREATE TYPE statement.

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

<column_list_definition> ::= <column_elem>[,...]

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

The syntax of *<any\_table\_type\>* requires you to explicitly specify **TABLE\(…\)** \(for example, <code>CREATE PROCEDURE anyproc_in (IN itab <b>TABLE(...)</b>, outtab <b>TABLE(...)</b> ) AS BEGIN…</code>\).



</dd>
</dl>



</dd><dt><b>

LANGUAGE

</b></dt>
<dd>

Specifies the programming language that is used in the procedure.

```
LANGUAGE <lang>

<lang> ::= { SQLSCRIPT | GRAPH }
```

The default is SQLSCRIPT. Define the language in all procedure definitions.

Specify GRAPH to use graph script, a domain-specific programming language for custom graph algorithms and analytics.



</dd><dt><b>

SQL SECURITY \{ DEFINER | INVOKER \}

</b></dt>
<dd>

Specifies the security mode for the procedure. The default is DEFINER.


<dl>
<dt><b>

DEFINER

</b></dt>
<dd>

Specifies that the procedure is executed with the privileges of the user who defined the procedure.



</dd><dt><b>

INVOKER

</b></dt>
<dd>

Specifies that the procedure is executed with the privileges of the user who invoked the procedure.



</dd>
</dl>



</dd><dt><b>

DEFAULT SCHEMA

</b></dt>
<dd>

Specifies the schema for unqualified objects in the procedure body.

```
DEFAULT SCHEMA <default_schema_name>

<default_schema_name> ::= <identifier>
```

If nothing is specified, then the current\_schema of the session is used.



</dd><dt><b>

DETERMINISTIC

</b></dt>
<dd>

DETERMINISTIC is for use with SQLScript procedures that produce scalar results. It specifies that the procedure returns the same result any time that it is called with the same input parameters.



</dd><dt><b>

READS SQL DATA

</b></dt>
<dd>

Specifies that the procedure is read only and side-effect free. That is, the procedure does not make modifications to the database data or its structure, even if the procedure body contains dynamic SQL calls.

The advantage of using this parameter is that certain optimizations are available for read-only procedures.



</dd><dt><b>

WITH ENCRYPTION

</b></dt>
<dd>

Encrypts the procedure definition. See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for more information on this clause and the impact of encrypting a procedure.



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

Defines the main body of the procedure. See the CREATE PROCEDURE statement for more information on what *<statement\_body\>* can contain. [CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md)



</dd><dt><b>

AUTOCOMMIT DDL \{ ON | OFF \}

</b></dt>
<dd>

Specifies whether to automatically commit DDL statements in the procedure body. Specify ON when automatic commit of DDL statements is required; for example, during administrative operations such as importing data.

This clause is only supported for SQLScript procedures that are not read-only. The default value is OFF.



</dd><dt><b>

SEQUENTIAL EXECUTION

</b></dt>
<dd>

Forces sequential execution of the procedure logic. No parallelism takes place.



</dd>
</dl>



<a name="loio20d0328875191014964a9059637c7f5f__sql_alter_procedure_recompile_1sql_alter_procedure_recompile_description"/>

## Description

For the full description of the clauses for the ALTER PROCEDURE statement with respect to SQLScript procedures, including examples, refer to the CREATE PROCEDURE and ALTER PROCEDURE statements in the *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



<a name="loio20d0328875191014964a9059637c7f5f__sql_alter_procedure_recompile_1sql_alter_procedure_recompile_examples"/>

## Example

**Example - Using variable cache**

Alters an SQLScript procedure to cache variable X:

```
CREATE TABLE test_cache (a INT);
INSERT INTO test_cache VALUES(5);

CREATE OR REPLACE PROCEDURE test_result_cache 
LANGUAGE SQLSCRIPT AS
 BEGIN
  x = SELECT * FROM test_cache;
  SELECT * FROM :x; 
 END;

ALTER PROCEDURE test_result_cache ADD VARIABLE CACHE ON X ENABLE;
```

**Related Information**  


[CREATE PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/7a2da744ce544db1814a5fff250e99f6.html "You use this SQL statement to create a procedure.") :arrow_upper_right:

[ALTER PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/042ab4636cf34a9cb88dd61c808861a8.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_1_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[M\_SQLSCRIPT\_VARIABLE\_CACHE System view](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-variable-cache-system-view-9fb8ca5.md "Provides runtime information about procedures and functions that have variable caches defined.")

[CREATE TYPE Statement \(Procedural\)](create-type-statement-procedural-20d5c1e.md "Creates a user-defined type")

