<!-- loio20d7332f75191014866fc4b83cfba146 -->

# DROP REMOTE SOURCE Statement \(Access Control\)

Removes an existing remote source.



<a name="loio20d7332f75191014866fc4b83cfba146__sql_drop_remote_source_1sql_drop_remote_source_syntax"/>

## Syntax

```
DROP REMOTE SOURCE <remote_source_name> [<drop_option>]
```



<a name="loio20d7332f75191014866fc4b83cfba146__sql_drop_remote_source_1sql_drop_remote_source_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<remote\_source\_name\>*

</b></dt>
<dd>

Specifies the identifier of the remote source.

```
<remote_source_name> ::= <identifier>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

When *<drop\_option\>* is not specified, a RESTRICT drop is performed.

CASCADE drops the remote source and dependent objects.

RESTRICT drops the remote source only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.



</dd>
</dl>



<a name="loio20d7332f75191014866fc4b83cfba146__sql_drop_remote_source_1sql_drop_remote_source_description"/>

## Description

The DROP REMOTE SOURCE statement removes an existing remote source.



<a name="loio20d7332f75191014866fc4b83cfba146__section_opr_ddt_5cb"/>

## Permissions

This statement requires the DROP object privilege on the remote source.



<a name="loio20d7332f75191014866fc4b83cfba146__sql_drop_remote_source_1sql_drop_remote_source_examples"/>

## Example

Create the remote source S and then drop it.

```
CREATE REMOTE SOURCE S ADAPTER ASEODBC 
    CONFIGURATION 'DSN=ProductionASE' 
    WITH CREDENTIAL TYPE 'PASSWORD' USING 'user="aseuser";password="asepassword"';

 DROP REMOTE SOURCE S;
```

