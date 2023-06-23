<!-- loiod131415cbf7349158d2654e0fcf73487 -->

# Public Synonyms \(.hdbpublicsynonym\)

Create public synonyms that refer to database objects located in the target schema of the current container.



The Public Synonym plug-in can be used to create public synonyms that refer to database objects located in the target schema of the current container. Public synonyms are single database objects; a public synonym with a specific name can only be created from within **one** HDI container.

> ### Note:  
> The Public Synonym plug-in is intended for use in migration scenarios where an existing application uses public synonyms to accesses database objects. As a result, the corresponding plug-in library \(`com.sap.hana.di.publicsynonym`\) is not part of the default libraries for a new HDI container and must be explicitly configured by an administrator, as described in the *Maintaining HDI Containers* section of the *SAP HANA Administration Guide*.



<a name="loiod131415cbf7349158d2654e0fcf73487__section_m1t_xxh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a public-synonym definition for HDI:

> ### Code Syntax:  
> `src/a_synonym.hdbpublicsynonym`
> 
> ```json
> { 
>   "<synonym 1>" : { 
>     "target": { 
>       "object" : "<the target object 1>" 
>     } 
>   }, 
>   "<synonym 2>" : { 
>     "target": { 
>       "object" : "<the target object 2>" 
>     } 
>   }, 
>   <...> 
> }
> ```

Like the normal synonym artifact, the design-time definition file for a public-synonym \(`.hdbpublicsynonym`\) can contain multiple definitions. The elements *<synonym\_1\>*, *<synonym\_2\>*, and so on, define the names of the public synonyms to be created; *<the target object 1\>* and *<the target object 2\>* are the corresponding, referenced container-specific run-time objects.

The following example creates a public synonym named `com.sap.hana.example::A_Public_Synonym` in the schema `PUBLIC` which points to the object `com.sap.hana.example::A_TABLE` in the container’s schema. The name of the public synonym must follow the normal name-space rules.

> ### Sample Code:  
> ```json
> { 
>   "com.sap.hana.example::A_Public_Synonym" : { 
>     "target": { 
>       "object" : "com.sap.hana.example::A_TABLE" 
>     } 
>   } 
> }
> ```

> ### Note:  
> Users who make use of the `_SYS_BIC` synonym must be assigned to a container-specific role that provides privileges to the addressed target object; the role can be assigned to the user with the container’s `GRANT_CONTAINER_SCHEMA_ROLES` application programming interface \(API\).



<a name="loiod131415cbf7349158d2654e0fcf73487__section_xcs_wxh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbpublicsynonym": { 
> 	"plugin_name" : "com.sap.hana.di.publicsynonym"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[Maintaining HDI Containers \(SAP HANA Admin Guide\)](../10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

