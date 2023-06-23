<!-- loio20e74dc875191014b20c81d140d67e42 -->

# SESSION\_CONTEXT Function \(Miscellaneous\)

Returns the value of the specified session variable assigned to the current user.



<a name="loio20e74dc875191014b20c81d140d67e42__sql_function_session_context_1sql_function_session_context_syntax"/>

## Syntax

```
SESSION_CONTEXT(<session_variable>)
```



<a name="loio20e74dc875191014b20c81d140d67e42__sql_function_session_context_1sql_function_session_context_description"/>

## Description

The *<session\_variable\>* can either be predefined or user-defined. Predefined session variables that can be set by the client are APPLICATION, APPLICATIONUSER, and TRACEPROFILE.

Session variables can be defined or modified using a <code>SET [SESSION] <i class="varname">&lt;variable_name&gt;</i> = <i class="varname">&lt;value&gt;</i></code> statement, and unset using an <code>UNSET [SESSION] <i class="varname">&lt;variable_name&gt;</i></code> statement.

SESSION\_CONTEXT returns an NVARCHAR with a maximum length of 512 characters.



<a name="loio20e74dc875191014b20c81d140d67e42__sql_function_session_context_1sql_function_session_context_examples"/>

## Example

The following query returns the value ***HDBStudio***, or a similar value depending on your settings:

```
SELECT SESSION_CONTEXT('APPLICATION') "session context" FROM DUMMY;
```

**Related Information**  


[Session Management Statements](../012-SQL-Statements/session-management-statements-20a27b0.md "The following SQL statements manage database sessions.")

[SESSION\_USER Function \(Miscellaneous\)](session-user-function-miscellaneous-20e76c1.md "Returns the user name of the current session.")

[M\_SESSION\_CONTEXT System View](../../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[SET \[SESSION\] Statement \(Session Management\)](../012-SQL-Statements/set-session-statement-session-management-20fd82b.md "Sets a session variable for the current session.")

[UNSET \[SESSION\] Statement \(Session Management\)](../012-SQL-Statements/unset-session-statement-session-management-20fec78.md "Unsets a session variable for the current session.")

