<!-- loio08191144d5804c86af9395b110ac37be -->

# Virtual Tables \(.hdbvirtualtable and .hdbvirtualtableconfig\)

Transform a design-time virtual table resource into a virtual table database object.



The virtual-table plug-in transforms a design-time virtual-table resource \(defined in `.hdbvirtualtable` and `.hdbvirtualtableconfig` artifacts\) into a virtual-table database object. The target database to which the virtual table points must be available by means of a database remote source. The file format required for the design-time artifacts uses a DDL-style syntax that is equivalent to the corresponding syntax in the SQL command `CREATE VIRTUAL TABLE`, although without the leading “`CREATE`” command.

In most cases the remote source is not known during development but depends on deployment decisions. Consequently, the complete definition of a virtual table is split into two design-time files: a virtual table file \(with a default configuration\) and an explicit virtual table configuration that contains the binding from virtual table to remote source, target database, target schema, and target object. The explicit configuration can be provided at the latest at deployment time, overriding the optional default configuration. In this way, an administrator can map object references according to the deployment context.

The `AT` part of the `VIRTUAL TABLE` definition defines the default configuration; virtual tables `WITH REMOTE` are not supported.

> ### Note:  
> The container’s object owner \(“*<container\>*\#OO”\) must have the “CREATE VIRTUAL TABLE” privilege on the remote source, for example: “`CREATE VIRTUAL TABLE ON REMOTE SOURCE`”.

If the remote table is changed, this is not normally detected during deployment. To enable the checking and redeployment of changed remote tables, the optional `MAKE` parameter "`validate_external_dependencies`", or the optional container-configuration parameter "`make.validate_external_dependencies`" can be set to "`true`". The check detects changes to the remote table and redeploys the virtual table. The check also detects deleted virtual tables and raises a warning. An explicit redeployment of such a virtual table may need to be performed, if needed.



<a name="loio08191144d5804c86af9395b110ac37be__section_xln_r33_1hb"/>

## Example Artifact Code

The following code shows a simple example of a virtual-table definition for SAP HDI:

> ### Code Syntax:  
> `/src/remote_customers.hdbvirtualtable`
> 
> ```sql
> VIRTUAL TABLE "com.sap.hana.example::REMOTE_CUSTOMERS" 
> AT REMOTE.CUSTOMERS
> ```

The name of the remote source `REMOTE.CUSTOMERS` specified in the virtual-table definition \(`hdbvirtualtable`\) is overwritten by the name of the remote source that is defined with the `remote` property in the corresponding virtual-table configuration file \(`hdbvirtualtableconfig`\), i.e., `REMOTE_SYSTEM_A` in the example illustrated below. For syntax reasons, it is also necessary to provide a remote source with the name of the table object in the definition of the virtual table, even though it will be overwritten. Note that the `database` property in the virtual-table configuration below refers to the name of the remote database \(`DATABASE_B`\).

> ### Code Syntax:  
> `/cfg/remote_customers.hdbvirtualtableconfig`
> 
> ```json
> {
>  "com.sap.hana.example::REMOTE_CUSTOMERS" : {
>     "target" : { 
>        "remote"   : "REMOTE_SYSTEM_A",
>        "database" : "DATABASE_B", 
>        "schema"   : "APPLICATON_C", 
>        "object"   : "CUSTOMERS" 
>     }
>   },
>  "com.sap.hana.example::REMOTE_CUSTOMERS_2" : {
>     "target" : { 
>        "logical_schema" : "<The logical schema>",
>        "object"         : "CUSTOMERS" 
>     }
>   }
> }
> ```

If the `"logical_schema"` field is defined in a target description, it is not possible to use any of the fields `"database"`, `"schema"`, or `"remote"`. Specifying a `"logical_schema"` creates a deployment dependency to a logical schema defined in the `.hdblogicalschema` artifact.

> ### Tip:  
> The logical schema defined in a `.hdblogicalschema` artifact contains the name of the actual target `schema` and the name of the `remote` source. Optionally, a <code>“database”</code> can be specified in a logical schema defined in the `.hdblogicalschema` artifact.



<a name="loio08191144d5804c86af9395b110ac37be__section_fj4_q33_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> 
> "hdbvirtualtable" : {
>    "plugin_name" : "com.sap.hana.di.virtualtable"
> }, 
> "hdbvirtualtableconfig" : { 
>    "plugin_name" : "com.sap.hana.di.virtualtable.config"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Logical Schemas \(.hdblogicalschema and .hdblogicalschemaconfig\)](logical-schemas-hdblogicalschema-and-hdblogicalschemaconfig-fa9cda8.md "Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.")

