<!-- loio52103853351841f6a1e87f40b2686da9 -->

# DO BEGIN...END Statement \(Procedural\)

Executes an anonymous block a single time.



## Syntax

```
DO 
 [ <named_parameters_list> ] [ ( <bound_parameter_clause> ) ]
  BEGIN [ <block_properties > ] 
    <variable_declaration>
    <statement_list>
  END
```



## Syntax Elements


<dl>
<dt><b>

*<named\_parameters\_list\>*

</b></dt>
<dd>

Specifies the list of named parameters.

```
<named_parameters_list> ::= ( [ <named_parameter>] [ { ,<named_parameter> } … ] )
```


<dl>
<dt><b>

*<named\_parameter\>*

</b></dt>
<dd>

Specifies the name of the parameter.

```
<named_parameter> ::= <parameter_mode>, <parameter_name>, <type_name>
```



</dd>
</dl>



</dd><dt><b>

*<bound\_parameter\_clause\>*

</b></dt>
<dd>

Specifies the input and output parameters for the procedure with value bindings.

```
<bound_parameter_clause> ::= <bound_parameter> [, … ]
```


<dl>
<dt><b>

*<bound\_parameter\>*

</b></dt>
<dd>

Specifies a procedure parameter with its associated data type and value binding.

```
<bound_parameter> ::= <parameter> => <proc_param>
```



</dd><dt><b>

*<proc\_param\>*

</b></dt>
<dd>

Specifies procedure parameters.



</dd>
</dl>



</dd><dt><b>

*<block\_properties\>*

</b></dt>
<dd>

Specifies one or more properties to apply to the block.

```
<block_properties> ::= 
 SEQUENTIAL EXECUTION
 | PARALLEL EXECUTION
 | AUTONOMOUS TRANSACTION
```


<dl>
<dt><b>

SEQUENTIAL EXECUTION

</b></dt>
<dd>

Specify SEQUENTIAL EXECUTION to sequence the execution of independent DML statements and read-write procedure calls.



</dd><dt><b>

PARALLEL EXECUTION

</b></dt>
<dd>

Specify PARALLEL EXECUTION to parallelize the execution of independent DML statements and read-write procedure calls.



</dd><dt><b>

AUTONOMOUS TRANSACTION

</b></dt>
<dd>

Specify AUTONOMOUS TRANSACTION if you want the block to be executed independently of the main procedure. Changes made and committed using AUTONOMOUS TRANSACTION persist regardless of whether the main procedure transaction is committed or rolled back. The end of an AUTONOMOUS TRANSACTION block has an implicit commit.



</dd>
</dl>



</dd><dt><b>

*<variable\_declaration\>*

</b></dt>
<dd>

Declares variables for use in anonymous block.

```
<variable_declaration> ::= 
 <declaration> 
 [ <declaration> ]
 […] 

<declaration> ::= 
 DECLARE <variable_name> { <sql_data_type> | TABLE ( <column_definition> [,…] [ SEARCH KEY ( <column_name> [,…] ) ; 
 | DECLARE <variable_name> AUTO <default_value>;

 <column_definition> ::= <column_name> <sql_data_type>
 <default_value> ::= { ( DEFAULT | := | = ) { <value> | <expression> }
```

Specifying AUTO allows you to declare a variable and its default value without having to explicitly set the data type.



</dd><dt><b>

*<statement\_list\>*

</b></dt>
<dd>

Specifies one or more statements to execute as part of the anonymous block.



</dd>
</dl>



## Description

An anonymous block is only executed once. All SQLScript statements supported in procedures are also supported in anonymous blocks. Unlike procedures, an anonymous block has no corresponding object created in the catalog.

Anonymous blocks are defined and executed in a single step. Therefore, lifecycle handling like CREATE or DROP is not needed. The body of an anonymous block is similar to the procedure body.

To return a result set, use a SELECT statement because anonymous blocks do not have any parameters defined.

For output parameters, ***?*** is a valid value and cannot be omitted because otherwise the query parameter cannot be bound. For input parameters, the name of a physical table can be set. For scalar input parameters, any scalar expression can be used, except for scalar UDF. DEFAULT EMPTY and INOUT parameters are not supported.



## Examples

Execute an anonymous block that creates a table and inserts values into that table.

```
DO
BEGIN
    DECLARE I INTEGER;
    CREATE ROW TABLE TAB1 (I INTEGER); 
    FOR I IN 1..10 DO
        INSERT INTO TAB1 VALUES (:I);
    END FOR;
END;
```

Execute an anonymous block and return the result set by using a SELECT statement.

```
DO
BEGIN
    T1 = SELECT I, 10 AS J FROM TAB;
    T2 = SELECT I, 20 AS K FROM TAB;
    T3 = SELECT J, K FROM :T1, :T2 WHERE :T1.I = :T2.I;
    SELECT * FROM :T3;
END;
```

Execute an anonymous block that calls another procedure.

```
DO
BEGIN
    T1 = SELECT * FROM TAB;
    CALL PROC3(:T1, :T2);
    SELECT * FROM :T2;
END;
```

Execute an anonymous block that includes an exception handler.

```
DO
BEGIN
    DECLARE I, J INTEGER;
    BEGIN
        DECLARE EXIT HANDLER FOR SQLEXCEPTION
        IF ::SQL_ERROR_CODE = 288 THEN
            DROP TABLE TAB;
            CREATE ROW TABLE TAB (I INTEGER PRIMARY KEY);
        ELSE
            RESIGNAL;
        END IF;

        CREATE ROW TABLE TAB (I INTEGER PRIMARY KEY);
    END;

    FOR I in 1..3 DO
        INSERT INTO TAB VALUES (:I);
    END FOR;

    IF :J <> 3 THEN
        SIGNAL SQL_ERROR_CODE 10001;
    END IF;
END;
```

Execute an anonymous block that uses COMMIT and ROLLBACK.

```
DO
BEGIN
    CREATE ROW TABLE TAB2 (K INT);
    COMMIT; 
    DROP TABLE TAB;
    CREATE ROW TABLE TAB (J INT);
    ROLLBACK;
    DELETE FROM TAB;
END;
```

Execute an anonymous block that calls a procedure to process the selected data.

```
DO
  BEGIN
    T1 = SELECT I, 10 AS J FROM TAB;
    T2 = SELECT I, 20 AS K FROM TAB;
    T3 = SELECT J, K FROM :T1, :T2 WHERE :T1.I = :T2.I;
    CALL PROC3(:T3, T4);
    SELECT * FROM :T4;
  END;
```

Execute an anonymous block that runs a loop to insert data into a table.

```
DO
  BEGIN
    DECLARE I INTEGER;
    FOR I in 1..3 DO
        INSERT INTO TAB VALUES (:I);
      END FOR;
  END;
```

Execute an anonymous block that computes the sum of two integers.

```
DO (IN A INT => 1, IN B INT => ?, OUT C INT => ?)
BEGIN
    C = :A + :B;
END;
```

**Related Information**  


[Anonymous Block](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/dec9d68044bd49bcbb45c990ba49c81d.html "An anonymous block is an executable DML statement which can contain imperative or declarative statements.") :arrow_upper_right:

[Explicit Parallel Execution](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2024_3_QRC/en-US/8db200a4f585490c81c4930689ec1a5c.html "") :arrow_upper_right:

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

