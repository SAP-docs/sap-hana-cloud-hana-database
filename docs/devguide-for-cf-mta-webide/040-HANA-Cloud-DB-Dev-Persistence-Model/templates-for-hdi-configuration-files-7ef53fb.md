<!-- loio7ef53fb04ecc49a3ae647c21a0736994 -->

# Templates for HDI Configuration Files

The HDI Deployer implements a template mechanism for HDI configuration files.

The HDI Deployer enables you to set up a template mechanism for HDI configuration files, for example, configuration files for synonyms or projection views based on services which are bound to the `db/` module application. With this template mechanism, it is possible to configure synonyms, projection views, and similar artifacts. to point to the right database schema without knowing the schema name at development time.

On startup, the HDI Deployer recursively scans the local `cfg/` folder and picks up all files with a `.*config` suffix, for example, all `.hdbsynonymconfig`, `.hdbvirtualtableconfig` files. For all collected files which contain `.configure` markers in their content, the HDI Deployer applies the configuration template mechanism and creates transient configuration files which are then deployed to the HDI container as described in the following examples.

For a synonym configuration file `cfg/LOCAL_TARGET.hdbsynonymconfig`:

> ### Code Syntax:  
> ```json
> {
>  "LOCAL_TARGET" : { 
>    "target" : { 
>       "schema.configure" : "logical-external-service/schema", 
>       "database.configure" : "logical-external-service/database", 
>       "object" : "TARGET" 
>     }
>   }
> }
> ```

The following section:

> ### Code Syntax:  
> ```json
> "schema.configure" : "logical-external-service/schema", 
> "database.configure" : "logical-external-service/database", 
> "object" : "TARGET" 
> ```

is transformed by the template mechanism into:

> ### Code Syntax:  
> ```json
> "schema" : "THE_SCHEMA", 
> "database" : "THE_DATABASE", 
> "object" : "TARGET" 
> ```

where “`THE_SCHEMA`” and “`THE_DATABASE`” are the values for the schema and database fields of the bound service “`logical-external-service`” , which are denoted by the path expressions “`logical-external-service/schema`” and “`logical-external-service/database`”.

If a field in the service is missing, it will not be configured and will be removed instead, for example, “`database`” in the code examples above might be optional. The names of the services are subject to the service replacements mechanism, which can be used to map a real service, for example, “`real-external-service`”, to a logical service name which is used in the configuration files, for example, “`logical-external-service`”. It is not always applicable to use “`schema.configure`”, “`database.configure`”, in the configuration template files. For this reason, the HDI Deployer provides a generic way of copying a set of properties from the bound service, for example, schema, database, remote source, etc. if they are present, although the template file doesn't mention them. For the configuration file `cfg/LOCAL_TARGET.hdbsynonymconfig`, this could looks as follows:

> ### Code Syntax:  
> `cfg/LOCAL_TARGET.hdbsynonymconfig`
> 
> ```json
> { "LOCAL_TARGET" : { "target" : { "*.configure" : "logical-external-service", "object" : "TARGET" } } } 
> ```

When the HDI Deployer encounters a `*.configure` entry, it copies all well-known fields which are present in the bound service into the configuration file. The well-known fields are currently “`remote`”, “`database`”, and “`schema`”.

The HDI Deployer also supports old-style `.hdbsynonymtemplate` template files. If a `.hdbsynonymtemplate` file is found in the `cfg/` or `src/` folder, it is processed as a configuration template file and a transient file with the suffix `.hdbsynonymconfig` is created. A field grantor is replaced with the schema value from the referenced service; in a configuration template file, a <code>“grantor”</code> field is equivalent to a `"schema.configure" : "the-service/schema"` entry.

**Related Information**  


[Configuring the HDI Deployer](configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[Integrate the HDI Deployer into a Mutlitarget Application's Database Module](integrate-the-hdi-deployer-into-a-mutlitarget-application-s-database-modu-0194390.md "Install the HDI Deployer for use by a Multi-Target Application (MTA).")

[Logical Schemas (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_3_QRC/en-US/fa9cda8b540a486dacd12e06f9a60330.html "Transforms a design-time logical-schema definition into run-time database objects that can be used by synonyms and so on.") :arrow_upper_right:

[Projection Views (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_3_QRC/en-US/d8a3392c1287420ca82ac3090cd5049b.html "Transforms a design-time projection-view definition into a database object.") :arrow_upper_right:

[Synonyms (SAP HANA Cloud, HDI Reference)](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2022_3_QRC/en-US/aad1653a9b95422089fec53f48c2899e.html "Transforms a design-time synonym definition into a database synonym object.") :arrow_upper_right:

