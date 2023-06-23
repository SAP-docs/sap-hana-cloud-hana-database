<!-- loio93de88bf2c8242179647e40f958c24e5 -->

# Procedures \(.hdbprocedure\)

Transform a design-time procedure resource into a procedure database object.



The procedure plug-in transforms a design-time procedure resource \(described in a `.hdbprocedure` artifact\) into a procedure database object. The file format required for the `hdbprocedure` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE PROCEDURE`, but without the leading “`CREATE`” command. The procedure plug-in supports the following languages for the `hdbprocedure` artifact: SQLScript, L, and R. AFLLang procedures are handled by the “AFLLang Procedure” plug-in.

> ### Note:  
> If the procedure is implemented in R, then the container’s object owner \(<code><i class="varname">&lt;container&gt;</i>#OO</code>\) needs the privilege `CREATE R SCRIPT`.



<a name="loio93de88bf2c8242179647e40f958c24e5__section_fpc_pxh_1hb"/>

## Example Artifact Code

The following code shows a simple example of a procedure definition for HDI:

> ### Code Syntax:  
> `/src/SELECT_CUTOMER.hdbprocedure`
> 
> ```sql
> PROCEDURE "com.sap.hana.example::SELECT_CUSTOMER" (
>    IN ID INTEGER, 
>    OUT NAME NVARCHAR(1024) 
> ) 
> LANGUAGE SQLSCRIPT 
> SQL SECURITY INVOKER 
> AS 
> BEGIN 
>    SELECT NAME INTO NAME FROM "com.sap.hana.example::CUSTOMERS" 
>    WHERE CUSTID = ID; 
> END
> ```



<a name="loio93de88bf2c8242179647e40f958c24e5__section_tkz_nxh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbprocedure" : {
>    "plugin_name" : "com.sap.hana.di.procedure"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

