<!-- loio20fd82b675191014b22c8af08d0b319c -->

# SET \[SESSION\] Statement \(Session Management\)

Sets a session variable for the current session.



<a name="loio20fd82b675191014b22c8af08d0b319c__sql_set_session_1sql_set_session_syntax"/>

## Syntax

```
SET [SESSION] <variable_string_literal> = <value_string_literal>
```



<a name="loio20fd82b675191014b22c8af08d0b319c__sql_set_session_1sql_alter_system_alter_session_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<variable\>*

</b></dt>
<dd>

Specifies the variable to set. The maximum length of *<variable\>* is 5000 characters.



</dd><dt><b>

*<value\>*

</b></dt>
<dd>

Specifies the value for the specified variable. The maximum length of *<value\>* is 5000 characters.



</dd>
</dl>



<a name="loio20fd82b675191014b22c8af08d0b319c__sql_set_session_1sql_set_session_description"/>

## Description

The maximum number of session variables is 1024 per session by default \(or as defined by the max\_session\_variables setting in the `indexserver.ini` configuration file.

Session variable settings may be overridden by options specified in a query.

Session variables with the `XS_` prefix are protected and cannot be overwritten with the standard SQL SET command.

Session variables can be retrieved by using the SESSION\_CONTEXT function or by querying the M\_SESSION\_CONTEXT system view.



<a name="loio20fd82b675191014b22c8af08d0b319c__sql_unset_session_1sql_set_session_examples"/>

## Example

Set the session variable MY\_VAR to abc:

```
SET 'MY_VAR' = 'abc';
```

Select the variable MY\_VAR from the current session.

```
SELECT SESSION_CONTEXT('MY_VAR') FROM DUMMY;
```

or

```
SELECT * FROM SYS.M_SESSION_CONTEXT WHERE CONNECTION_ID = CURRENT_CONNECTION;
```

Unset the session variable MY\_VAR.

**Related Information**  


[M\_SESSION\_CONTEXT System View](../../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[UNSET \[SESSION\] Statement \(Session Management\)](unset-session-statement-session-management-20fec78.md "Unsets a session variable for the current session.")

[SESSION\_CONTEXT Function \(Miscellaneous\)](../011-SQL-Functions/session-context-function-miscellaneous-20e74dc.md "Returns the value of the specified session variable assigned to the current user.")

[Session Variables](../session-variables-a16678c.md " 		 		 		 		 		 		 	")

