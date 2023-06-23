<!-- loio20d5a65575191014946db96aaedbef5b -->

# CREATE TRIGGER Statement \(Data Definition\)

Creates a trigger on a table or view.



<a name="loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_syntax"/>

## Syntax

```
CREATE [ OR REPLACE ] TRIGGER <trigger_name> <trigger_action_time> <trigger_event_list>
   ON <subject_table_name>
   [ REFERENCING <transition_list> ] 
   [ <for_each> ] 
   [ <trigger_order_clause> ]
   [ ONLINE ]
      BEGIN 
         [ <trigger_decl_list> ]
         [ <proc_handler_list> ]
         <trigger_stmt_list>
      END
```



<a name="loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces the definition of the trigger if it already exists. A CREATE OR REPLACE operation does not change the ID of the trigger, nor any privileges associated with it.



</dd><dt><b>

*<trigger\_name\>*

</b></dt>
<dd>

Specifies the name of the trigger to be created, with optional schema name.

```
<trigger_name> ::= [<schema_name>.]<identifier>
 
<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<trigger\_action\_time\>*

</b></dt>
<dd>

Specifies when the trigger action should occur.

```
<trigger_action_time> ::= 
 BEFORE 
 | AFTER  
 | INSTEAD OF
```


<dl>
<dt><b>

BEFORE

</b></dt>
<dd>

Specifies that the trigger is executed before the DML operation on a table.



</dd><dt><b>

AFTER

</b></dt>
<dd>

Specifies that the trigger is executed after the DML operation on a table.



</dd><dt><b>

INSTEAD OF

</b></dt>
<dd>

Specifies that the trigger is executed instead of the DML operation on a view.

A view with an INSTEAD OF trigger becomes updatable. An INSTEAD OF trigger is only allowed for SQL views, not for tables or column views.

UPDATE with FROM clause and REPLACE DML is not allowed when an INSTEAD OF trigger exists.

This option is not supported within the FOR EACH clause.



</dd>
</dl>



</dd><dt><b>

*<trigger\_event\_list\>*

</b></dt>
<dd>

Specifies the data modification command that activates the trigger action.

```
<trigger_event_list> ::= 
 <trigger_event> 
 | <trigger_event_list> OR <trigger_event>
 
<trigger_event> ::= 
 INSERT 
 | DELETE 
 | UPDATE [ [ EXCEPT ] OF <column_name_list> ]
 
<column_name_list> ::= <column_name> [ , <column_name>}...]
 
<column_name> ::= <identifier>
```

If *<column\_name\_list\>* is provided with the UPDATE OF clause, then the UPDATE trigger only fires if a column specified in the list is updated. If *<column\_name\_list\>* is provided with the UPDATE EXCEPT OF clause, then the UPDATE trigger is not fired if a column specified in the list is updated. The UPDATE trigger is fired regardless of the UPDATE EXCEPT OF clause if columns that are not specified in the list are updated together.



</dd><dt><b>

*<subject\_table\_name\>*

</b></dt>
<dd>

Specifies the subject table or view name.

```
<subject_table_name> ::= <identifier>
```



</dd><dt><b>

REFERENCING *<transition\_list\>*

</b></dt>
<dd>

When a trigger transition variable is declared, the trigger can access records that are being changed by the DML triggering the trigger. For more information, see [Transition variable](create-trigger-statement-data-definition-20d5a65.md#loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_example_transition_variable) and [Transition table](create-trigger-statement-data-definition-20d5a65.md#loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_example_transition_table).


<dl>
<dt><b>

*<transition\_list\>*

</b></dt>
<dd>

Specifies one or more transition list entries.

```
<transition_list> ::= <transition> [ , <transition>...]
```



</dd><dt><b>

*<transition\>*

</b></dt>
<dd>

Specifies a transition variable or table variable.

```
<transition> ::= <transition_variable> | <transition_table>
```



</dd><dt><b>

*<transition\_variable\>*

</b></dt>
<dd>

During row-level trigger execution, *<trans\_var\_name\>*.*<column\_name\>* represents a single record from the corresponding column that is being changed by the DML.

```
<transition_variable> ::= { OLD | NEW } ROW [ AS ] <trans_var_name>
 
<trans_var_name> ::= <identifier>
```

*<column\_name\>* is the target tables column name. Only a ROW trigger can use a transition variable.



</dd><dt><b>

*<transition\_table\>*

</b></dt>
<dd>

During statement-level trigger execution, *<trans\_tab\_name\>* represents records being changed by the trigger DML as a table variable.

```
<transition_table> ::= { OLD | NEW } TABLE [ AS ] <trans_tab_name>
 
<trans_tab_name> ::= <identifier>
```

Only statement triggers can use a transition table.



</dd><dt><b>

OLD

</b></dt>
<dd>

Specifies that you can access the old row of the DML in the trigger. This is the row that is replaced by an update or a deleted old row. UPDATE triggers and DELETE triggers can have OLD ROW transition variables or OLD TABLE transition table variables.



</dd><dt><b>

NEW

</b></dt>
<dd>

Specifies that you can access the new record of the DML in the trigger. This is the row that is inserted or the new updated row.

UPDATE triggers and INSERT triggers can have NEW ROW transition variables or NEW TABLE transition table variables.



</dd>
</dl>



</dd><dt><b>

*<for\_each\>*

</b></dt>
<dd>

Specifies whether the trigger is called in a row-wise or statement-wise fashion.

```
<for_each> ::= FOR EACH { ROW | STATEMENT }
```

The default is ROW.


<dl>
<dt><b>

ROW

</b></dt>
<dd>

Specifies that a row-level trigger is used. This is fired once for each row affected by the triggering event.



</dd><dt><b>

STATEMENT

</b></dt>
<dd>

Specifies that a statement-level trigger is used. This is fired once for each triggering event. Both row-store and column-store tables support statement level triggers



</dd>
</dl>



</dd><dt><b>

*<trigger\_order\_clause\>*

</b></dt>
<dd>

Specifies the order in which the triggers are executed.

```
<trigger_order_clause> ::= { FOLLOWS | PRECEDES <trigger_name_list> }

<trigger_name_list> ::= <trigger_name> [,...]
```


<dl>
<dt><b>

FOLLOWS

</b></dt>
<dd>

Specifies that the trigger being created is fired after the specified triggers in *<trigger\_name\_list\>*.



</dd><dt><b>

PRECEDES

</b></dt>
<dd>

Specifies that the trigger being created is fired before the specified triggers in *<trigger\_name\_list\>*.



</dd>
</dl>



</dd><dt><b>

ONLINE

</b></dt>
<dd>

Applies an intentional exclusive lock \(instead of an exclusive lock\) before performing the operation. An intentional exclusive lock differs from the default lock \(exclusive\) because it allows concurrent DML and DDL related to the object to proceed, and will retry the operation until it can proceed.

ONLINE applies an intentional exclusive lock only if the auto commit mode for DDL statements is set to on. If the auto commit mode for DDL statement is not set to on, then an exclusive lock is still applied.



</dd><dt><b>

*<trigger\_decl\_list\>*

</b></dt>
<dd>

Specifies the trigger declaration.

```
<trigger_decl_list> ::= DECLARE <trigger_decl> [ … ]
```


<dl>
<dt><b>

*<trigger\_decl\>*

</b></dt>
<dd>

Declares trigger variables or trigger conditions.

```
<trigger_decl> ::= 
 <trigger_var_decl>  
 | <trigger_condition_decl>
```

The declared variable can be used as a scalar value assignment or referenced in a trigger SQL statement.



</dd><dt><b>

*<trigger\_var\_decl\>*

</b></dt>
<dd>

Specifies the trigger variable declaration.

```
<trigger_var_decl> ::= 
 <var_name> [ CONSTANT ] <data_type> [ NOT NULL ] [<trigger_default_assign>];
```



</dd><dt><b>

*<var\_name\>*

</b></dt>
<dd>

Specifies the identifier of the trigger variable.

```
<var_name> ::= <identifier>
```



</dd><dt><b>

CONSTANT

</b></dt>
<dd>

Specifies that you cannot change the variable during trigger execution.



</dd><dt><b>

*<data\_type\>*

</b></dt>
<dd>

Specifies the data type of the trigger variable.

```
<data_type> ::= 
 DATE 
 | TIME 
 | SECONDDATE 
 | TIMESTAMP 
 | TINYINT 
 | SMALLINT 
 | INTEGER 
 | BIGINT 
 | SMALLDECIMAL 
 | DECIMAL 
 | REAL 
 | DOUBLE
 | NVARCHAR
 | VARBINARY 
 | BLOB 
 | CLOB 
 | NCLOB 
```



</dd><dt><b>

*<trigger\_default\_assign\>*

</b></dt>
<dd>

Specifies the default value of the trigger variable.

```
<trigger_default_assign> ::= { DEFAULT <expression> | <expression> }
```



</dd><dt><b>

*<trigger\_condition\_decl\>*

</b></dt>
<dd>

Specifies the condition handler declaration.

```
<trigger_condition_decl> ::= 
 <condition_name> CONDITION;
 | <condition_name> CONDITION FOR <sql_error_code>;
```



</dd><dt><b>

*<condition\_name\>*

</b></dt>
<dd>

Specifies a declared condition name that you can reference in an exception handler.

```
<condition_name> ::= <identifier> 
```



</dd><dt><b>

*<sql\_error\_code\>*

</b></dt>
<dd>

Specifies the error code for exception handling.

```
<sql_error_code> ::= SQL_ERROR_CODE <int_const>
```



</dd>
</dl>



</dd><dt><b>

*<proc\_handler\_list\>*

</b></dt>
<dd>

Declares exception handlers to catch SQL exceptions.

```
<proc_handler_list> ::= <proc_handler> [ <proc_handler> […] ]
 
<proc_handler> ::= 
 DECLARE EXIT HANDLER FOR <proc_condition_value_list> <trigger_stmt>
```


<dl>
<dt><b>

*<proc\_condition\_value\_list\>*

</b></dt>
<dd>

Specifies one or more condition values.

```
<proc_condition_value_list> ::= 
 <proc_condition_value> [,...]
```



</dd><dt><b>

*<proc\_condition\_value\>*

</b></dt>
<dd>

Specifies a procedure condition value.

```
<proc_condition_value> ::= 
 SQLEXCEPTION     
 | SQLWARNING
 | <sql_error_code> 
 | <condition_name>
```

You can use a specific error code number or condition name declared on a condition variable.



</dd>
</dl>



</dd><dt><b>

*<trigger\_stmt\_list\>*

</b></dt>
<dd>

Specifies that the trigger body syntax is a subset of the procedure body syntax.

```
<trigger_stmt_list> ::= <trigger_stmt> [ <trigger_stmt> […] ]
 
<trigger_stmt> ::= 
 <proc_block>   
 | <proc_assign>    
 | <proc_if>        
 | <proc_loop>  
 | <proc_while>     
 | <proc_for>   
 | <proc_foreach>
 | <proc_signal>    
 | <proc_resignal>
 | <trigger_sql>    
 | <trigger_proc_call>   
 | <proc_exit>
 | <proc_continue>
 | <proc_open>
 | <proc_fetch>
 | <proc_close>
 | <proc_return>
```

For more information, see the CREATE PROCEDURE statement.


<dl>
<dt><b>

*<proc\_block\>*

</b></dt>
<dd>

Specifies sections of your trigger procedures that can be nested using BEGIN and END terminals.

```
<proc_block> ::= 
 BEGIN 
   [ <trigger_decl_list> ]
   [ <proc_handler_list> ]
   <trigger_stmt_list>
  END;
```



</dd><dt><b>

*<proc\_assign\>*

</b></dt>
<dd>

Assigns values to variables.

```
<proc_assign> ::= <var_name> := <expression>;
 
<var_name> ::= <identifier>
```



</dd><dt><b>

*<proc\_if\>*

</b></dt>
<dd>

Controls execution flow with conditionals.

```
<proc_if> ::= 
 IF <condition> THEN <trigger_stmt_list> [ <proc_elsif_list> ] [ <proc_else> ]
   END IF;

<proc_elsif_list> ::= <proc_elsif> [ <proc_elsif> […] ]

<proc_elsif> ::=
 ELSEIF <condition> THEN <trigger_stmt_list>

<proc_else> ::= ELSE <trigger_stmt_list>
```



</dd><dt><b>

*<condition\>*

</b></dt>
<dd>

Specifies the conditions where the command should be performed.

```
<condition> ::= 
 <condition> OR  <condition>
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>
```



</dd><dt><b>

*<proc\_loop\>*

</b></dt>
<dd>

Repeatedly executes a set of trigger statements.

```
<proc_loop> ::= 
   LOOP 
      <trigger_stmt_list> 
   END LOOP;
```



</dd><dt><b>

*<proc\_while\>*

</b></dt>
<dd>

Repeatedly calls a set of trigger statements while a condition is true.

```
<proc_while> ::= 
   WHILE 
     <condition>
     DO <trigger_stmt_list> 
   END WHILE;
```



</dd><dt><b>

*<proc\_for\>*

</b></dt>
<dd>

Iterates over a set of data.

```
<proc_for> ::= 
 FOR <column_name> IN [ <reverse> ] <expression> [ <expression> […] ]
   DO <trigger_stmt_list>
  END FOR;
```



</dd><dt><b>

*<column\_name\>*

</b></dt>
<dd>

Specifies the name of the column where the data iteration is to occur.

```
<column_name> ::= <identifier>
```



</dd><dt><b>

*<reverse\>*

</b></dt>
<dd>

Specifies that the results should be iterated over in reverse order.

```
<reverse> ::= REVERSE
```



</dd><dt><b>

*<proc\_foreach\>*

</b></dt>
<dd>

Iterates over all elements in a set of data.

```
<proc_foreach> ::= 
 FOR <column_name> AS <column_name> [<open_param_list>]
   DO <trigger_stmt_list>
  END FOR;
```



</dd><dt><b>

*<open\_param\_list\>*

</b></dt>
<dd>

Specifies one or more input expressions to be iterated over.

```
<open_param_list> ::= ( <expr_list> )

<expr_list> ::= <expression>[, <expression> [,…] ]
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
 RESIGNAL [<signal_value>] [ <set_signal_info> ];
```

If an error code is not specified, then RESIGNAL throws the caught exception.



</dd><dt><b>

*<signal\_value\>*

</b></dt>
<dd>

Specifies to SIGNAL or RESIGNAL a signal name or an SQL error code.

```
<signal_value> ::= { <signal_name> | <sql_error_code> }
 
<signal_name> ::= <identifier>
 
<sql_error_code> ::= <unsigned_integer>
```



</dd><dt><b>

*<set\_signal\_info\>*

</b></dt>
<dd>

Delivers an error message to users when specified error is thrown during trigger execution.

```
<set_signal_info> ::= SET MESSAGE_TEXT = '<message_string>'

<message_string> ::= <any_character>
```



</dd><dt><b>

*<trigger\_sql\>*

</b></dt>
<dd>

Specifies the trigger SQL.

```
<trigger_sql> ::= <select_into_stmt>
 | <insert_stmt>
 | <delete_stmt>
 | <update_stmt>
 | <replace_stmt>
 | <upsert_stmt>
```

For information on *<insert\_stmt\>*, see the INSERT statement.

For information on *<delete\_stmt\>*, see the DELETE statement.

For information on *<update\_stmt\>*, see the UPDATE statement.

For information on *<replace\_stmt\>* and *<upsert\_stmt\>*, see the REPLACE | UPSERT statement.



</dd><dt><b>

*<select\_into\_stmt\>*

</b></dt>
<dd>

 

```
<select_into_stmt> ::=
 SELECT <select_list> INTO <var_name_list> <from_clause>
   [ <where_clause> ]
   [ <group_by_clause> ]
   [ <having_clause> ] 
   [ { <set_operator> <subquery> [, ... ] ]
   [ <order_by_clause> ] 
   [ <limit> ]
```



</dd><dt><b>

*<trigger\_proc\_call\>*

</b></dt>
<dd>

Calls a previously defined procedure.

```
<trigger_proc_call> ::= CALL <procedure_name>
```

The called procedure can only include SQL statements that are suitable for triggers.

For information on *<select\_list\>*, *<from\_clause\>*, *<where\_clause\>*, *<group\_by\_clause\>*, *<having\_clause\>*, *<set\_operator\>*, *<subquery\>*, *<order\_by\_clause\>*, and *<limit\>*, see the SELECT statement.



</dd><dt><b>

*<var\_name\_list\>*

</b></dt>
<dd>

Specifies a scalar variable.

```
<var_name_list> ::= <var_name>[, <var_name> [,…] ]
 
<var_name> ::= <identifier>
```

You can assign a selected item value to this scalar variable.



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

Skips current loop iteration and continues with the next value.

```
<proc_continue> ::= CONTINUE;
```



</dd><dt><b>

*<proc\_open\>*

</b></dt>
<dd>

Specifies cursor operations.

```
<proc_open> ::= OPEN <cursor_name> [ <open_param_list> ];

<proc_fetch> ::= FETCH <cursor_name> INTO <column_name_list>;

<proc_close> ::= CLOSE <cursor_name>;
```



</dd><dt><b>

*<proc\_return\>*

</b></dt>
<dd>

Returns from a trigger.

```
<proc_return> ::= RETURN;
```

Cannot return a value.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_description"/>

## Description

A trigger is a kind of procedure that automatically executes when an event occurs on a given table or view. The body of a trigger contains a set of statements that are executed when a given operation \(INSERT/UPDATE/DELETE\) takes place on a given subject table or subject view.

The following notes apply to triggers:

-   Referencing an associated column in the trigger is not allowed because the trigger transition table only has the subject table data in context during the operation.

-   In the case of batch/bulk statements, a statement-level trigger is executed *once per batch entry*. So for example, if inserting a batch, then the statement-level trigger is executed for every INSERT statement entry in the batch.

-   Statement-level triggers are supported for both row-store and column-store tables. You can convert a row table with a statement trigger into a column table by using ALTER TABLE.

-   Modification \(any INSERT/UPDATE/DELETE/REPLACE\) of a subject table that a trigger is defined on is not allowed in the trigger body.

-   A trigger on a partitioned table cannot access the subject table, while a trigger on a non-partitioned table can execute a SELECT statement on its subject table.

-   When a subject table is accessed in a trigger body, batch updates do not always show row-wise results for performance reasons.

-   The maximum trigger number per single table and per DML is 1024, which means a table can have maximum 1024 INSERT triggers, 1024 UPDATE triggers, and 1024 DELETE triggers in the same time.

-   Most procedures are allowed in the body of a trigger. The procedure that is called in a trigger only can have SQL statements which are suitable for a trigger body.

-   Transition variable modifications are allowed in the BEFORE trigger. Internal columns \($trexkey$, $rowid$, concat column\) or generated column modifications are not allowed.

-   Unsupported trigger actions:

    -   Result-set assignments, such as selecting a result set assignment into a table type

    -   Dynamic SQL execution, such as building SQL statements dynamically at SQLScript runtime





<a name="loio20d5a65575191014946db96aaedbef5b__section_eym_xkk_pbb"/>

## Permissions

Only database users with the TRIGGER privilege for the given *<subject\_table\_name\>* are allowed to create a trigger for that table or view.



<a name="loio20d5a65575191014946db96aaedbef5b__sql_create_trigger_1sql_create_trigger_examples"/>

## Examples

**Basic trigger usage**

Create a table that the trigger is created for.

```
CREATE TABLE TARGET ( A INT);
```

Create a table that the trigger accesses and modifies.

```
CREATE TABLE SAMPLE ( A INT);
```

Create the following trigger.

```
CREATE TRIGGER TEST_TRIGGER
 AFTER INSERT ON TARGET FOR EACH ROW
 BEGIN
     DECLARE SAMPLE_COUNT INT;
     SELECT COUNT(*) INTO SAMPLE_COUNT FROM SAMPLE;
     IF :SAMPLE_COUNT = 0
     THEN
       INSERT INTO SAMPLE VALUES(5);
     ELSEIF :SAMPLE_COUNT = 1
     THEN
       INSERT INTO SAMPLE VALUES(6);
     END IF;
 END;
```

TEST\_TRIGGER is executed after any record insert execution for TARGET table.

```
INSERT INTO TARGET VALUES (1);
 SELECT * FROM SAMPLE;
```

The SAMPLE table record count is zero at the first insert attempt and the trigger TEST\_TRIGGER inserts 5 into the SAMPLE table. The SELECT statement returns 5.

```
INSERT INTO TARGET VALUES (2);
 SELECT * FROM SAMPLE;
```

On the second insertion to the TARGET table, the trigger inserts 6 into the SAMPLE table because its count is now two. The SELECT statement returns 6.

**Trigger ordering**

Create the trigger TRIGGER\_TEST\_1 that is executed after an insert execution on TARGET table. TRIGGER\_TEST\_1 is executed following the execution of TEST\_TRIGGER.

```
CREATE TRIGGER TRIGGER_TEST_1
AFTER INSERT ON TARGET
FOR EACH ROW FOLLOWS TEST_TRIGGER
BEGIN
     DECLARE SAMPLE_COUNT INT;
     SELECT COUNT(*) INTO SAMPLE_COUNT FROM SAMPLE;
     IF :SAMPLE_COUNT = 0
     THEN
       INSERT INTO SAMPLE VALUES(5);
     ELSEIF :SAMPLE_COUNT = 1
     THEN
       INSERT INTO SAMPLE VALUES(6);
     END IF;
 END; 
```

**Trigger with AFTER UPDATE and a WHILE loop**

```
CREATE TABLE TARGET ( A INT);
 CREATE TABLE SAMPLE ( A INT);
 CREATE TRIGGER TEST_TRIGGER_WHILE_UPDATE
 AFTER UPDATE ON TARGET
 BEGIN
     DECLARE found INT := 1;
     DECLARE val INT := 1;
     WHILE :found <> 0 DO
         SELECT count(*) INTO found FROM sample WHERE a = :val;
         IF :found = 0 THEN
             INSERT INTO sample VALUES(:val);
         END IF;
         val := :val + 1;
     END WHILE;
 END;
```

**UPDATE trigger with column list**

```
CREATE TABLE TARGET ( A INT, B INT);
CREATE TABLE SAMPLE ( A INT);
CREATE TRIGGER TEST_TRIGGER_UPDATE_COLUMN_LIST
AFTER UPDATE OF B ON TARGET
BEGIN
    INSERT INTO SAMPLE VALUES(1);
END;
INSERT INTO TARGET VALUES(1, 1);
UPDATE TARGET SET A = 0;
 -- does not fire the trigger
SELECT COUNT(*) FROM SAMPLE;
```

The SELECT statement returns 0.

```
UPDATE TARGET SET B = 0; -- does fire the trigger
SELECT COUNT(*) FROM SAMPLE;
```

The SELECT statement returns 1.

**UPDATE EXCEPT OF trigger with column list**

```
CREATE TABLE TARGET ( A INT, B INT);
CREATE TABLE SAMPLE ( A INT);
CREATE TRIGGER TEST_TRIGGER_UPDATE_EXCEPT_OF_COLUMN_LIST
AFTER UPDATE EXCEPT OF B ON TARGET
BEGIN
    INSERT INTO SAMPLE VALUES(1);
END;
INSERT INTO TARGET VALUES(1, 1);
UPDATE TARGET SET B = 0; -- does not fire the trigger
SELECT COUNT(*) FROM SAMPLE; 
```

The SELECT statement returns 0.

```
UPDATE TARGET SET A = 0; -- does fire the trigger
SELECT COUNT(*) FROM SAMPLE;
```

The SELECT statement returns 1.

```
UPDATE TARGET SET A = 2, B = 2; -- does fire the trigger
SELECT COUNT(*) FROM SAMPLE;
```

The SELECT statement returns 2.

**Trigger with an AFTER INSERT and FOR loop**

```
CREATE TABLE TARGET ( A INT);
 CREATE TABLE control_tab(id INT PRIMARY KEY, name NVARCHAR(30), payment INT);                              
 CREATE TABLE message_box(message NVARCHAR(200), log_time TIMESTAMP);                           

 CREATE TRIGGER TEST_TRIGGER_FOR_INSERT                             
 AFTER INSERT ON TARGET                                             
 BEGIN                                                              
     DECLARE v_id        INT := 0;                                  
     DECLARE v_name      NVARCHAR(20) := '';                         
     DECLARE v_pay       INT := 0;                                  
     DECLARE v_msg       NVARCHAR(200) := '';                        
     DELETE FROM message_box;                                       
     FOR v_id IN 100 .. 103 DO                                  
         SELECT name, payment INTO v_name, v_pay FROM control_tab WHERE id = :v_id;                                      
         v_msg := :v_name || ' has ' || TO_VARCHAR(:v_pay);            
         INSERT INTO message_box VALUES (:v_msg, CURRENT_TIMESTAMP);
     END FOR;                                                       
 END;
```

**Trigger with EXIT HANDLER examples**

```
CREATE TABLE TARGET ( A INT);
 CREATE TABLE MYTAB (I INTEGER PRIMARY KEY);
 
 CREATE TRIGGER MYTRIG_SQLEXCEPTION
 AFTER INSERT ON TARGET 
 BEGIN
     DECLARE EXIT HANDLER FOR SQLEXCEPTION RESIGNAL;
     INSERT INTO MYTAB VALUES (1);
     INSERT INTO MYTAB VALUES (1);  -- expected unique violation error: 301
     -- not reached
 END;
 
 CREATE TRIGGER MYTRIG_SQL_ERROR_CODE 
 AFTER UPDATE ON TARGET 
 BEGIN
     DECLARE EXIT HANDLER FOR SQL_ERROR_CODE 301 RESIGNAL;
     INSERT INTO MYTAB VALUES (1);
     INSERT INTO MYTAB VALUES (1);  -- expected unique violation error: 301
     -- not reached
 END;
 
 CREATE TRIGGER MYTRIG_CONDITION 
 AFTER DELETE ON TARGET 
 BEGIN
     DECLARE MYCOND CONDITION FOR SQL_ERROR_CODE 301;
     DECLARE EXIT HANDLER FOR MYCOND RESIGNAL;
     INSERT INTO MYTAB VALUES (1);
     INSERT INTO MYTAB VALUES (1);  -- expected unique violation error: 301
     -- not reached
 END;
```

**Trigger with SIGNAL/RESIGNAL examples**

```
CREATE TABLE TARGET ( A INT);
 CREATE TABLE MYTAB (I INTEGER PRIMARY KEY);
 CREATE TABLE MYTAB_TRIGGER_ERR (err_code INTEGER, err_msg NVARCHAR(30));

 CREATE TRIGGER MYTRIG_SIGNAL 
 AFTER INSERT ON TARGET 
 BEGIN
     DECLARE MYCOND CONDITION FOR SQL_ERROR_CODE 10001;
     DECLARE EXIT HANDLER FOR MYCOND INSERT INTO MYTAB_TRIGGER_ERR VALUES (::SQL_ERROR_CODE, ::SQL_ERROR_MESSAGE);
     INSERT INTO MYTAB VALUES (1);
     SIGNAL MYCOND SET MESSAGE_TEXT = 'my error message1';  -- signal immediately
     -- not reached
     INSERT INTO MYTAB VALUES (2);
 END;

 INSERT INTO SUBJECT VALUES (1)

 SELECT * FROM MYTAB_TRIGGER_ERR;
 (10001, my error message1)
 
 SELECT * FROM MYTAB;
```

The SELECT statement returns 1.

```
CREATE TRIGGER MYTRIG_RESIGNAL
 AFTER UPDATE ON TARGET 
 BEGIN
     DECLARE MYCOND CONDITION FOR SQL_ERROR_CODE 10002;
     DECLARE EXIT HANDLER FOR MYCOND RESIGNAL;  -- 2. throws error with error code 10002
     INSERT INTO MYTAB VALUES (1);
     SIGNAL MYCOND SET MESSAGE_TEXT = 'my error message2';  -- 1. signal immediately 
     -- not reached
     INSERT INTO MYTAB VALUES (2);
 END;

 UPDATE SUBJECT SET A = 100 WHERE A = 1;
 ERR-10002
 ERR-MSG:user-defined error: "TRIGGER_EXCEPTION"."MYTRIG_RESIGNAL": line 4 col 37 (at pos 210): [10002] (range 3) user-defined error exception: my error message2
```

**Row-wise trigger using transition variable**

```
CREATE TABLE TARGET ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE_OLD ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE_NEW ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE ( A INT, B NVARCHAR(10));
 INSERT INTO TARGET VALUES ( 1, 'oldvalue');
 INSERT INTO TARGET VALUES ( 2, 'oldvalue');
 INSERT INTO TARGET VALUES ( 5, 'oldvalue');

 CREATE TRIGGER TEST_TRIGGER_VAR_UPDATE                   
 AFTER UPDATE ON TARGET                                   
 REFERENCING NEW ROW mynewrow, OLD ROW myoldrow          
 FOR EACH ROW                                             
 BEGIN                                                    
  INSERT INTO SAMPLE_new VALUES(:mynewrow.a, :mynewrow.b); 
  INSERT INTO SAMPLE_old VALUES(:myoldrow.a, :myoldrow.b);
  INSERT INTO SAMPLE VALUES(0, 'trigger');
 END;                                                     

 UPDATE TARGET SET b = 'newvalue' WHERE A < 3;
 SELECT * FROM TARGET;
 1, 'newvalue'
 2, 'newvalue'
 5, 'oldvalue'
 SELECT * FROM SAMPLE_NEW;
 1, 'newvalue'
 2, 'newvalue'
 SELECT * FROM SAMPLE_OLD;
 1, 'oldvalue'
 2, 'oldvalue'
 SELECT * FROM SAMPLE;
 0, 'trigger'
 0, 'trigger'
```

**Statement-wise trigger using transition table**

```
CREATE TABLE TARGET ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE_OLD ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE_NEW ( A INT, B NVARCHAR(10));
 CREATE TABLE SAMPLE ( A INT, B NVARCHAR(10));
 INSERT INTO TARGET VALUES ( 1, 'oldvalue');
 INSERT INTO TARGET VALUES ( 2, 'oldvalue');
 INSERT INTO TARGET VALUES ( 5, 'oldvalue');

 CREATE TRIGGER TEST_TRIGGER_TAB_UPDATE                   
 AFTER UPDATE ON TARGET                                   
 REFERENCING NEW TABLE mynewtab, OLD TABLE myoldtab
 FOR EACH STATEMENT
 BEGIN                                                    
  INSERT INTO SAMPLE_new SELECT * FROM :mynewtab;
  INSERT INTO SAMPLE_old SELECT * FROM :myoldtab; 
  INSERT INTO SAMPLE VALUES(0, 'trigger');
 END;                                                     

 UPDATE TARGET SET b = 'newvalue' WHERE A < 3;
 SELECT * FROM TARGET;
 1, 'newvalue'
 2, 'newvalue'
 5, 'oldvalue'
 SELECT * FROM SAMPLE_NEW;
 1, 'newvalue'
 2, 'newvalue'
 SELECT * FROM SAMPLE_OLD;
 1, 'oldvalue'
 2, 'oldvalue'
 SELECT * FROM SAMPLE;
 0, 'trigger'

CREATE TABLE T1(A INTEGER PRIMARY KEY, B INTEGER);
CREATE COLUMN TABLE T2(A INTEGER PRIMARY KEY, C INTEGER);
CREATE VIEW V1 AS (SELECT T1.A A, B, C, T1.A+10 D FROM T1, T2 WHERE T1.A = T2.A);

CREATE TRIGGER TR1 INSTEAD OF INSERT ON V1 REFERENCING NEW ROW NEW
BEGIN
    INSERT INTO T1 VALUES(:NEW.A, :NEW.B);
    INSERT INTO T2 VALUES(:NEW.A, :NEW.C);
END;

INSERT INTO V1(A,B,C) VALUES(1,2,3);
SELECT FROM T1 ORDER BY A, B;
```

The SELECT statement returns 1, 2.

```
SELECT FROM T2 ORDER BY A, C;
```

The SELECT statement returns 1, 3.

```
SELECT FROM V1 ORDER BY A, B, C, D;
```

The SELECT statement returns 1, 2, 3, 11

```
CREATE TRIGGER TR2 INSTEAD OF UPDATE ON V1 REFERENCING OLD ROW OLD, NEW ROW NEW
BEGIN
    UPDATE T1 SET A=:NEW.A, B=:NEW.B WHERE A=:OLD.A;
    UPDATE T2 SET A=:NEW.A, C=:NEW.C WHERE A=:OLD.A;
END;

UPDATE V1 SET A = 5, B = 6, C = 7 WHERE A = 1;
SELECT FROM T1 ORDER BY A, B;
```

The SELECT statement returns 5, 6.

```
SELECT FROM T2 ORDER BY A, C;
```

The SELECT statement returns 5, 7.

```
SELECT FROM V1 ORDER BY A, B, C, D;
```

The SELECT statement returns 5, 6, 7, 11.

```
CREATE TRIGGER TR3 INSTEAD OF DELETE ON V1 REFERENCING OLD ROW OLD
BEGIN
    DELETE FROM T1 WHERE A = :OLD.A;
    DELETE FROM T2 WHERE A = :OLD.A;
END;

DELETE FROM V1;
SELECT FROM T1 ORDER BY A, B;
SELECT FROM T2 ORDER BY A, C;
SELECT FROM V1 ORDER BY A, B, C, D;
```

**Related Information**  


[TRIGGERS System View](../../020-System-Views-Reference/021-System-Views/triggers-system-view-2101f6d.md "Provides information about triggers that are defined for tables.")

[Table Variable Type Definition](https://help.sap.com/viewer/d1cb63c8dd8e4c35a0f18aef632687f0/2023_2_QRC/en-US/ea5065d06d14426799d879234d8e3e7b.html "") :arrow_upper_right:

[Introduction to SQL](../introduction-to-sql-209f502.md "This chapter describes the SAP HANA database implementation of Structured Query Language (SQL).")

[Data Types](../data-types-20a1569.md "A data type defines the characteristics of a data value. A special value of NULL is included in every data type to indicate the absence of a value.")

[Expressions](../expressions-20a4389.md "An expression is a clause that can be evaluated to return values.")

[CREATE PROCEDURE Statement \(Procedural\)](create-procedure-statement-procedural-20d4674.md "Creates a procedure that uses the specified programming language.")

[Predicates](../predicates-20a2ab2.md "")

[INSERT Statement \(Data Manipulation\)](insert-statement-data-manipulation-20f7f70.md "Adds a record to a table.")

[DELETE Statement \(Data Manipulation\)](delete-statement-data-manipulation-20d6169.md "Deletes records from a table where a specified condition is met.")

[UPDATE Statement \(Data Manipulation\)](update-statement-data-manipulation-20ff268.md "Changes the values of the records of a table.")

[REPLACE Statement \(Data Manipulation\)](replace-statement-data-manipulation-20fc06a.md "Updates rows in a table or inserts new rows. This UPSERT and REPLACE statements are synonymous and have identical syntax and purpose.")

[SELECT Statement \(Data Manipulation\)](select-statement-data-manipulation-20fcf24.md "Queries data from the database.")

