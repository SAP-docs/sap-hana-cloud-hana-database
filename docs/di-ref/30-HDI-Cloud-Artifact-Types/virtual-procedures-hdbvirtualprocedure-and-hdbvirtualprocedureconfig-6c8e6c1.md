<!-- loio6c8e6c1b62d54197bdaa786910295665 -->

# Virtual Procedures \(.hdbvirtualprocedure and .hdbvirtualprocedureconfig\)

Transform a design-time virtual-procedure resource into a virtual-procedure database object.



The Virtual Procedure plug-in transforms a design-time virtual procedure resource \(defined in a `.hdbvirtualprocedure` artifact\) into a virtual-procedure database object. The target database to which the virtual procedure points must be available via a database remote source.

Since, in most cases, the remote source is not known during development but depends on deployment decisions, the complete definition of a virtual procedure is split into two design-time files: a virtual procedure file \(with an optional default configuration\) and an explicit virtual procedure configuration that contains the binding from virtual procedure to remote source. The explicit configuration can be provided at latest at deployment time, overriding the optional default configuration. Iin this way, an administrator can map object references according to the deployment context.



<a name="loio6c8e6c1b62d54197bdaa786910295665__section_r3k_v33_1hb"/>

## Example Artifact Code

The file format required for the `.hdbvirtualprocedure` artifact uses a DDL-style syntax that is equivalent to the corresponding CREATE VIRTUAL PROCEDURE SQL syntax, **without** the leading `CREATE`. The `AT` part of the `VIRTUAL PROCEDURE` definition defines the default configuration for the remote source, as illustrated in the following example:

> ### Code Syntax:  
> `/src/remote_procedure.hdbvirtualprocedure`
> 
> ```sql
> VIRTUAL PROCEDURE "com.sap.hana.example::REMOTE_PROCEDURE"
> ( 
>   IN INT_PARAM_AS_IN INT, 
>   OUT OUT_TABLE TABLE( INT_COLUMN INT, NVARCHAR_COLUMN NVARCHAR(2000))
> ) 
> CONFIGURATION '{}' 
> AT REMOTE_SOURCE 
> ```

> ### Note:  
> The container’s object owner \(<code><i class="varname">&lt;container&gt;</i>#OO</code>\) must have the privilege `CREATE VIRTUAL PROCEDURE ON REMOTE SOURCE` on the remote source.

> ### Code Syntax:  
> `/cfg/remote_procedure.hdbvirtualprocedureconfig`
> 
> ```json
> { 
>   "com.sap.hana.example::REMOTE_PROCEDURE" : { 
>     "target" : { 
>       "remote" : "REMOTE_SYSTEM_A" 
>     } 
>   } 
> } 
> ```



<a name="loio6c8e6c1b62d54197bdaa786910295665__section_pwj_533_1hb"/>

## Plug-in Configuration



### 

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration for the virtual procedure should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```sql
> "hdbvirtualprocedure" : { 
>    "plugin_name" : "com.sap.hana.di.virtualprocedure"
> }, 
> "hdbprojectionviewconfig" : { 
>    "plugin_name" : "com.sap.hana.di.virtualprocedure.config"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

