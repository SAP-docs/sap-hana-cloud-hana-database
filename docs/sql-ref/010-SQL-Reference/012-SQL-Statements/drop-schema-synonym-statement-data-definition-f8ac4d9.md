<!-- loiof8ac4d9c656049c29d80a9ba3a495001 -->

# DROP SCHEMA SYNONYM Statement \(Data Definition\)

Removes a schema synonym.



## Syntax

```
DROP SCHEMA SYNONYM <synonym_name>
```



<a name="loiof8ac4d9c656049c29d80a9ba3a495001__section_nwc_jjc_4fb"/>

## Syntax Elements


<dl>
<dt><b>

*<synonym\_name\>*

</b></dt>
<dd>

The name of the schema synonym to drop.



</dd>
</dl>



<a name="loiof8ac4d9c656049c29d80a9ba3a495001__section_hm2_ljc_4fb"/>

## Description

Use DROP SCHEMA SYNONYM to remove a schema synonym.



<a name="loiof8ac4d9c656049c29d80a9ba3a495001__section_cnw_mgf_pfb"/>

## Permissions

You must have the CREATE SCHEMA system privilege.

A schema synonym is automatically dropped when the schema to which it refers is dropped.



<a name="loiof8ac4d9c656049c29d80a9ba3a495001__section_rdx_zjc_4fb"/>

## Example

Execute the following statement to create a schema synonym called TEST\_SCHEMA\_SYN that references the schema SYSTEM:

```
CREATE OR REPLACE SCHEMA SYNONYM TEST_SCHEMA_SYN FOR SYSTEM;
```

Execute the next statement to drop that same schema synonym:

```
DROP SCHEMA SYNONYM TEST_SCHEMA_SYN;
```

**Related Information**  


[DROP SCHEMA Statement \(Data Definition\)](drop-schema-statement-data-definition-20d7891.md "Removes a schema.")

[CREATE SCHEMA Statement \(Data Definition\)](create-schema-statement-data-definition-20d4eca.md "Creates a schema in the current database.")

[CREATE SCHEMA SYNONYM Statement \(Data Definition\)](create-schema-synonym-statement-data-definition-1b54e1f.md "Creates a schema synonym.")

[SET SCHEMA Statement \(Session Management\)](set-schema-statement-session-management-20fd550.md "Changes the default schema for the session to the specified schema.")

