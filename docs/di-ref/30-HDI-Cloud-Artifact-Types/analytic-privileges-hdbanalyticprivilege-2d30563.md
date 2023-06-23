<!-- loio2d3056363053436898fcf5a3141b482f -->

# Analytic Privileges \(.hdbanalyticprivilege\)

Transform a design-time XML-based analytic-privileges resource into a analytic-privileges object in the database.



The analytic privileges plug-in transforms a design-time XML-based analytic-privileges resource \(defined in a `.hdbanalyticprivilege` artifact\) into an analytic-privileges object in the database. The file format required for the design-time `.hdbanalyticprivilege` artifact uses the XML syntax. The referenced views must be defined using the `WITH STRUCTURED PRIVILEGE CHECK` clause.



<a name="loio2d3056363053436898fcf5a3141b482f__section_zjp_j5h_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plugin configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "hdbanalyticprivilege" : {
>    "plugin_name" : "com.sap.hana.di.analyticprivilege"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

