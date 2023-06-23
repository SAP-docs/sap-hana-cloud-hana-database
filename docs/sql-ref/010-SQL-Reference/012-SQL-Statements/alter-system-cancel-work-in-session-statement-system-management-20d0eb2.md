<!-- loio20d0eb287519101498c4ecb8114cab17 -->

# ALTER SYSTEM CANCEL \[WORK IN\] SESSION Statement \(System Management\)

Cancels the currently executing statement of a session.



<a name="loio20d0eb287519101498c4ecb8114cab17__sql_alter_system_cancel_work_1sql_alter_system_cancel_work_syntax"/>

## Syntax

```
ALTER SYSTEM CANCEL [WORK IN] SESSION <connection_id>
```



<a name="loio20d0eb287519101498c4ecb8114cab17__sql_alter_system_cancel_work_1sql_alter_system_cancel_work_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<connection\_id\>*

</b></dt>
<dd>

Specifies the connection ID of the session.

```
<connection_id> ::= <string_literal>
```



</dd>
</dl>



<a name="loio20d0eb287519101498c4ecb8114cab17__sql_alter_system_cancel_work_1sql_alter_system_cancel_work_description"/>

## Description

The transaction of the canceled session is rolled back. The statement that was executing returns error code 139 \(current operation canceled by request and transaction rolled back\).



<a name="loio20d0eb287519101498c4ecb8114cab17__sql_alter_system_cancel_work_1sql_alter_system_cancel_work_examples"/>

## Example

The following query returns the current database connection IDs and the statements that the sessions are executing.

```
 SELECT C.CONNECTION_ID, PS.STATEMENT_STRING
   FROM M_CONNECTIONS C JOIN M_PREPARED_STATEMENTS PS
        ON C.CONNECTION_ID = PS.CONNECTION_ID AND C.CURRENT_STATEMENT_ID = PS.STATEMENT_ID
  WHERE C.CONNECTION_STATUS = 'RUNNING'
    AND C.CONNECTION_TYPE = 'Remote';
```

Using the connection ID information that you obtained using the query above, you can now cancel a running query. In the statement below, replace *<connection\_id\>* with a connection ID from the query above.

```
ALTER SYSTEM CANCEL SESSION '<connection_id>';
```

