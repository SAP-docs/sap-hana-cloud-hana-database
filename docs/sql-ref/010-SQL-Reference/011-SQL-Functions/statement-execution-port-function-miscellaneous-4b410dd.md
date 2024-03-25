<!-- loio4b410ddd8e8041eb89772717d20a29e0 -->

# STATEMENT\_EXECUTION\_PORT Function \(Miscellaneous\)

Returns the port of the node that executes the statement.



<a name="loio4b410ddd8e8041eb89772717d20a29e0__sql_function_sign_1sql_function_sign_syntax"/>

## Syntax

```
STATEMENT_EXECUTION_PORT()
```



<a name="loio4b410ddd8e8041eb89772717d20a29e0__sql_function_sign_1sql_function_sign_description"/>

## Description

This function is evaluated once per query. The same information appears in the HOST column, as querying the M\_CONNECTIONS system view; however, using this function is faster and less expensive.



<a name="loio4b410ddd8e8041eb89772717d20a29e0__sql_function_sign_1sql_function_sign_examples"/>

## Example

```
SELECT STATEMENT_EXECUTION_HOST() FROM DUMMY;

DO BEGIN
    DECLARE lv_host NVARCHAR(256) = STATEMENT_EXECUTION_HOST();
    DECLARE lv_port INTEGER = STATEMENT_EXECUTION_PORT();
    SELECT * FROM M_CE_CALCSCENARIOS WHERE HOST = :lv_host AND PORT = :lv_port;
END;
```

