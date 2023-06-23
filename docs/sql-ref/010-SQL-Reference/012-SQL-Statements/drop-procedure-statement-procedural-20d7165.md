<!-- loio20d7165e75191014a7129ace03afebeb -->

# DROP PROCEDURE Statement \(Procedural\)

Deletes a procedure from the database.



<a name="loio20d7165e75191014a7129ace03afebeb__sql_drop_procedure_1sql_drop_procedure_syntax"/>

## Syntax

```
DROP PROCEDURE <proc_name> [<drop_option>]
```



<a name="loio20d7165e75191014a7129ace03afebeb__sql_drop_procedure_1sql_drop_procedure_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<proc\_name\>*

</b></dt>
<dd>

Specifies the name of the procedure to be dropped, and optionally, a schema name.

```
<proc_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies whether a cascaded drop is performed.

```
<drop_option> ::= CASCADE | RESTRICT
```

When *<drop\_option\>* is not specified, then a non-cascaded drop be performed. Only the specified procedure is dropped; dependent objects of the procedure are invalidated, but they are not dropped.

The invalidated objects can be revalidated when an object that has same schema and object name is created.


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Drops the procedure and dependent objects.



</dd><dt><b>

RESTRICT

</b></dt>
<dd>

Drops the procedure only when dependent objects do not exist. If this drop option is used and a dependent object exists, then an error is thrown.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d7165e75191014a7129ace03afebeb__sql_drop_procedure_1sql_drop_procedure_description"/>

## Description

Drops a procedure created using CREATE PROCEDURE from the database catalog.



<a name="loio20d7165e75191014a7129ace03afebeb__sql_drop_procedure_1sql_drop_procedure_examples"/>

## Examples

Drop a procedure called my\_proc from the database using a non-cascaded drop.

```
DROP PROCEDURE my_proc;
```

