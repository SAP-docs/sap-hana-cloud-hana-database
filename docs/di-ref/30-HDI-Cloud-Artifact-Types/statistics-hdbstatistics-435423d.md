<!-- loio435423d28f2d40f5979ec17b6141d3f1 -->

# Statistics \(.hdbstatistics\)

Transforms a design-time statistics resource into a statistics object on a database table.



The statistics plug-in transforms a design-time statistics resource \(defined in a `.hdbstatistics` artifact\) into a statistics object on a database table. The file format required for the `hdbstatistics` artifact uses a DDL-style syntax that is equivalent to the syntax of the corresponding SQL command `CREATE STATISTICS`, but without the leading “`CREATE`”.

> ### Restriction:  
> The statistics plug-in only supports named statistics.



<a name="loio435423d28f2d40f5979ec17b6141d3f1__section_sqd_413_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time definition of a statistics file for HDI:

> ### Code Syntax:  
> `/src/CUSTOMER_NAME_STATISTICS.hdbstatistics`
> 
> ```sql
> STATISTICS "com.sap.hana.example::CUSTOMER_NAME_STATISTICS" 
> ON "com.sap.hana.example::CUSTOMERS" (NAME)
> ```



<a name="loio435423d28f2d40f5979ec17b6141d3f1__section_ov5_m13_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbstatistics" : {
>    "plugin_name" : "com.sap.hana.di.statistics" 
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

