<!-- loioa86453dcaffa408e9aaefc0f399a8f48 -->

# HDI Artifact and Build Plug-in Configuration

In SAP HANA Cloud HDI, design-time artifacts are distinguished by means of a unique file suffix that must be mapped to an HDI build plug-in.



Each type of SAP HDI design-time artifacts has a unique file suffix that reflects the content of the file, for example, table, view, procedure, synonym. The file suffix must be mapped to a corresponding build plug-in to enable successful deployment of the design-time artifacts to an HDI container at run time. The following example of an incomplete HDI configuration file \(`.hdiconfig`\) illustrates how the design-time artifact types `.hdbsynonym`, `.hdbview`, `.hdbcalculationview`, and `.hdbprocedure` are mapped to their corresponding HDI build plug-in:

> ### Code Syntax:  
> The HDI Container Configuration File \(`.hdiconfig`\)
> 
> ```json
> {
>   "plugin_version": "4.0.0.0",  // optional, ensures no deployment to on-premise
>   "file_suffixes" : {
>     "hdbsynonym" : { 
>       "plugin_name" : "com.sap.hana.di.synonym"},
>     "hdbview" : { 
>       "plugin_name" : "com.sap.hana.di.view"}, 
>     "hdbcalculationview" : { 
>       "plugin_name" : "com.sap.hana.di.calculationview"},
>     "hdbprocedure" : { 
>       "plugin_name" : "com.sap.hana.di.procedure"},
>     "<file suffix 2>" : {
>       "plugin_name"   : "com.sap.hana.di.<plugin name>",
>       "plugin_version": "4.<plugin_version>"} // optional; overrides global version
>    }
> }
> ```

> ### Restriction:  
> All “hdi\*” file-suffixes \(for example, “`.hdiconfig`” or “`.hdinamespace`”\) are reserved by the SAP HANA Deployment Infrastructure \(HDI\) and cannot be used or \(re\)configured.



<a name="loioa86453dcaffa408e9aaefc0f399a8f48__section_sps_jrv_bpb"/>

## HDI Plug-in Version

For Cloud versions of HANA DI \(HDI\) build plug-ins, the version number is optional. However, as illustrated in the example above, you can use the global `"plugin_version"` number `4.0.0.0`, if you want to ensure that all HDI build plug-ins are only intended for use in the Cloud. Using the format `4.0.0.0` will prevent this version of the build plug-in from being deployed in an on-premise environment. The same rule applies for the specification of a particular plug-in version at the local level, for example, if you want to specify a particular version for an individual HDI build plug-in.

> ### Note:  
> The version number defined at the local level for a specific HDI build plug-in overrides the version defined at the global level for all HDI build plug-ins.



<a name="loioa86453dcaffa408e9aaefc0f399a8f48__section_tps_jrv_bpb"/>

## HDI Plug-in Types

The SAP HANA Cloud, SAP HANA database deployment infrastructure \(HDI\) supports a wide variety of database artifact types, for example, tables, indexes, views, procedures, triggers, and so on. For more information about the syntax required for a particular type of design-time artifact and the configuration of the corresponding build plug-in, see *HDI Artifact Type and Build Plug-ins* in *Related Information* below.

> ### Note:  
> Some of the HDI plug-ins available for database development in SAP HANA on-premise or SAP HANA as a Service \(HaaS\) are not available in SAP HANA Cloud, for example, SAP HANA CDS \(`.hdbcds`\). For more information about which plug-ins are available for use in SAP HANA Cloud, see *Related Information* below.

**Related Information**  


[HDI Artifact Type and Build Plug-ins](hdi-artifact-type-and-build-plug-ins-f8618f7.md "The SAP HANA Cloud, design-time database artifact types, for example, tables and views, are mapped to an SAP HDI build plug-in.")

[SAP HANA Cloud, SAP HANA Database Deployment Infrastructure Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/4077972509f5437c85d6a03e01509417.html "Set up and maintain the deployment infrastructure for the SAP HANA Cloud, SAP HANA database service.") :arrow_upper_right:

[Design-time Content Compatibility \(SAP HANA Cloud Migration Guide\)](https://help.sap.com/viewer/3c53bc7b58934a9795b6dd8c7e28cf05/hanacloud/en-US/9c8656d9c1a34c829fab426cb77b4639.html)

