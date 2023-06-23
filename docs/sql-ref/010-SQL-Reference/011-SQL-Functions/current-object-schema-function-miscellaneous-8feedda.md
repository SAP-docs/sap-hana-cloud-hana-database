<!-- loio8feedda0f93b4b5aa66af0714d62c83a -->

# CURRENT\_OBJECT\_SCHEMA Function \(Miscellaneous\)

Returns the current schema name when creating a view.



<a name="loio8feedda0f93b4b5aa66af0714d62c83a__sql_function_current_object_schema_1sql_function_current_object_schema_syntax"/>

## Syntax

```
CURRENT_OBJECT_SCHEMA()
```



<a name="loio8feedda0f93b4b5aa66af0714d62c83a__sql_function_current_object_schema_1sql_function_current_object_schema_description"/>

## Description

When creating a view, use the CURRENT\_OBJECT\_SCHEMA function where a schema name is required in the definition of the view, but a hard-coded schema name does not work. Currently, only the WORKDAYS\_BETWEEN and CONVERT\_CURRENCY functions support CURRENT\_OBJECT\_SCHEMA as replacement for an actual schema name.



<a name="loio8feedda0f93b4b5aa66af0714d62c83a__sql_function_current_object_schema_1sql_function_current_object_schema_examples"/>

## Example

The following example replaces CURRENT\_OBJECT\_SCHEMA with the name of the current schema \(in this case, ***SCHEMA1***\):

```
CREATE VIEW SCHEMA1.VIEW1 AS SELECT WORKDAYS_BETWEEN('01', '2014-01-09', '2014-01-10', CURRENT_OBJECT_SCHEMA()) FROM DUMMY;
```

