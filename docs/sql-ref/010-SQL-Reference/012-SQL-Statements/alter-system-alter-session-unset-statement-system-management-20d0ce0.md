<!-- loio20d0ce04751910149e6bf5840bb2042a -->

# ALTER SYSTEM ALTER SESSION UNSET Statement \(System Management\)

Unsets session variables for database sessions.



<a name="loio20d0ce04751910149e6bf5840bb2042a__sql_alter_system_alter_session_unset_1sql_alter_system_alter_session_unset_syntax"/>

## Syntax

```
ALTER SYSTEM ALTER SESSION <session_id> UNSET <key>
```



<a name="loio20d0ce04751910149e6bf5840bb2042a__sql_alter_system_reclaim_data_space_1sql_alter_system_alter_session_unset_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<session\_id\>*

</b></dt>
<dd>

Specifies the session ID of the session where the variable should be unset.

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



</dd>
</dl>



<a name="loio20d0ce04751910149e6bf5840bb2042a__sql_alter_system_alter_session_unset_1sql_alter_system_alter_session_unset_description"/>

## Description

For a list of predefined variables, see the M\_SESSION\_CONTEXT system view.

Session variables can be retrieved using the SESSION\_CONTEXT command or from the M\_SESSION\_CONTEXT system view, and unset by using the ALTER SYSTEM ALTER SESSION UNSET statement.



<a name="loio20d0ce04751910149e6bf5840bb2042a__section_qbz_vfr_xrb"/>

## Permissions

To unset session variables, you must have the SESSION ADMIN system privilege.



<a name="loio20d0ce04751910149e6bf5840bb2042a__sql_alter_system_alter_session_unset_1sql_alter_system_alter_session_unset_examples"/>

## Example

Set the session variable MY\_VAR to 'abc' in your database session.

```
SET 'MY_VAR' = 'abc';
```

Execute the following query to get a list of all the session variables of the current session.

```
SELECT * FROM M_SESSION_CONTEXT WHERE CONNECTION_ID = CURRENT_CONNECTION;
```

Remove the session variable from the specified session. In the statement below, replace *<your\_session\_id\>* with the session ID that the previous statement returned.

```
ALTER SYSTEM ALTER SESSION <your_session_id> UNSET 'MY_VAR';
```

You get a list of all the session variables of the current session.

```
SELECT * FROM M_SESSION_CONTEXT WHERE CONNECTION_ID = CURRENT_CONNECTION;
```

From the results of this statement you can see that the MY\_VAR variable has been unset.

