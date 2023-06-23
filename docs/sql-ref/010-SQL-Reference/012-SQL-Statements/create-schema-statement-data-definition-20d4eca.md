<!-- loio20d4ecad7519101497d192700ce5f3df -->

# CREATE SCHEMA Statement \(Data Definition\)

Creates a schema in the current database.



<a name="loio20d4ecad7519101497d192700ce5f3df__sql_create_schema_1sql_create_schema_syntax"/>

## Syntax

```
CREATE SCHEMA <schema_name> [OWNED BY <user_name>]
```



<a name="loio20d4ecad7519101497d192700ce5f3df__sql_create_schema_1sql_create_schema_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<schema\_name\>*

</b></dt>
<dd>

Specifies the schema name.

```
<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<user\_name\>*

</b></dt>
<dd>

Specifies the name of the schema owner. If omitted, the current user is the owner of the schema.

```
<user_name> ::= <unicode_name>
```



</dd>
</dl>



<a name="loio20d4ecad7519101497d192700ce5f3df__sql_create_schema_1sql_create_schema_description"/>

## Description

The CREATE SCHEMA statement creates a schema in the current database.



<a name="loio20d4ecad7519101497d192700ce5f3df__section_opr_ddt_5cb"/>

## Permissions

This statement requires the CREATE SCHEMA privilege.



<a name="loio20d4ecad7519101497d192700ce5f3df__sql_create_schema_1sql_create_schema_examples"/>

## Example

```
CREATE SCHEMA my_schema OWNED BY system;
```

