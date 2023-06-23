<!-- loio28fe43b7c5cc4374b85c67cadc8e9b3f -->

# Virtual Packages \(.hdbvirtualpackage \)

Transform a design-time Hadoop Map Reduce Job or SparkSQL resource into a virtual-package database object.



The Virtual Package plug-in transforms a design-time Hadoop Map Reduce Job or a SparkSQL resource into a virtual-package database object with adapter type “hadoop” or “sparksql” respectively. The Virtual Package plug-in supports the following two formats:

-   Plain Hadoop JAR files

    Plug-in: `hdbvirtualpackagehadoop`

-   Plain SparkSQL files

    Plug-in: `hdbvirtualpackagesparksql`




<a name="loio28fe43b7c5cc4374b85c67cadc8e9b3f__section_hbh_p33_1hb"/>

## Plug-in Configuration

In the configuration file for the SAP HDI container \(`.hdiconfig`\), the plug-in configuration for virtual package resources should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbvirtualpackagehadoop" : {
>    "plugin_name" : "com.sap.hana.di.virtualpackage.hadoop"
> },
> "hdbvirtualpackagesparksql" : { 
>    "plugin_name" : "com.sap.hana.di.virtualpackage.sparksql"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

