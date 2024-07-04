<!-- loio64004007ba094687bfc1a03453efb804 -->

# The SAP HDI Container Configuration File

Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure \(HDI\).

In SAP HDI, a design-time container defines an isolated environment for design-time files. To create run-time objects from the corresponding design-time files \(for example, a catalog object from a source definition of a stored procedure\), HDI uses so-called Build Plug-ins. It is not possible to create a catalog object from a design-time resource without having a plug-in which can read and transform this source definition. For this reason, each design-time resource type must be mapped to a build plug-in for each container that is created. This mapping is configured in an HDI container-configuration file: a file with no name but the mandatory file suffix `.hdiconfig`.

> ### Note:  
> The `.hdiconfig` file must be located in the root folder of the database module. However, you can include additional `.hdiconfig` files further down the source-file hierarchy, for example, if you want to change \(expand/restrict\) the definitions at a certain point in the hierarchy.

By default, a file suffix \(for example, `.hdbprocedure`\) is not bound to a specific version of a known build plug-in. Instead, the binding is established by the contents of the `.hdiconfig` file, which must be deployed into the container along with the artifacts it describes. An `.hdiconfig` file is a JSON file with the following structure:

> ### Sample Code:  
> ```json
> {
> "plugin_version": "4.0.0.0",
> "file_suffixes" : {
>    "hdbsynonym" : { 
>       "plugin_name" : "com.sap.hana.di.synonym"},
>    "hdbview" : { 
>       "plugin_name" : "com.sap.hana.di.view"}, 
>    "hdbcalculationview" : { 
>       "plugin_name" : "com.sap.hana.di.calculationview"},
>    "hdbprocedure" : { 
>       "plugin_name" : "com.sap.hana.di.procedure"},
>    "<hdb_file_suffix_#>" : {
>       "plugin_name" : "<plugin_NAME>" }
>     }
> }
> ```

It is also possible to define the plug-in version for individual artifact plug-ins, as illustrated in the following example:

> ### Sample Code:  
> ```json
> {
> "file_suffixes" : {
>    "hdbsynonym" : { 
>       "plugin_name"   : "com.sap.hana.di.synonym", 
>       "plugin_version": "4.0.0.0"},
>    "hdbview" : { 
>       "plugin_name"   : "com.sap.hana.di.view", 
>       "plugin_version": "4.0.0.0" }, 
>    "hdbcalculationview" : { 
>       "plugin_name"   : "com.sap.hana.di.calculationview", 
>       "plugin_version": "4.0.0.0"},
>    "hdbprocedure" : { 
>       "plugin_name"   : "com.sap.hana.di.procedure", 
>       "plugin_version": "4.0.0.0"},
>    "<hdb_file_suffix_#>" : {
>       "plugin_name"   : "<plugin_NAME>","<plugin_VERSION>" }
>     }
> }
> ```

> ### Note:  
> If the plug-in version is defined at both the global and local \(individual\) level, as illustrated in the following example, then the version specified for an HDI build plug-in at the individual level takes precedence.

```json
{
"plugin_version": "4.0.0.0",
"file_suffixes" : {
   "hdbsynonym" : { 
      "plugin_name"   : "com.sap.hana.di.synonym"},
   "hdbview" : { 
      "plugin_name"   : "com.sap.hana.di.view"}, 
   "hdbcalculationview" : { 
      "plugin_name"   : "com.sap.hana.di.calculationview", 
      "plugin_version": "4.0.20.0"},
   "hdbprocedure" : { 
      "plugin_name"   : "com.sap.hana.di.procedure", 
      "plugin_version": "4.0.20.0"}
    }
}
```

The plug-in **name** corresponds to the plug-in name in reverse-URL notation, for example, `com.sap.hana.di.procedure` or `com.sap.hana.di.view`.

**Related Information**  


[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_3_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

