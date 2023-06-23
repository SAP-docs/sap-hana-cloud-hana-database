<!-- loioa52198083ad642f79851b8f501aad7f5 -->

# RENAME SCHEMA Statement \(Data Definition\)

Rename a schema without creating a new schema.



## Syntax

```
RENAME SCHEMA <source_schema_name> TO <target_schema_name>
```



<a name="loioa52198083ad642f79851b8f501aad7f5__section_ljw_wrq_cgb"/>

## Syntax Elements


<dl>
<dt><b>

*<source\_schema\_name\>*

</b></dt>
<dd>

Specifies the current name of the schema that you want to rename.

```
<source_schema_name>:;= <unicode_name>
```



</dd><dt><b>

*<target\_schema\_name\>*

</b></dt>
<dd>

Specifies the new name of the schema.

```
<target_schema_name>:;= <unicode_name>
```

Attempting to use an existing schema name returns an error.



</dd>
</dl>



<a name="loioa52198083ad642f79851b8f501aad7f5__section_krz_5sq_cgb"/>

## Description

Rename an existing schema. The schema name of all objects in the source schema is also renamed. All privileges granted to schema objects, data contained in those objects, the validity of the objects, and object IDs are unaffected by the rename.

You cannot rename a user's default schema.

> ### Note:  
> If the schema is referenced in an audit policy, a new audit policy must be created and the old one deleted, or the existing audit policy must be updated for the renamed schema. It is recommended not to mix objects from different schemas in the same audit policy.



<a name="loioa52198083ad642f79851b8f501aad7f5__section_pd2_lwt_dgb"/>

## Permissions

You must be the owner of the source schema and you must have the CREATE SCHEMA system privilege.



<a name="loioa52198083ad642f79851b8f501aad7f5__section_idy_jtq_cgb"/>

## Example

Execute the following statements to create two schemas, named schema0 and schema1:

```
CREATE SCHEMA schema0;
CREATE SCHEMA schema1;
```

Create and populate a table in schema1 and create views based on that table:

```
CREATE TABLE schema1.tb1(x, INT);
INSERT INTO schema1.tb1 VALUES (1);
CREATE VIEW schema1.vi1 AS SELECT * FROM schema1.tb1;
CREATE VIEW schema0.vi0 AS SELECT * FROM schema1.vi1;
```

Execute the following statement to rename schema1 to schema2:

```
RENAME SCHEMA schema1 TO schema2;
```

Execute the following SELECT statement:

```
SELECT * FROM schema2.tb1;
```

The statement executes successfully and returns ***1*** as a result, since the table schema1.tb1 has been renamed to schema2.tb1.

Execute the following SELECT statement:

```
SELECT * FROM schema2.vi1;
```

The statement executes successfully and returns ***1*** as a result, since the view schema1.vi1 has been renamed to schema2.vi1.

Execute the following SELECT statement:

```
SELECT * FROM schema0.vi0;
```

The statement returns an error indicating that it is invalid as the view schema0.vi0 relies on the view schema1.vi1, which has been renamed to schema2.vi2.

**Related Information**  


[CREATE SCHEMA Statement \(Data Definition\)](create-schema-statement-data-definition-20d4eca.md "Creates a schema in the current database.")

[DROP SCHEMA Statement \(Data Definition\)](drop-schema-statement-data-definition-20d7891.md "Removes a schema.")

[SET SCHEMA Statement \(Session Management\)](set-schema-statement-session-management-20fd550.md "Changes the default schema for the session to the specified schema.")

[CREATE AUDIT POLICY Statement \(Access Control\)](create-audit-policy-statement-access-control-20d3d56.md "Creates an audit policy.")

[ALTER AUDIT POLICY Statement \(Access Control\)](alter-audit-policy-statement-access-control-20cfb7b.md "Enables or disables an audit policy, changes audit trail target types for an audit policy, and configures the retention period of the policy.")

