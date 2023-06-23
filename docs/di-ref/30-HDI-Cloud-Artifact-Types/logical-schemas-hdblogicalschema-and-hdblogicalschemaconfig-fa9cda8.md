<!-- loiofa9cda8b540a486dacd12e06f9a60330 -->

# Logical Schemas \(.hdblogicalschema and .hdblogicalschemaconfig\)

Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.



An `.hdblogicalschema` artifact defines a logical schema name and a mapping to the real schema name and database. The logical schema can then be used by other objects, for example, synonyms.

> ### Note:  
> The target schema etc. specified in the `.hdblogicalschema` definition must already exist.

Synonym and projection-view configurations \(as described in the corresponding sections for `.hdbsynonymconfig` and `.hdbprojectionviewconfig` artifacts\) provide two ways of defining the schema containing the accessed database object. Either the schema is specified explicitly in the <code>“schema”</code> field of the configuration or the configuration contains a <code>“logical_schema”</code> field. Specifying a <code>“logical_schema”</code> creates a deployment dependency to a logical schema definition that is deployed separately.

Since, in most cases, the fully qualified names of any referenced database objects are not known at design time \(because they depend on deployment decisions\), the complete definition of a logical schema is split into two design-time files: a declaration \(with an optional default configuration\), and an explicit configuration of the logical schema’s target. The explicit configuration can be provided \(at the latest\) at deployment time, and the explicit configuration overrides the optional default configuration. In this way, an administrator can map object references according to the deployment context.

The complete definition of a logical schema is split into the following design-time files:

-   `.hdblogicalschema`

    The declaration of a logical schema \(with an optional default configuration\)

-   `.hdblogicalschemaconfig`

    An explicit \(but optional\) configuration of the logical schema's target; the configuration can also be included in the logical schema's definition \(`.hdblogicalschema`\).


> ### Note:  
> The explicit configuration can be provided at the latest at deployment time, and it overrides the optional default configuration. In this way, an administrator can map object references according to the deployment context.



<a name="loiofa9cda8b540a486dacd12e06f9a60330__section_ckz_fxh_1hb"/>

## Example Artifact Code

Logical schema definitions have the following JSON format.

> ### Code Syntax:  
> Combined Logical Schema Definition and Configuration \(`logicalschemas.hdblogicalschema`\)
> 
> ```json
> {
>  "<logicalschema1>" : {
>    "target": {
>      "remote"   : "<remote source name>", 
>      "database" : "<database name>", 
>      "schema"   : "<target schema>"   
>    } 
>  }
> }
> ```

The <code>“schema”</code> property of a target description is mandatory; it cannot be empty, and the declared value must be different from the container schema. In addition, if you also use the properties `"remote"` or `"database"`, bear in mind that they might be not applicable for every plug-in artifact. For example, the Projection View plug-in \(`.hdbprojectionview`\) does not support the `"remote"` property; the Synonym plug-in, however, accepts either the `"remote"` or `"database"` property, but not both properties at the same time. For this reason, it is recommended to specify different logical schema definitions for use with different plug-ins.

Alternatively, you can split the logical-schema definition and the corresponding configuration into two separate files, as follows:

> ### Code Syntax:  
> Logical Schema Definition \(`logicalschemas.hdblogicalschema`\)
> 
> ```json
> {
>  "com.sap.hana.example::<logicalschema1>" : {
>   },
>  "com.sap.hana.example::<logicalschema2>" : {
>   }
> }
> ```

> ### Note:  
> A logical-schema configuration file can contain multiple definitions. The following example is not complete and intended for illustration purposes only.

> ### Code Syntax:  
> Logical-Schema Configuration File \(`logicalschemas.hdblogicalschemaconfig`\)
> 
> ```json
> {
>  "com.sap.hana.example::<logicalschema1>" : {
>    "target": { 
>      "schema" : "<target schema>"   
>    } 
>  }, 
>  "com.sap.hana.example::<logicalschema2>" : { 
>    "target": { 
>      "remote"   : "<remote source name>", 
>      "database" : "<database name>",
>      "schema"   : "<target schema>"
>     }
>  }, 
>  <...> 
> } 
> ```

The HDI Deployer enables you to set up a template mechanism for HDI configuration files, for example, configuration files for logical schemas, synonyms, or projection views based on services which are bound to an application's database \(`db/`\) module. With this template mechanism, it is possible to configure synonyms, projection views, and similar artifacts. to point to the right database schema without knowing the schema name at development time.

> ### Note:  
> For more information about setting up and using templates for HDI configuration files, see *Related Information* below.



<a name="loiofa9cda8b540a486dacd12e06f9a60330__section_ssr_cxh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdblogicalschema" : { 
>    "plugin_name" : "com.sap.hana.di.logicalschema
> }, 
> "hdblogicalschemaconfig" : { 
>    "plugin_name" : "com.sap.hana.di.logicalschema.config" 
> }
> ```

**Related Information**  


[Projection Views \(.hdbprojectionview and .hdbprojectionviewconfig\)](projection-views-hdbprojectionview-and-hdbprojectionviewconfig-d8a3392.md "Transforms a design-time projection-view definition into a database object.")

[Synonyms \(.hdbsynonym and .hdbsynonymconfig\)](synonyms-hdbsynonym-and-hdbsynonymconfig-aad1653.md "Transforms a design-time synonym definition into a database synonym object.")

[Virtual Tables \(.hdbvirtualtable and .hdbvirtualtableconfig\)](virtual-tables-hdbvirtualtable-and-hdbvirtualtableconfig-0819114.md "Transform a design-time virtual table resource into a virtual table database object.")

[Templates for HDI Configuration Files (SAP HANA Cloud Database Developer Guide (SAP Business App Studio))](https://help.sap.com/viewer/c2b99f19e9264c4d9ae9221b22f6f589/2023_2_QRC/en-US/7ef53fb04ecc49a3ae647c21a0736994.html "The HDI Deployer implements a template mechanism for HDI configuration files.") :arrow_upper_right:

