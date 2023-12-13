<!-- loioaad1653a9b95422089fec53f48c2899e -->

# Synonyms \(.hdbsynonym and .hdbsynonymconfig\)

Transforms a design-time synonym definition into a database synonym object.



Although it is true that design-time resources must be free of explicit schema references in order to enable deployment into multiple containers, the rules requiring the use only schema-local objects is occasionally too restrictive. For example, often it is necessary to be able to access database objects that are not brought into the system via HANA DI; such objects include database objects from an ERP system or replicated objects. These objects can be easily accessed by defining synonyms.

Since, in most cases, the fully qualified names of the referenced database objects are not known at design time \(because they depend on deployment decisions\), the complete definition of a synonym is split into two design-time files: a declaration \(with an optional default configuration\), and an explicit configuration of the synonym’s target. The explicit configuration can be provided at latest at deployment time, and the explicit configuration overrides the optional default configuration. In this way, an administrator can map object references according to the deployment context.

The complete definition of a synonym is split into the following design-time files:

-   `.hdbsynonym`

    A synonym declaration \(with an optional default configuration\)

-   `.hdbsynonymconfig`

    An explicit \(but optional\) configuration of the synonym’s target; the configuration can also be included in the synonym definition \(`.hdbsynonym`\).


> ### Note:  
> The explicit configuration can be provided at the latest at deployment time and it overrides the optional default configuration. In this way, an administrator can map object references according to the deployment context.

Consider a procedure with the following SQL query in the body:

```sql
SELECT * FROM SYS.DUMMY;
```

Since `SYS.DUMMY` is a non-local schema reference \(the same applies to `PUBLIC.DUMMY`\), the usage is forbidden within the procedure. To perform the `SELECT` on the `SYS.DUMMY` table, the developer must define a synonym, as illustrated in the following examples:



<a name="loioaad1653a9b95422089fec53f48c2899e__section_jld_vd3_1hb"/>

## Example Artifact Code

Synonym definitions and configurations have JSON format, where the synonym definitions use the content of “`target`” object\(s\) in the associated synonym configuration as a default configuration. The following code shows a simple example of a synonym definition for HDI:

> ### Code Syntax:  
> `/src/synonyms.hdbsynonym`
> 
> ```json
> { "com.sap.hana.example::DUMMY" : {
>   } 
> }
> ```

Though the non-local schema references are no longer included, it is still not possible to deploy the procedure since the synonym is not yet bound to any object. To bind the synonym to an object, you must define a synonym configuration, as illustrated in the following example:

> ### Note:  
> The following example is not syntactically correct; it provides **all** options and is intended for illustration purposes only.

> ### Code Syntax:  
> `/src/synonyms.hdbsynonymconfig`
> 
> ```json
> { 
>   "com.sap.hana.example::DUMMY" : { 
>      "target" : { 
>         "database"   : "DATABASE_A", // optional (cross-database access)
>         "schema"     : "SYS",        // optional
>         "object"     : "DUMMY",
>         "revalidate" : true          // optional (Boolean)
>      }
>   },
>   "com.sap.hana.example::synonym2" : { 
>      "target": { 
>         "logical_schema": "<the logical schema>", // not in conjunction with 
>                                                   // "database", "schema", "revalidate"
>         "object" : "<the target object>" 
>      } 
>   },
>   "com.sap.hana.example::synonym3" : { 
>      "target" : { 
>         "remote"   : "<the remote source>", // not in conjunction with "database"
>         "schema"   : "<my Schema>",        
>         "object"   : "<the target object>"
>      }
>   }  
> }
> ```

If the `logical_schema` field of a target description is defined, it is not necessary to provide the fields `database`, `schema`, or `revalidate`. In this case, there is a deployment dependency to a logical schema definition \(described in `.hdblogicalschema` files\). The logical schema definition contains the schema name that is actually used; it must be different from the name of the container schema.

If the target description does not contain the `logical_schema` field and the `schema` field is omitted, too, then the synonym points to a container-local object. In this case, the referenced object is considered as a deployment dependency unless the `revalidate` field is set to <code>“false”</code>. The `revalidate` field is optional and defaults to <code>“true”</code> for this case.

If the `schema` field of a target description is omitted, the synonym points to a container-local object. This means that the referenced object is considered as a deployment dependency unless the `revalidate` field is set to “`false`”. The `revalidate` field is optional and defaults to “true” for this case.

If the `schema` field of a target description is defined, then the referenced target object is treated as a run-time object that is not managed by the SAP HANA Deployment Infrastructure \(HDI\), which also means that it is not considered during dependency management.

> ### Restriction:  
> The `revalidate` field is not allowed if the `schema` field is defined.

If the `database` field of a target description is defined, then the synonym points to an object inside a remote database in a multi-tenant database-container setup.

If the `"remote"` field of a target description is defined, then a `"database"` cannot be specified. Note that the referenced target `"object"` is **not** regarded as an HDI-managed run-time object, is therefore not considered during dependency management.

With these two configuration files, the synonym `com.sap.hana.example::DUMMY` for the table `SYS.DUMMY` is fully defined, and the procedure can be deployed. In this way, you can access non-local schema references and configure the synonyms to match the local deployment database structure without modifying any sources **except** the synonym configurations.

If the synonym points to an object outside of the container, this external object or one of its dependencies might change over time, making it necessary to re-deploy the synonym and the objects in the container that depend on the synonym. Such changes can be detected automatically during a `MAKE` of the container, even when the synonym is not included in the set of files to be deployed, by using the `MAKE` parameter "`validate_external_dependencies`" set to "true", or the optional container configuration parameter "`make.validate_external_dependencies`" set to "true".

> ### Restriction:  
> If the synonym points to an object inside another schema or a different container or to an object inside the same container which is owned by a different user, then the container’s object owner \(<code><i class="varname">&lt;container&gt;</i>#OO</code>\) needs to be granted the required privileges on this target object, for example, `SELECT`, `UPDATE`, and `INSERT`. If views \(that are exposed to other users\) or definer-mode procedures are built on top of synonyms, then the object owner needs privileges `WITH GRANT OPTION`.

The HDI Deployer enables you to set up a template mechanism for HDI configuration files, for example, configuration files for logical schemas, synonyms, or projection views based on services which are bound to an application's database \(`db/`\) module. With this template mechanism, it is possible to configure synonyms, projection views, and similar artifacts. to point to the right database schema without knowing the schema name at development time.

> ### Note:  
> For more information about setting up and using templates for HDI configuration files, see *Related Information* below.



<a name="loioaad1653a9b95422089fec53f48c2899e__section_t1x_td3_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbsynonym" : { 
>    "plugin_name" : "com.sap.hana.di.synonym"
> }, 
> "hdbsynonymconfig" : { 
>    "plugin_name" : "com.sap.hana.di.synonym.config"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Logical Schemas \(.hdblogicalschema and .hdblogicalschemaconfig\)](logical-schemas-hdblogicalschema-and-hdblogicalschemaconfig-fa9cda8.md "Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.")

[Templates for HDI Configuration Files (SAP HANA Cloud Database Developer Guide (SAP Business App Studio))](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2023_4_QRC/en-US/7ef53fb04ecc49a3ae647c21a0736994.html "The HDI Deployer implements a template mechanism for HDI configuration files.") :arrow_upper_right:

