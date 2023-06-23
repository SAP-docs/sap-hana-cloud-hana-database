<!-- loio7475cf480ad8498c9991c8a9392d6fc7 -->

# Libraries \(.hdblibrary\)

Transform a design-time library resource into a library database object.



The library plug-in transforms a design-time library resource \(`hdblibrary`\) into a library database object. The file format required for `.hdblibrary` artifacts uses a DDL-style syntax that is equivalent to the corresponding syntax in the SQL command `CREATE LIBRARY`, although without the leading “`CREATE`” command.

> ### Restriction:  
> Supported languages are: L, SQLScript.



<a name="loio7475cf480ad8498c9991c8a9392d6fc7__section_q32_mgh_ycb"/>

## Example Artifact Code

The following code shows a simple example of a library for HDI written in SQLScript:

> ### Code Syntax:  
> `/src/mylibrary.hdblibrary`
> 
> ```sql
> LIBRARY "com.sap.hana.example::MYLIBRARY"
> LANGUAGE SQLSCRIPT
> AS
> BEGIN
>   PUBLIC VARIABLE A CONSTANT INT = 1;
> END
> ```



<a name="loio7475cf480ad8498c9991c8a9392d6fc7__section_elf_zwh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdblibrary" : {
>    "plugin_name" : "com.sap.hana.di.library"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

