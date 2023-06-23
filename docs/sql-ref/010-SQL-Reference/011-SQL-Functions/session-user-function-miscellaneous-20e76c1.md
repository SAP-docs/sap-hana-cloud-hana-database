<!-- loio20e76c1a7519101496b1f32f0d1128d9 -->

# SESSION\_USER Function \(Miscellaneous\)

Returns the user name of the current session.



<a name="loio20e76c1a7519101496b1f32f0d1128d9__sql_function_session_user_1sql_function_session_user_syntax"/>

## Syntax

```
SESSION_USER
```



<a name="loio20e76c1a7519101496b1f32f0d1128d9__sql_function_session_user_1sql_function_session_user_description"/>

## Description

SESSION\_USER and CURRENT\_USER are similar functions, but there are differences. SESSION\_USER reflects how the session connected to the server, while CURRENT\_USER may be affected by the SQL SECURITY clause and reflects how permissions are applied.



<a name="loio20e76c1a7519101496b1f32f0d1128d9__sql_function_session_user_1sql_function_session_user_examples"/>

## Example

The following query returns user name of the current session:

```
SELECT SESSION_USER "session user" FROM DUMMY;
```

Consider the following fictitious definer-mode procedure that is declared by USER\_A:

```
CREATE PROCEDURE USER_A.PROC1 LANGUAGE SQLSCRIPT SQL SECURITY DEFINER AS
 BEGIN
     SELECT SESSION_USER "session user" , CURRENT_USER "current user" FROM DUMMY;
 END;
```

The following fictitious query returns ***USER\_B*** when USER\_B executes USER\_A.PROC:

```
CALL USER_A.PROC1;
```

Consider the following fictitious invoker-mode procedure that is declared by USER\_A:

```
CREATE PROCEDURE USER_A.PROC2 LANGUAGE SQLSCRIPT SQL SECURITY INVOKER AS
 BEGIN
     SELECT SESSION_USER "session user" , CURRENT_USER "current user" FROM DUMMY;
 END; 
```

The following fictitious query returns ***USER\_B*** when USER\_B executes USER\_A.PROC:

```
CALL USER_A.PROC2;
```

**Related Information**  


[Session Management Statements](../012-SQL-Statements/session-management-statements-20a27b0.md "The following SQL statements manage database sessions.")

[M\_SESSION\_CONTEXT System View](../../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[SESSION\_CONTEXT Function \(Miscellaneous\)](session-context-function-miscellaneous-20e74dc.md "Returns the value of the specified session variable assigned to the current user.")

[CURRENT\_USER Function \(Miscellaneous\)](current-user-function-miscellaneous-20de8b3.md "Returns the current user name at the current statement context.")

