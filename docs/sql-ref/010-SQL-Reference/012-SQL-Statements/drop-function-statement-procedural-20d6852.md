<!-- loio20d6852375191014a6e2f134db8fc8cb -->

# DROP FUNCTION Statement \(Procedural\)

Deletes a function from the database.



<a name="loio20d6852375191014a6e2f134db8fc8cb__sql_drop_function_1sql_drop_function_syntax"/>

## Syntax

```
DROP FUNCTION <func_name> [<drop_option>]
```



<a name="loio20d6852375191014a6e2f134db8fc8cb__sql_drop_function_1sql_drop_function_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<func\_name\>*

</b></dt>
<dd>

Specifies the name of the function to be dropped, with optional schema name.

```
<func_name> ::= [<schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```



</dd>
</dl>


<dl>
<dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies whether a cascaded drop is performed.

```
<drop_option> ::= CASCADE | RESTRICT
```

When *<drop\_option\>* is not specified, a non-cascaded drop is performed. This only drops the specified function; dependent objects of the function are invalidated but not dropped.

The invalidated objects can be revalidated when an object that has same schema and object name is created.


<dl>
<dt><b>

CASCADE

</b></dt>
<dd>

Drops the function and dependent objects.



</dd><dt><b>

RESTRICT

</b></dt>
<dd>

Drops the function only when dependent objects do not exist. If this drop option is used and a dependent object exists an error is thrown.



</dd>
</dl>



</dd>
</dl>



<a name="loio20d6852375191014a6e2f134db8fc8cb__sql_drop_function_1sql_drop_function_description"/>

## Description

Drops a function created using CREATE FUNCTION from the database catalog.



<a name="loio20d6852375191014a6e2f134db8fc8cb__section_yyl_43h_5rb"/>

## Permissions

You must have the DROP object privilege on the function or the schema in which the function is located.



<a name="loio20d6852375191014a6e2f134db8fc8cb__sql_drop_function_1sql_drop_function_examples"/>

## Examples

Drop a function called my\_func from the database using a non-cascaded drop.

```
DROP FUNCTION my_func;
```

