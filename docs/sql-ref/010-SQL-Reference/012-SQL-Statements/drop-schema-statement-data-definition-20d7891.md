<!-- loio20d7891d751910149164f0d4ca73639d -->

# DROP SCHEMA Statement \(Data Definition\)

Removes a schema.



<a name="loio20d7891d751910149164f0d4ca73639d__sql_drop_schema_1sql_drop_schema_syntax"/>

## Syntax

```
DROP SCHEMA <schema_name> [<drop_option>]
```



<a name="loio20d7891d751910149164f0d4ca73639d__sql_drop_schema_1sql_drop_schema_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<schema\_name\>*

</b></dt>
<dd>

Drops the specified schema.

```
<schema_name> ::= <unicode_name>
```



</dd><dt><b>

*<drop\_option\>*

</b></dt>
<dd>

Specifies the drop option to use.

```
<drop_option> ::= CASCADE | RESTRICT
```

CASCADE drops the schema and all objects contained in the schema, regardless of which user created them. If there are objects in another schema that refer to objects in the schema being dropped, they are dropped if they belong to the user who is dropping the schema, otherwise they are invalidated.

Invalidated objects can be re-validated when an object that has same schema name is created.

RESTRICT drops the schema, but only when there are no objects in it. If RESTRICT is specified while there are still objects in the schema, then an error is returned.

If *<drop\_option\>* is not specified, then RESTRICT is used by default.

Invalidated objects can be re-validated when an object that has same schema name is created.



</dd>
</dl>



<a name="loio20d7891d751910149164f0d4ca73639d__sql_drop_schema_1sql_drop_schema_description"/>

## Description

The DROP SCHEMA statement removes a schema.

Dropping a schema also drops any expression macros defined for the view. The list of all expression macros for a schema can be obtained by querying the VIEW\_EXPRESSION\_MACROS system view.

If you drop a schema, any schema synonym that references it is also dropped.



<a name="loio20d7891d751910149164f0d4ca73639d__sql_drop_schema_1sql_drop_schema_examples"/>

## Example

Create a schema named my\_schema and a table named my\_schema.t.

```
CREATE SCHEMA my_schema;
 CREATE ROW TABLE my_schema.t (a INT);
```

Drop my\_schema with a CASCADE option.

```
DROP SCHEMA my_schema CASCADE;
```

