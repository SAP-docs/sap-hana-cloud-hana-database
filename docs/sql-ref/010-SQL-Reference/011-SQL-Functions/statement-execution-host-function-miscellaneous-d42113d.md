<!-- loiod42113dcde234542919d610a739ffcc1 -->

# STATEMENT\_EXECUTION\_HOST Function \(Miscellaneous\)

Returns the host of the node that executes the statement.



<a name="loiod42113dcde234542919d610a739ffcc1__sql_function_sign_1sql_function_sign_syntax"/>

## Syntax

```
STATEMENT_EXECUTION_HOST()
```



<a name="loiod42113dcde234542919d610a739ffcc1__sql_function_sign_1sql_function_sign_description"/>

## Description

This function is evaluated once per query. The same information appears in the HOST column, as querying the M\_CONNECTIONS system view; however, using this function is faster and less expensive.



<a name="loiod42113dcde234542919d610a739ffcc1__sql_function_sign_1sql_function_sign_examples"/>

## Example

```
SELECT STATEMENT_EXECUTION_HOST() FROM DUMMY;

DO BEGIN
    DECLARE lv_host NVARCHAR(256) = STATEMENT_EXECUTION_HOST();
    DECLARE lv_port INTEGER = STATEMENT_EXECUTION_PORT();
    SELECT * FROM M_CE_CALCSCENARIOS WHERE HOST = :lv_host AND PORT = :lv_port;
END;
```

