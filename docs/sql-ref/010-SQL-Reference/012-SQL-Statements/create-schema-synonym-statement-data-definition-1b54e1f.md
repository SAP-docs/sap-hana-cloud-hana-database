<!-- loio1b54e1f64cfc401bb3adbe7c143bc323 -->

# CREATE SCHEMA SYNONYM Statement \(Data Definition\)

Creates a schema synonym.



## Syntax

```
CREATE [OR REPLACE] SCHEMA SYNONYM <synonym_name> FOR <schema_reference>
```



<a name="loio1b54e1f64cfc401bb3adbe7c143bc323__section_jhm_szg_nfb"/>

## Syntax Elements


<dl>
<dt><b>

*<synonym\_name\>*

</b></dt>
<dd>

The name of the synonym.



</dd><dt><b>

*<schema\_reference\>*

</b></dt>
<dd>

The name of the schema the synonym is for.



</dd>
</dl>



<a name="loio1b54e1f64cfc401bb3adbe7c143bc323__section_efb_hvb_4fb"/>

## Description

The CREATE SCHEMA SYNONYM statement creates a synonym for an existing schema. Use the synonym when executing the SET SCHEMA statement, and, at connection time, the schema is redirected to the schema referenced by the synonym.

A schema synonym can be used in the following object definitions:

-   Projection views
-   SQL views
-   Table functions
-   Synonyms
-   Procedures

Schema synonyms have the following restrictions:

-   Synonyms cannot be used in the name of a new object:

    ```
    CREATE TABLE SCHEMA_SYNONYM.TAB (A INT); -- error
    ```

-   Synonyms cannot be created for the PUBLIC, SYS, or \_SYS\* schemas
-   Synonyms cannot be used for the DEFAULT SCHEMA of procedures
-   Synonyms cannot be used to update the current schema in SET SCHEMA:

    ```
    CREATE SCHEMA SYNONYM SCHEMA_SYNONYM FOR SCHEMA_A;
    SET SCHEMA SCHEMA_SYNONYM; -- current schema becomes SCHEMA_A
    CREATE OR REPLACE SCHEMA SYNONYM SCHEMA_SYNONYM FOR SCHEMA_B; -- current schema will remain SCHEMA_A
    ```

-   Synonyms cannot be used to refer to objects to be imported or exported:

    ```
    EXPORT SCHEMA_SYNONYM."*" AS BINARY INTO '/tmp'; -- error
    IMPORT SCHEMA_SYNONYM."*" AS BINARY FROM '/tmp'; -- error
    IMPORT ALL AS BINARY FROM '/tmp' WITH RENAME SCHEMA 'SOURCE' TO 'SCHEMA_SYNONYM'; -- error
    EXPORT INTO CSV FILE '/tmp/data.csv' FROM SCHEMA_SYNONYM.TBL; -- error
    IMPORT FROM CSV FILE '/tmp/data.csv' INTO SCHEMA_SYNONYM.TBL; -- error
    ```

-   Tables with associations which refer to schema synonyms cannot be imported:

    ```
    IMPORT "SCHEMA"."TABLE_WITH_SCH_SYN_IN_ASSOC_CLAUSE" AS BINARY FROM '/tmp'; -- error
    ```


The synonym name cannot be the same as an existing schema name.



<a name="loio1b54e1f64cfc401bb3adbe7c143bc323__section_blr_zff_pfb"/>

## Permissions

You must have the CREATE SCHEMA system privilege.



<a name="loio1b54e1f64cfc401bb3adbe7c143bc323__section_mdx_bfc_4fb"/>

## Example

Execute the following statement to create a schema synonym called TEST\_SCHEMA\_SYN that references the schema SYSTEM:

```
CREATE SCHEMA SYNONYM TEST_SCHEMA_SYN FOR SYSTEM;
```

Execute the next statement to set the schema to the new schema synonym at connection time:

```
SET SCHEMA TEST_SCHEMA_SYN;
```

Now, when you execute ***SELECT CURRENT\_SCHEMA FROM DUMMY;***, it returns SYSTEM.

Execute the following statement to change the target schema from the schema synonym TEST\_SCHEMA\_SYN to the actual schema SYSTEM:

```
SET SCHEMA SYSTEM;
```

If you execute ***SELECT CURRENT\_SCHEMA FROM DUMMY;*** again, it returns SYSTEM.

Execute the following statements to create a table in the schema MY\_SCHEMA and a view that selects from the table using the synonym SCH\_SYN:

```
CREATE SCHEMA MY_SCHEMA;
CREATE TABLE MY_SCHEMA.TBL (A INT);
CREATE SCHEMA SYNONYM SCH_SYN FOR MY_SCHEMA;
CREATE VIEW MY_SCHEMA.VW AS SELECT * FROM SCH_SYN.TBL;
```

**Related Information**  


[SET SCHEMA Statement \(Session Management\)](set-schema-statement-session-management-20fd550.md "Changes the default schema for the session to the specified schema.")

[DROP SCHEMA Statement \(Data Definition\)](drop-schema-statement-data-definition-20d7891.md "Removes a schema.")

[DROP SCHEMA SYNONYM Statement \(Data Definition\)](drop-schema-synonym-statement-data-definition-f8ac4d9.md "Removes a schema synonym.")

[CREATE SCHEMA Statement \(Data Definition\)](create-schema-statement-data-definition-20d4eca.md "Creates a schema in the current database.")

