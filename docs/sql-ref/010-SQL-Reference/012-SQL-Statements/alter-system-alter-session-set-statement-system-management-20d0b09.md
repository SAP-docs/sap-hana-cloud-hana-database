<!-- loio20d0b09375191014b517e1ec387f9c26 -->

# ALTER SYSTEM ALTER SESSION SET Statement \(System Management\)

Sets session variables for database sessions.



<a name="loio20d0b09375191014b517e1ec387f9c26__sql_alter_system_alter_session_1sql_alter_system_alter_session_syntax"/>

## Syntax

```
ALTER SYSTEM ALTER SESSION <session_id> SET <key> = <value>
```



<a name="loio20d0b09375191014b517e1ec387f9c26__sql_set_session_1sql_alter_system_alter_session_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<session\_id\>*

</b></dt>
<dd>

Specifies the session ID of the session where the variable should be set.

```
<session_id> ::= <unsigned_integer>
```



</dd><dt><b>

*<key\>*

</b></dt>
<dd>

Specifies the key of a session variable.

```
<key> ::= <string_literal>
```

The maximum length of key is 32 characters.



</dd><dt><b>

*<value\>*

</b></dt>
<dd>

Specifies the desired value of a session variable.

```
<value> ::= <string_literal>
```

The maximum length of *<value\>* is 512 characters.



</dd>
</dl>



<a name="loio20d0b09375191014b517e1ec387f9c26__sql_alter_system_alter_session_1sql_alter_system_alter_session_description"/>

## Description

For a list of predefined variables, see the M\_SESSION\_CONTEXT system view.

Session variables can be retrieved using the SESSION\_CONTEXT command or from the M\_SESSION\_CONTEXT system view, and unset by using the ALTER SYSTEM ALTER SESSION UNSET statement.



<a name="loio20d0b09375191014b517e1ec387f9c26__section_qbz_vfr_xrb"/>

## Permissions

To set session variables, you must have the SESSION ADMIN system privilege.



<a name="loio20d0b09375191014b517e1ec387f9c26__sql_alter_system_alter_session_1sql_alter_system_alter_session_examples"/>

## Example

For this example, you must run each command in this example in the same SQL editor because you need the same database session to make the example work properly.

Obtain your current session ID.

```
SELECT connection_id FROM m_connections WHERE OWN = 'TRUE';
```

Set the variable MY\_VAR to 'some\_value' in your session. In the command below, replace *<your\_session\_id\>* with the session ID from the previous query.

```
ALTER SYSTEM ALTER SESSION <your_session_id> SET 'MY_VAR'= 'some_value';
```

Check the current value of MY\_VAR in your session.

```
SELECT SESSION_CONTEXT('MY_VAR') FROM dummy;
```

