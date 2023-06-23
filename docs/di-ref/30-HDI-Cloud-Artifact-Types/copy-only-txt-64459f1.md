<!-- loio64459f1b9aa24163bbac5d9229e05aac -->

# Copy Only \(.txt\)

Transform an arbitrary design-time resource into a deployed object.



The copy-only plug-in transforms an arbitrary design-time resource \(defined in a `.txt` artifact\) into a deployed object by copying it from the container’s work file system to the deployed file system.

> ### Restriction:  
> This type of design-time resource does not have a representation inside the run-time container. The resource is only accessible by means of SAP HANA DI APIs.



<a name="loio64459f1b9aa24163bbac5d9229e05aac__section_fkv_cvh_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "txt" : {
>    "plugin_name" : "com.sap.hana.di.copyonly"
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

