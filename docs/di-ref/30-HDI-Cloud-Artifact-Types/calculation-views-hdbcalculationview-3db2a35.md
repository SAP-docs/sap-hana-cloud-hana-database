<!-- loio3db2a35e714e4f6e9711fb62997d0c5c -->

# Calculation Views \(.hdbcalculationview\)

Transform a design-time calculation view description into a set of view database objects.



The Calculation View plug-in transforms a design-time calculation view described in a `.hdbcalculationview` artifact into a set of view database objects. The file format used in the `.hdbcalculationview` artifact is based on XML syntax.



## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plugin configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbcalculationview" : {
>    "plugin_name" : "com.sap.hana.di.calculationview"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

