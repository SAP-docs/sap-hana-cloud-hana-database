<!-- loio83275bd31c1e4acba9285813e64ee12f -->

# Table Types \(.hdbtabletype\)

Transforms a design-time table type resource into a table type database object.



The table-type plug-in transforms a design-time table-type resource \(defined in a `.hdbtabletype` artifact\) into a table-type database object, for example, for use by signatures of SQL procedures. The file format required for the `.hdbtabletype` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE TYPE AS TABLE`, but without the leading “`CREATE`”.



<a name="loio83275bd31c1e4acba9285813e64ee12f__section_ynx_3f3_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time, **table type** definition for SAP HDI:

> ### Code Syntax:  
> `/src/TT_PUBLISHERS.hdbtabletype`
> 
> ```sql
> TYPE "com.sap.hana.example::TT_PUBLISHERS" AS TABLE (
>    "PUBLISHER" INTEGER, 
>    "NAME" NVARCHAR(50), 
>    "PRICE" DECIMAL, 
>    "COUNT" INTEGER 
> )
> ```



<a name="loio83275bd31c1e4acba9285813e64ee12f__section_cd4_hf3_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbtabletype" : {
>    "plugin_name" : "com.sap.hana.di.tabletype"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

