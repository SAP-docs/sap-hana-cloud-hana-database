<!-- loio20fec78075191014a376da819b302f43 -->

# UNSET \[SESSION\] Statement \(Session Management\)

Unsets a session variable for the current session.



<a name="loio20fec78075191014a376da819b302f43__sql_unset_session_1sql_unset_session_syntax"/>

## Syntax

```
UNSET [SESSION] <key>
```



<a name="loio20fec78075191014a376da819b302f43__sql_unset_session_1sql_unset_session_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<key\>*

</b></dt>
<dd>

Specifies the session variable to unset.

```
<key> ::= <string_literal>
```



</dd>
</dl>



<a name="loio20fec78075191014a376da819b302f43__sql_unset_session_1sql_unset_session_description"/>

## Description

The list of session variables in use for the current session can be found by querying the M\_SESSION\_CONTEXT system view.



<a name="loio20fec78075191014a376da819b302f43__sql_unset_session_1sql_set_session_examples"/>

## Example

Set the session variable MY\_VAR to abc.

```
SET 'MY_VAR' = 'abc';
```

Select the variable MY\_VAR from the current session.

```
SELECT SESSION_CONTEXT('MY_VAR') FROM DUMMY;
```

Unset the session variable MY\_VAR.

```
UNSET 'MY_VAR';
```

**Related Information**  


[SET \[SESSION\] Statement \(Session Management\)](set-session-statement-session-management-20fd82b.md "Sets a session variable for the current session.")

[M\_SESSION\_CONTEXT System View](../../020-System-Views-Reference/022-Monitoring-Views/m-session-context-system-view-20c50b7.md "Displays the session variables set for each connection.")

[Session Variables](../session-variables-a16678c.md " 		 		 		 		 		 		 	")

