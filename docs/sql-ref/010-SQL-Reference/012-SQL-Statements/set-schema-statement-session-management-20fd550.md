<!-- loio20fd550375191014b886a338afb4cd5f -->

# SET SCHEMA Statement \(Session Management\)

Changes the default schema for the session to the specified schema.



<a name="loio20fd550375191014b886a338afb4cd5f__sql_set_schema_1sql_set_schema_syntax"/>

## Syntax

```
SET SCHEMA <schema_name>
```



<a name="loio20fd550375191014b886a338afb4cd5f__sql_set_schema_1sql_set_schema_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<schema\_name\>*

</b></dt>
<dd>

Specifies the name of the schema that the session should change to.

```
<schema_name> ::= <unicode_name>
```

If *<schema\_name\>* is the name of a schema synonym, then the current schema is set to the schema that is referenced by the schema synonym.



</dd>
</dl>



<a name="loio20fd550375191014b886a338afb4cd5f__sql_set_schema_1sql_set_schema_description"/>

## Description

The user's schema is used as the default schema when executing a SQL statement that references database objects without specifying a schema name.



<a name="loio20fd550375191014b886a338afb4cd5f__sql_set_schema_1sql_set_schema_example"/>

## Example

The following example creates a new schema called MY\_SCHEMA, and then sets the default schema to it.

```
CREATE SCHEMA MY_SCHEMA;
SET SCHEMA MY_SCHEMA;
```

Now, if a table is created \(for example, MY\_TABLE\) and no schema is specified, it is automatically created in the MY\_SCHEMA schema. Likewise, a query such as `SELECT * FROM MY_TABLE;` would be equivalent to `SELECT * FROM MY_SCHEMA.MY_TABLE`.

