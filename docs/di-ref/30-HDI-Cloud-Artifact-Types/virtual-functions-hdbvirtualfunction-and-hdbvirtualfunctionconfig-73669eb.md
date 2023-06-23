<!-- loio73669ebdcef44bd9ab0eb57de6a8cf2a -->

# Virtual Functions \(.hdbvirtualfunction and .hdbvirtualfunctionconfig\)

Transform a design-time virtual function resource into a virtual function database object.



The virtual-function plug-in transforms a design-time virtual function resource \(defined in `hdbvirtualfunction` and `hdbvirtualfunctionconfig`artifacts\) into a virtual-function database object. The target database to which the virtual function points must be available by means of a database remote source.

The file format required for the design-time artifacts uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE VIRTUAL FUNCTION`, without the leading “`CREATE`”. The `AT` part of the `VIRTUAL FUNCTION` definition defines the default configuration for the remote source. The container’s object owner \(<code><i class="varname">&lt;container&gt;</i>#OO</code>\) must have the privilege `CREATE VIRTUAL FUNCTION ON REMOTE SOURCE` on the remote source.

Since, in most cases, the remote source is not known during development but depends on deployment decisions, the complete definition of a virtual function is split into two design-time files: a virtual function file \(with a default configuration\) and an explicit virtual function configuration that contains the binding from virtual function to remote source. The explicit configuration can be provided, at the latest, at deployment time, overriding the optional default configuration. Ini this way, an administrator can map object references according to the deployment context.



<a name="loio73669ebdcef44bd9ab0eb57de6a8cf2a__section_oqy_x33_1hb"/>

## Example Artifact Code

The following code shows a simple example of a virtual function definition for SAP HDI:

> ### Code Syntax:  
> `/src/remote_function.hdbvirtualfunction`
> 
> ```sql
> VIRTUAL FUNCTION "com.sap.hana.example::REMOTE_FUNCTION"()
> RETURNS TABLE ( WORD NVARCHAR(60), COUNT INTEGER) 
> PACKAGE "com.sap.hana.example::WORD_COUNT" 
> CONFIGURATION '{}' 
> AT REMOTE_SOURCE
> ```

> ### Code Syntax:  
> `/src/remote_function.hdbvirtualfunctionconfig`
> 
> ```json
> { 
>   "com.sap.hana.example::REMOTE_FUNCTION" : { 
>      "target" : { 
>         "remote" : "REMOTE_SYSTEM_A" 
>      } 
>   } 
> }
> ```



<a name="loio73669ebdcef44bd9ab0eb57de6a8cf2a__section_wh1_x33_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbvirtualfunction" : {
>    "plugin_name" : "com.sap.hana.di.virtualfunction"
> }
> "hdbvirtualfunctionconfig" : {
>    "plugin_name" : "com.sap.hana.di.virtualfunction.config"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

