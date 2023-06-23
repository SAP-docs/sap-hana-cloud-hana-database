<!-- loio20d1524e751910148706e0aab4063a0f -->

# ALTER SYSTEM DISCONNECT SESSION Statement \(System Management\)

Disconnects the specifed connection session from the database.



<a name="loio20d1524e751910148706e0aab4063a0f__sql_alter_system_disconnect_1sql_alter_system_disconnect_syntax"/>

## Syntax

```
ALTER SYSTEM DISCONNECT SESSION <session_id>
```



<a name="loio20d1524e751910148706e0aab4063a0f__sql_alter_system_disconnect_1sql_alter_system_disconnect_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<session\_id\>*

</b></dt>
<dd>

Specifies the external \(client\) session to be disconnected.

```
<session_id> ::= <string_literal> 
```



</dd>
</dl>



<a name="loio20d1524e751910148706e0aab4063a0f__sql_alter_system_disconnect_1sql_alter_system_disconnect_description"/>

## Description

Before disconnecting, any currently running operations associated with the session are terminated.

If *<session\_id\>* is an internal connection, the statement is ignored.



<a name="loio20d1524e751910148706e0aab4063a0f__section_fpp_mnr_xrb"/>

## Permissions

To disconnect sessions, you must have the SESSION ADMIN system privilege.



<a name="loio20d1524e751910148706e0aab4063a0f__sql_alter_system_disconnect_1sql_alter_system_disconnect_examples"/>

## Example

The following query obtains the session IDs of idle sessions.

```
SELECT CONNECTION_ID, IDLE_TIME FROM M_CONNECTIONS
  WHERE CONNECTION_STATUS = 'IDLE' AND CONNECTION_TYPE = 'Remote'
  ORDER BY IDLE_TIME DESC;
```

To disconnect a session, replace *<connection\_id\>* with a connection ID from the query above.

```
ALTER SYSTEM DISCONNECT SESSION '<connection_id>';
```

