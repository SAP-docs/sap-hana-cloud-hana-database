<!-- loiod8a3392c1287420ca82ac3090cd5049b -->

# Projection Views \(.hdbprojectionview and .hdbprojectionviewconfig\)

Transforms a design-time projection-view definition into a database object.



The Projection View plug-in transforms a design-time projection view resource \(described in a `.hdbprojectionview` artifact\) into a projection view database object. A projection-view configuration resource is required that contains the binding from the projection view to the target database, target schema, and target object; the configuration file is similar in format to the one that can be used for the configuration of a database synonym or a logical-schema target.

The complete definition of a projection view is split into the following design-time files:

-   `hdbprojectionview`

    A projection view declaration \(with an optional default configuration\)

-   `hdbprojectionviewconfig`

    An explicit configuration of the projection view's target. A projection view configuration file can contain multiple configurations.


> ### Note:  
> The explicit configuration can be provided at the latest at deployment time and it overrides the optional default configuration. This way, an administrator can map object references according to the deployment context



<a name="loiod8a3392c1287420ca82ac3090cd5049b__section_i4x_txh_1hb"/>

## Example Artifact Code

The format of the projection view file uses a DDL-style syntax which is equivalent to the syntax of the corresponding SQL command `CREATE PROJECTION VIEW`, without the leading “`CREATE`” command. The `FROM` clause of the `PROJECTION VIEW` definition defines the default configuration. For more information about the syntax used in an SQL projection view, see *Related Information* below.

The following code shows a simple example of a projection-view definition for HDI:

> ### Code Syntax:  
> `/src/customers.hdbprojectionview`
> 
> ```sql
> PROJECTION VIEW "com.sap.hana.example::CUSTOMERS_VIEW" 
> AS 
> SELECT ID, NAME FROM "<database>"."<schema>"."<object>"
> ```

To deploy the projection view, you must bind the projection view to an object. To bind the projection view to an object, you must define a projection-view **configuration**, as illustrated in the following example:

> ### Code Syntax:  
> `/src/customers.hdbprojectionviewconfig`
> 
> ```json
> { 
>   "com.sap.hana.example::CUSTOMERS_VIEW" : { 
>     "target" : { 
>       "database" : "DATABASE_A",  
>       "schema"   : "APPLICATON_B", // optional 
>       "object"   : "CUSTOMERS" 
>     } 
>   } 
> }
> ```

> ### Note:  
> A projection view configuration file can contain multiple configurations.

> ### Code Syntax:  
> `/src/alternate.hdbprojectionviewconfig`
> 
> ```json
> { 
>   "com.sap.hana.example::CUSTOMERS_VIEW" : { 
>     "target" : { 
>       "logical_schema" : "ANOTHER_APPLICATON", // not in conjunction with 
>                                                // database or schema
>       "object"   : "CUSTOMERS" 
>     } 
>   } 
> }
> ```

If the `"logical_schema"` field of a target description is defined, it is not possible to define either the `"database"` or the `"schema"` field. The `"logical_schema"` specifies a deployment dependency to a logical schema definition \(described in the `.hdblogicalschema` artifact\). The logical schema definition contains the schema name that is actually used, which must be different from the name of the container schema.

> ### Note:  
> It is also possible to include an \(optional\) `"database"` name. However, a `remote` source name is not allowed.

If the target description does not contain the `logical_schema` field and the `schema` field is omitted, too, then the projection view points to a container-local object. In this case, the referenced object is considered as a deployment dependency unless the `revalidate` field is set to <code>“false”</code>. The `revalidate` field is optional and defaults to <code>“true”</code> for this case.

If no explicit schema is defined for a target description, the projection view points to a container-local object. In this case, the referenced object is considered as a deployment dependency. If the projection view points to an object inside another schema, to a different container, or to an object inside the same container, which is owned by a different user, then the container’s object owner \(“<code><i class="varname">&lt;containerName&gt;</i>#OO</code>””\) must have the required privileges \(for example, `WITH GRANT OPTION`\) on the specified target object, for example, `SELECT`, `UPDATE`, `INSERT`.

If the projection view points to an object outside of the container, this external object or one of its dependencies might change over time, making it necessary to re-deploy the projection view and the objects in the container that depend on the projection view. Such changes can be detected automatically during a `MAKE` of the container, even when the projection view is not included in the set of files to be deployed, by using the `MAKE` parameter "`validate_external_dependencies`" set to "true", or the optional container configuration parameter "`make.validate_external_dependencies`" set to "true".

The HDI Deployer enables you to set up a template mechanism for HDI configuration files, for example, configuration files for logical schemas, synonyms, or projection views based on services which are bound to an application's database \(`db/`\) module. With this template mechanism, it is possible to configure synonyms, projection views, and similar artifacts. to point to the right database schema without knowing the schema name at development time.

> ### Note:  
> For more information about setting up and using templates for HDI configuration files, see *Related Information* below.



<a name="loiod8a3392c1287420ca82ac3090cd5049b__section_zpx_sxh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbprojectionview" : { 
>    "plugin_name" : "com.sap.hana.di.projectionview"
> }, 
> "hdbprojectionviewconfig" : { 
>    "plugin_name" : "com.sap.hana.di.projectionview.config"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Logical Schemas \(.hdblogicalschema and .hdblogicalschemaconfig\)](logical-schemas-hdblogicalschema-and-hdblogicalschemaconfig-fa9cda8.md "Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.")

[Templates for HDI Configuration Files (SAP HANA Cloud Database Developer Guide (SAP Business App Studio))](https://help.sap.com/viewer/c2b99f19e9264c4d9ae9221b22f6f589/2023_2_QRC/en-US/7ef53fb04ecc49a3ae647c21a0736994.html "The HDI Deployer implements a template mechanism for HDI configuration files.") :arrow_upper_right:

[CREATE PROJECTION VIEW Statement \(SAP HANA Cloud SQL Reference Guide\)](https://help.sap.com/viewer/c1d3f60099654ecfb3fe36ac93c121bb/cloud/en-US/e35411b417a94f199679b9f9f45c2306.html)

