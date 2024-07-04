<!-- loio20d467407519101484f190f545d54b24 -->

# CREATE PROCEDURE Statement \(Procedural\)

Creates a procedure that uses the specified programming language.



<a name="loio20d467407519101484f190f545d54b24__sql_create_procedure_1sql_create_procedure_syntax"/>

## Syntax

```
CREATE [ OR REPLACE ] PROCEDURE <proc_name> 
   [ (<input_output_parameter_clause>) ]
   [ LANGUAGE <lang> ]
   [ SQL SECURITY { DEFINER | INVOKER } ]
   [ DEFAULT SCHEMA <default_schema_name> ]
   [ READS SQL DATA ] 
   [ <variable_cache_clause> ]
   [ DETERMINISTIC ] 
   [ WITH ENCRYPTION ]
   [ AUTOCOMMIT DDL { ON | OFF } ]
   AS 
     { BEGIN [ SEQUENTIAL EXECUTION ]
        <statement_body>
       END
       | HEADER ONLY }
```



<a name="loio20d467407519101484f190f545d54b24__sql_create_procedure_1sql_create_procedure_syntax_elements"/>

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

READS SQL DATA

</b></dt>
<dd>

Specifies that the procedure is read only and side-effect free. That is, the procedure does not make modifications to the database data or its structure, even if the procedure body contains dynamic SQL calls.

The advantage of using this parameter is that certain optimizations are available for read-only procedures.



</dd><dt><b>

SEQUENTIAL EXECUTION

</b></dt>
<dd>

Forces sequential execution of the procedure logic. No parallelism takes place.



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

DETERMINISTIC

</b></dt>
<dd>

DETERMINISTIC is for use with SQLScript procedures that produce scalar results. It specifies that the procedure returns the same result any time that it is called with the same input parameters.



</dd><dt><b>

WITH ENCRYPTION

</b></dt>
<dd>

Encrypts the procedure definition. See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for more information on this clause and the impact of encrypting a procedure.



</dd><dt><b>

AUTOCOMMIT DDL \{ ON | OFF \}

</b></dt>
<dd>

Specifies whether to automatically commit DDL statements in the procedure body. Specify ON when automatic commit of DDL statements is required; for example, during administrative operations such as importing data.

This clause is only supported for SQLScript procedures that are not read-only. The default value is OFF.



</dd><dt><b>

*<statement\_body\>*

</b></dt>
<dd>

```
<statement_body> ::=
 [ <proc_using_list> ] [ <proc_decl_list> ] [ <proc_handler_list> ] <proc_stmt_list>
```

Defines the main body of the procedure according to the specified programming language.


<dl>
<dt><b>

*<proc\_using\_list\>*

</b></dt>
<dd>

Defines the libraries to use.

```
<proc_using_list> ::= <proc_using> [ ... ]

<proc_using> ::= USING <library_name> AS <library_alias>;
<library_name> ::= [ <schema_name>.]<identifier>
<library_alias> ::= <identifier>
```



</dd><dt><b>

*<proc\_decl\_list\>*

</b></dt>
<dd>

Defines the declarations for the procedure.

*<proc\_decl\_list\>*

```
<proc_decl_list> ::= <proc_declaration> [ <proc_declaration> [...]]

<proc_declaration> ::= 
DECLARE { 
 <proc_variable> 
 | <proc_table_variable>
 | <proc_row_variable>
 | <proc_cursor>
 | <proc_condition> };
```



</dd><dt><b>

*<proc\_variable\>*

</b></dt>
<dd>

Defines variables for the procedure.

```
<proc_variable>::=
 <variable_name_list> [ CONSTANT ] { <sql_type> | <array_datatype> | AUTO } [ NOT NULL ] [ <default_value> ]
 
<variable_name_list> ::= <variable_name>[, <variable_name> [,…] ]
 <array_datatype> ::= ARRAY [ = <array_constructor> ]
 <array_constructor> ::= ARRAY (<expression> [, <expression> [,...] )
 <default_value> ::= { DEFAULT | = } { <value> | <expression> }
 <value> ::= A value of the type specified by <sql_type> or an expression
```

When you specify AUTO, you must also specify *<default\_value\>*.



</dd><dt><b>

*<proc\_table\_variable\>*

</b></dt>
<dd>

Defines table variables for the procedure.

```

<proc_table_variable> ::= <proc_table_var_def> [ <sort_def> ]

<proc_table_var_def>
 <variable_name_list> <table_type_definition>  
 | <table_type>
 | <variable_name_list> [ CONSTANT ] LIKE { <table_name> 
 | :<table_variable_name>.<column_name> [ AUTO ] [ NOT NULL ] [ <default_value> ]
 | <variable_name_list> [ CONSTANT ] TABLE LIKE { <table_name> | :<table_variable_name> } [ AUTO ] [ <default_value> ]

<sort_def> ::= SEARCH KEY ( <col_name> [, <col_name> [,…] ]
```

When you specify AUTO, you must also specify *<default\_value\>*.

*<sort\_def\>* is used in SQLScript procedures to sort the table variables. See the *SAP HANA Cloud, SAP HANA Database SQLScript Reference* for more information on sorted table variables.



</dd><dt><b>

*<proc\_row\_variable\>*

</b></dt>
<dd>

Defines row variables for the procedure.

```
<proc_row_variable> ::= 
<variable_name_list> ROW <row_definition>
 | <variable_name_list> ROW LIKE { <persistent_table_name> | :<other_table_row_or_cursor_variable_name>
```



</dd><dt><b>

*<proc\_cursor\>*

</b></dt>
<dd>

Defines the procedure cursors.

```
<proc_cursor> ::= 
 CURSOR <cursor_name> [ ( <proc_cursor_param_list> ) ] FOR <subquery>;
<proc_cursor_param_list> ::= <proc_cursor_param> [,...]
<variable_name> ::= <identifier>
<cursor_name> ::= <identifier>
<proc_cursor_param> ::= <param_name> <datatype>
```



</dd><dt><b>

*<proc\_condition\>*

</b></dt>
<dd>

Defines variable conditions.

```
<proc_condition> ::= 
 <variable_name> CONDITION 
 | <variable_name> CONDITION FOR <sql_error_code>

```



</dd><dt><b>

*<proc\_handler\_list\>*

</b></dt>
<dd>

Declares exception handlers to catch SQL exceptions.

```
<proc_handler_list> ::= <proc_handler> [, <proc_handler> [,…] ]

<proc_handler> ::= DECLARE { EXIT | CONTINUE } HANDLER FOR <proc_condition_value_list> <proc_stmt>;
```



</dd><dt><b>

*<proc\_condition\_value\_list\>*

</b></dt>
<dd>

Specifies one or more condition values.

```
<proc_condition_value_list> ::= 
 <proc_condition_value> [, <proc_condition_value> [,...] ]
```



</dd><dt><b>

*<proc\_condition\_value\>*

</b></dt>
<dd>

Specifies a specific error code number or condition name declared on a condition variable.

```
<proc_condition_value> ::=
 SQLEXCEPTION
 | SQLWARNING
 | <sql_error_code>
 | <condition_name>
```



</dd><dt><b>

*<proc\_stmt\_list\>*

</b></dt>
<dd>

Specifies statements for the procedure body.

```
<proc_stmt_list> ::= <proc_stmt> [ <proc_stmt> [...] ]

<proc_stmt> ::= 
 <proc_block>
 | <proc_assign>
 | <proc_tabvar_search>
 | <proc_single_assign>
 | <proc_multi_assign>
 | <proc_if>
 | <proc_loop>
 | <proc_while>
 | <proc_for>
 | <proc_foreach>
 | <proc_exit>
 | <proc_continue>
 | <proc_signal>
 | <proc_resignal>
 | <proc_sql>
 | <proc_open>
 | <proc_fetch>
 | <proc_close>
 | <proc_call>
 | <proc_exec>
 | <proc_return>
 | <proc_insert>
 | <proc_update>
 | <proc_delete>
```



</dd><dt><b>

*<proc\_block\>*

</b></dt>
<dd>

Nests a section of the procedure by using the BEGIN and END keywords.

```
<proc_block> ::=
 BEGIN <proc_block_option> 
   [ <proc_decl_list> ] 
   [ <proc_handler_list> ]
   <proc_stmt_list> 
 END;
```

```
<proc_block_option> ::=
 [ SEQUENTIAL EXECUTION ] [ AUTONOMOUS TRANSACTION ]
 | [ AUTONOMOUS TRANSACTION ] [ SEQUENTIAL EXECUTION ]
```

The autonomous transaction is independent from the main procedure. Changes made and committed by an autonomous transaction can persist regardless of whether the main procedure transaction is committed or rolled back. The end of the autonomous transaction block has an implicit commit.



</dd><dt><b>

*<proc\_assign\>*

</b></dt>
<dd>

Assigns values to variables.

```
<proc_assign> ::= 
 <variable_name> = { <expression> | <array_function> };
 | <variable_name> '[' <expression> ']' = <expression>;
```

*<expression\>* is either a simple expression such as a character, a date, or a number, or it can be a scalar function.



</dd><dt><b>

*<proc\_tabvar\_search\>*

</b></dt>
<dd>

Searches for key value pairs in a table variable.

The position of the first matching record is returned, or NULL if no record matches. This result can be used in conjunction with other table variable operators \(DELETE and UPDATE\).

```
<proc_tabvar_search> ::= 
POS = <table_variable>.SEARCH( ( <column_list> ), ( <value_list> ) [, <start_position> ] )

<column_list> ::= <column1> [, <column2> [,..] ]
<value_list> ::= <value1> [, <value2> [,..] ]
<start_position> ::= <expression>

```

POS= is part of the required syntax. For example, specify `POS=:myTabVar.SEARCH(("key1", "key2"), ("I", 3));` to search for values "I" and 3 in columns key1 and key2, respectively, of the myTabVar table variable.


<dl>
<dt><b>

*<table\_variable\>*

</b></dt>
<dd>

Specifies the table variable to search.



</dd><dt><b>

*<column\_list\>* and *<value\_list\>*

</b></dt>
<dd>

Specifies the values to search for in the columns. The SAP HANA server pairs the columns listed with the values listed, thus forming the key-value pairs to search for. The number of items in *<column\_list\>* must be the same as the number of items in *<value\_list\>*. A column can be listed more than once in *<column\_list\>*, just as a value can be listed more than once in *<value\_list\>*.



</dd><dt><b>

*<start\_position\>*

</b></dt>
<dd>

Specifies the row to start with. The default value is 1, which specifies to scan all data starting at the beginning row. *<expression\>* can be any valid expression that resolves to a positive integer.



</dd>
</dl>



</dd><dt><b>

*<array\_function\>*

</b></dt>
<dd>

Specifies an array function.

```
<array_function> ::=
 ARRAY_AGG ( <table_variable>.<column_name> [ ORDER BY <sort_spec_list> ] ) 
 | CARDINALITY ( <array_variable_name> ) 
 | TRIM_ARRAY  ( <array_variable_name>,<array_variable_name>) 
 | ARRAY ( <array_variable_name_list> ) 

<table_variable> ::= <identifier>

<column_name> ::= <identifier>

<array_variable_name> ::= <identifier>
```

The ARRAY\_AGG function returns the array by aggregating the set of elements in the specified column of the table variable. Ordering the elements is optional.

The CARDINALITY function returns the number for the element in the array *<array\_variable\_name\>*.

The TRIM\_ARRAY function returns the new array by removing the given number of elements, *<numeric\_value\_expression\>*, from the end of the array, *<array\_value\_expression\>*.

The ARRAY function returns an array whose elements are specified in the list *<array\_variable\_name\>*. For more information, see *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



</dd><dt><b>

*<proc\_single\_assign\>*

</b></dt>
<dd>

Assigns values to a list of variables with only one function evaluation.

```
<proc_single_assign> ::= 
 <variable_name> = <subquery> 
 |  <variable_name> = <proc_apply_filter>
 |  <variable_name> = <unnest_function>
 |  <variable_name> = <match_merge_op>
```



</dd><dt><b>

*<proc\_multi\_assign\>*

</b></dt>
<dd>

Assigns values to a list of variables with multiple function evaluations.

```
<proc_multi_assign> ::= ( <variable_name_list> ) = <function_expression>
```

*<function\_expression\>* is a scalar user-defined function and the number of elements in *<variable\_name\_list\>* equal the number of output parameters of the scalar user-defined function.



</dd><dt><b>

*<proc\_apply\_filter\>*

</b></dt>
<dd>

Defines a dynamic WHERE condition that is applied at runtime.

```
<proc_apply_filter> ::= 
 APPLY_FILTER ( {<table_name> | <table_variable>}, <variable_name> );
```

For more information about APPLY\_FILTER, see *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



</dd><dt><b>

*<unnest\_function\>*

</b></dt>
<dd>

Returns a table, including a row for each element of the specified array.

```
<unnest_function> ::=
 UNNEST ( <variable_name_list> ) [ WITH ORDINALITY ] [ <as_col_names> ];

<variable_name_list> ::= <variable_name> [, <variable_name> [,...] ]
```


<dl>
<dt><b>

WITH ORDINALITY

</b></dt>
<dd>

Appends an ordinal column to the return values.



</dd><dt><b>

*<as\_col\_names\>*

</b></dt>
<dd>

Specifies the column names of the return table.

```
<as_col_names> ::= AS [ <table_name> ] ( <column_name_list> ) 

<column_name_list> ::= <column_name> [, <column_name> [,...] ]

<column_name> ::= <identifier>
```



</dd>
</dl>



</dd><dt><b>

*<map\_merge\_op\>*

</b></dt>
<dd>

Applies each row of the input table to the mapper function and unites all intermediate result tables. For more information about the MAP\_MERGE operator, see the *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.

```
<map_merge_op> ::= 
MAP_MERGE ( <table_or_table_variable>, <mapper_identifier> ( <table_or_table_variable>.<column_name> [,...] [, <param_list> ])

<table_or_table_variable> ::= <table_variable_name> | <identifier> 
<table_variable_name> ::= <identifier> 
<mapper_identifier> ::= <identifier>
<column_name> ::= <identifier>
<param_list> ::= <param> [,...] 

<param> ::= 
 <table_or_table_variable> 
 | <string_literal> 
 | <numeric_literal> 
 | <identifier>
```



</dd><dt><b>

*<proc\_if\>*

</b></dt>
<dd>

Controls the execution flow with conditionals.

```
<proc_if> ::=
 IF <condition> THEN [ SEQUENTIAL EXECUTION ]
    [ <proc_decl_list> ]
    [ <proc_handler_list> ]
    <proc_stmt_list>
    [ <proc_elsif_list> ]
    [ <proc_else> ]
 END IF;

<proc_elsif_list> ::= 
 ELSEIF <proc_decl_list> ] [ <proc_handler_list> ] <proc_stmt_list> 

<proc_else> ::= 
 ELSE [ SEQUENTIAL EXECUTION ] [ <proc_decl_list> ] [ <proc_handler_list> ] <proc_stmt_list>
```


<dl>
<dt><b>

*<proc\_loop\>*

</b></dt>
<dd>

Uses a loop to repeatedly execute a set of statements.

```
<proc_loop> ::=
 LOOP [ SEQUENTIAL EXECUTION ]
    [ <proc_decl_list> ]
    [ <proc_handler_list> ]
    <proc_stmt_list>
 END LOOP;
```



</dd><dt><b>

*<proc\_while\>*

</b></dt>
<dd>

Specifies that a set of trigger statements is repeatedly called while a condition is true.

```
<proc_while> ::=
 WHILE <condition> DO [ SEQUENTIAL EXECUTION ]
    [ <proc_decl_list> ]
    [ <proc_handler_list> ]
    <proc_stmt_list>
 END WHILE;
```



</dd><dt><b>

*<proc\_for\>*

</b></dt>
<dd>

Specifies a FOR...IN loop that iterates over a set of data.

```
<proc_for> ::=
 FOR <column_name> IN [ REVERSE ] <expression> [...]  <expression> 
   DO [ SEQUENTIAL EXECUTION ]
     [ <proc_decl_list> ]
     [ <proc_handler_list> ]
     <proc_stmt_list>
 END FOR;
```



</dd><dt><b>

*<proc\_foreach\>*

</b></dt>
<dd>

Specifies a FOR...EACH loop that iterates over all elements in a set of data.

```
<proc_foreach> ::=
 FOR <column_name> AS <column_name> [ <open_param_list> ]
   DO [ SEQUENTIAL EXECUTION ]
     [ <proc_decl_list> ]
     [ <proc_handler_list> ]
     <proc_stmt_list>
 END FOR;

<open_param_list> ::= ( <expression> [, <expression> [,...] )
```



</dd><dt><b>

*<proc\_exit\>*

</b></dt>
<dd>

Terminates a loop.

```
<proc_exit> ::= BREAK;
```



</dd><dt><b>

*<proc\_continue\>*

</b></dt>
<dd>

Skips a current loop iteration and continues with the next value.

```
<proc_continue> ::= CONTINUE;
```



</dd><dt><b>

*<proc\_signal\>*

</b></dt>
<dd>

Explicitly raises an exception from within your trigger procedures.

```
<proc_signal> ::=
 SIGNAL <signal_value> [ <set_signal_info> ];
```



</dd><dt><b>

*<proc\_resignal\>*

</b></dt>
<dd>

Raises an exception on the action statement in an exception handler.

```
<proc_resignal> ::=
 RESIGNAL [ <signal_value> ] [ <set_signal_info> ];
```

If an error code is not specified, then RESIGNAL throws the caught exception.



</dd><dt><b>

*<signal\_value\>*

</b></dt>
<dd>

Specifies a SIGNAL or RESIGNAL for a signal name or an SQL error code.

```
<signal_value> ::= <signal_name> | <sql_error_code>

<signal_name> ::= <identifier>

<sql_error_code> ::= <unsigned_integer>
```



</dd><dt><b>

*<set\_signal\_info\>*

</b></dt>
<dd>

Specifies that an error message is delivered to users when a specified error is thrown during procedure execution.

```
<set_signal_info> ::= SET MESSAGE_TEXT = '<message_string>'

<message_string> ::= <any_character>
```



</dd><dt><b>

*<proc\_sql\>*

</b></dt>
<dd>

Specifies an SQL statement.

```
<proc_sql> ::=
 <subquery>
 | <select_into_stmt>
 | <select_from_embedded_function_stmt>
 | <insert_stmt>  
 | <delete_stmt> 
 | <update_stmt>  
 | <replace_stmt>  
 | <call_stmt>   
 | <create_table_stmt> 
 | <drop_table_stmt> 
```

*<select\_from\_embedded\_function\_stmt\>* and *<select\_into\_stmt\>* are for use exclusively in a SQLScript procedure body context. For all other SQL statements in *<proc\_sql\>*, refer to the topic for that specific statement found in this guide. For example, for more information on *<insert\_stmt\>*, see the INSERT Statement topic in this guide.


<dl>
<dt><b>

*<select\_from\_embedded\_function\_stmt\>*

</b></dt>
<dd>

Selects from an embedded function.

```
<select_from_embedded_function> ::= 
SELECT <select_list> FROM SQL FUNCTION <embedded_func_returns> BEGIN <sqlscript_body> END

<embedded_func_returns> = RETURNS { <table_ref> | ( <opt_cv_array_column_list> ) | <proc_param_name> <func_data_type> }
```

Any query with SQL FUNCTION in the body is not cached in SQL plan cache.

Queries with SQL FUNCTION can be used in SELECT or DML statements, not inside a DDL definition, and not inside a DO BEGIN...END or another SQL FUNCTION block.

For examples of how to use embedded SQL functions in the body of a SQLScript procedure, see the SAP HANA SQLScript reference guide.



</dd><dt><b>

*<select\_into\_stmt\>*

</b></dt>
<dd>

Specifies a query.

```
<select_into_stmt> ::= SELECT <select_list> INTO <variable_name_list> [ DEFAULT <scalar_expr_list> ]
 <from_clause>
 [ <where_clause> ]
 [ <group_by_clause> ]
 [ <having_clause> ] 
 [ {<set_operator> <subquery>, ... } ]
 [ <order_by_clause> ] 
 [ <limit> ];
```

For information on *<select\_list\>*, *<from\_clause\>*, *<where\_clause\>*, *<group\_by\_clause\>*, *<having\_clause\>*, *<set\_operator\>*, *<subquery\>*, *<order\_by\_clause\>*, and *<limit\>*, see the SELECT statement.



</dd>
</dl>



</dd><dt><b>

*<variable\_name\_list\>*

</b></dt>
<dd>

Specifies a variable list.

```
<variable_name_list> ::= <variable_name>[{, <variable_name>}...]

<variable_name> ::= <identifier>
```

*<variable\_name\>* is a scalar variable. You can assign a selected item value to this scalar variable.



</dd><dt><b>

*<proc\_open\>*

</b></dt>
<dd>

Controls cursor operations.

```
<proc_open> ::=
 OPEN <cursor_name> [ <open_param_list> ];

<proc_fetch> ::=
 FETCH <cursor_name> INTO <column_name_list>;

<proc_close> ::= CLOSE <cursor_name>;
```



</dd><dt><b>

*<proc\_call\>*

</b></dt>
<dd>

Calls a procedure using the CALL statement. See [CALL Statement \(Procedural\)](call-statement-procedural-20d364c.md).



</dd><dt><b>

*<proc\_exec\>*

</b></dt>
<dd>

Makes a dynamic SQL call.

```
<proc_exec> ::= 
 EXEC '<sql-statement>' [ INTO <variable_name_list> [ DEFAULT <scalar_expr_list> ] ] [ USING <expression_list> ] [ READS SQL DATA ];
 | EXECUTE IMMEDIATE '<sql-statement>' [ INTO <variable_name_list> [ DEFAULT <scalar_expr_list> ] ] [ USING <expression_list> ] [ READS SQL DATA ];

<variable_name_list> ::= <variable_name>[,...]
<variable_name> ::= <identifier>
<expression_list> ::= <expression>[,...]
```

EXEC executes *<sql-statement\>* passed as a string argument. EXEC does not return a result set if *<sql-statement\>* is a SELECT statement. Use EXECUTE IMMEDIATE for that purpose. If the query returns result sets or output parameters, then you can assign the values to scalar or table variables with the INTO clause.

When *<sql-statement\>* is a SELECT statement and table variables are listed in the INTO clause, result sets are assigned to the table variables sequentially. If scalar variables are listed in the INTO clause for a SELECT statement, then it works like *<select\_into\_stmt\>* and assigns the value of each column of the first row to a scalar variable when a single row is returned from a single result set. When the SQL statement is a CALL statement, output parameters represented as ':*<variable\_name\>*' in the SQL statement are assigned to the variables in the INTO clause according to the variable name.

If *<sql-statement\>* returns a single row, then you can assign the value of each column to a scalar variable by specifying the INTO *<variable\_name\_list\>* clause.

Bind scalar values by specifying the USING *<expression\_list\>* clause. *<expression\>* can be either a simple expression, such as a character, a date, or a number, or it can be a scalar variable.

READS SQL DATA specifies that the dynamic SQL call is read only and will not make modifications to the database data or its structure.



</dd><dt><b>

*<proc\_return\>*

</b></dt>
<dd>

Returns a value from a procedure.

```
<proc_return> ::= RETURN [ <proc_expr> ];
```

For more information about SQLScript, see *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



</dd><dt><b>

*<proc\_insert\>*

</b></dt>
<dd>

Inserts a new data record into a table variable at a specific position.

```
<proc_insert> ::= :<table_variable>.INSERT((<value>[,…] ), <index>)
```

All existing data records at the positions starting from the given index are moved to the next position. If the index is greater than the original table size, then the records between the inserted record and the original last record are initialized with NULL values.



</dd><dt><b>

*<proc\_update\>*

</b></dt>
<dd>

Updates a data record at a specific position in a table variable. There are two syntaxes for *<proc\_update\>*:

```
<proc_update> ::= :<table_variable>.UPDATE((<value>[,…] ), <index>))

<proc_update> ::= :<table_variable>[ <index> ] = (<value>[,…])

```

If *<index\>* is greater than the table size, then no operation is performed.



</dd><dt><b>

*<proc\_delete\>*

</b></dt>
<dd>

Deletes a data record at a specific position in a table variable.

```
<proc_delete> ::= :<table_variable>.DELETE(<index>)

```

If *<index\>* is greater than the table size, then no operation is performed.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

HEADER ONLY

</b></dt>
<dd>

Specifies that only the properties of the procedure are created along with the OID and no procedure dependencies exist.

Once the headers are replaced with full procedure definitions, dependencies are created while the procedure OID remains the same. Dependencies appear in the OBJECT\_DEPENDENCIES system view. HEADER ONLY is useful when several dependent procedures must be created.



</dd>
</dl>



<a name="loio20d467407519101484f190f545d54b24__sql_create_procedure_1sql_create_procedure_description"/>

## Description

The CREATE PROCEDURE statement creates a procedure using the specified programming language *<lang\>*.

For more information about SQLScript, see *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.

**CREATE OR REPLACE behavior:**

-   The behavior of CREATE OR REPLACE depends on the existence of a pre-defined procedure: If there is no existing procedure, then it behaves like CREATE PROCEDURE; otherwise, it behaves like ALTER PROCEDURE.

-   Explicitly set all parameters where the desired setting is different from the default \(for example, settings for the procedure language, the default schema, whether the procedure is deterministic or encrypted, sequential execution options, and so on\). Everything not specified in a CREATE OR REPLACE PROCEDURE statement is reset to its default.

-   If you specify the security mode, then the behavior depends on the existence of a pre-defined procedure: If there is no existing procedure, then the operation succeeds \(the procedure is created\). If the procedure exists, and the security mode is different, then an error is returned.

-   CREATE OR REPLACE does not change any DDL settings for the procedure, such as grant privileges, dependent objects, and so on.




<a name="loio20d467407519101484f190f545d54b24__sql_create_procedure_1sql_create_procedure_examples"/>

## Examples

**Example - Creating an SQL Script Procedure**

Create an SQLScript procedure with the following definition.

```
CREATE PROCEDURE orchestrationProc
 LANGUAGE SQLSCRIPT AS
 BEGIN
   DECLARE v_id BIGINT;
   DECLARE v_name NVARCHAR(30);
   DECLARE  v_pmnt BIGINT;
   DECLARE v_msg NVARCHAR(200);
   DECLARE CURSOR c_cursor1 (p_payment BIGINT) FOR
     SELECT id, name, payment FROM control_tab
       WHERE payment > :p_payment ORDER BY id ASC;
   CALL init_proc();
   OPEN c_cursor1(250000);
   FETCH c_cursor1 INTO v_id, v_name, v_pmnt; v_msg = :v_name || ' (id ' || :v_id || ') earns ' || :v_pmnt || ' $.';
   CALL ins_msg_proc(:v_msg);
   CLOSE c_cursor1;
 END;
```

The procedure features a number of imperative constructs, including the use of a cursor \(with associated state\) and local scalar variables with assignments.

**Example - Using variable cache**

The following example creates an SQLScript procedure that caches variable X:

```
CREATE TABLE test_cache (a INT);
INSERT INTO test_cache VALUES(5);

CREATE OR REPLACE PROCEDURE test_result_cache 
LANGUAGE SQLSCRIPT
VARIABLE CACHE ON X ENABLE AS
 BEGIN
  x = SELECT * FROM test_cache;
  SELECT * FROM :x; 
 END;
```

**Example - Use of READS SQL DATA with dynamic SQL -**The following examples show how to set dynamic SQL in the body of a procedure to read-only:

```
CREATE PROCEDURE Proc1() READS SQL DATA AS
  BEGIN
      EXEC 'SELECT * FROM DUMMY';
  END;
               
 CREATE PROCEDURE Proc1(IN A NVARCHAR(12)) AS
  BEGIN
      EXECUTE IMMEDIATE 'SELECT * FROM ' || :A READS SQL DATA;
 END;
```

**Related Information**  


[CREATE PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7a2da744ce544db1814a5fff250e99f6.html "You use this SQL statement to create a procedure.") :arrow_upper_right:

[ALTER PROCEDURE](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/042ab4636cf34a9cb88dd61c808861a8.html "") :arrow_upper_right:

[SAP HANA Cloud, SAP HANA SQLScript Reference](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/28f2d64d4fab4e789ee0070be418419d.html "This reference describes how to use the SQL extension SAP HANA SQLScript to embed data-intensive application logic into SAP HANA.") :arrow_upper_right:

[ALTER PROCEDURE Statement \(Procedural\)](alter-procedure-statement-procedural-20d0328.md "Alters a procedure or manually triggers a recompilation of a procedure by generating an updated execution plan.")

[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

[Library Members](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7ed0d89b6aa84696a3ce8cf5a8517415.html "") :arrow_upper_right:

[User-Defined Libraries](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/7cd14f1931404738a05c5e93e22564af.html "") :arrow_upper_right:

[CREATE LIBRARY Statement \(SQLScript\)](create-library-statement-sqlscript-62263ce.md "Creates a SQLScript user-defined library.")

[OBJECT\_DEPENDENCIES System View](../../020-System-Views-Reference/021-System-Views/object-dependencies-system-view-20cbd12.md "Provides information about the dependencies between objects, such as which views refer to a specific table.")

[M\_SQLSCRIPT\_VARIABLE\_CACHE System view](../../020-System-Views-Reference/022-Monitoring-Views/m-sqlscript-variable-cache-system-view-9fb8ca5.md "Provides runtime information about procedures and functions that have variable caches defined.")

