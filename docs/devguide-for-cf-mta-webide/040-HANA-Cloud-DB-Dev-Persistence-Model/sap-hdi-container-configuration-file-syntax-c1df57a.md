<!-- loioc1df57a55f774cbea9097bded789fd36 -->

# SAP HDI Container Configuration File Syntax

In SAP HANA Deployment Infrastructure \(HDI\), the JSON syntax is used to format the content of the HDI container-configuration file \(`.hdiconfig`\).



> ### Sample Code:  
> ```
> {
>   "plugin_version": "4.0.0.0",  // optional, ensures no deployment to on-premise
>   "file_suffixes" : {
>     "<file_suffix_1>" : {
>       "plugin_name"   : "<plugin_NAME>",
>       "plugin_version": "<plugin_VERSION>" // If different from global version 
>     },
>     "<file_suffix_2>" : {
>       "plugin_name"   : "<plugin_NAME>"
>     },
>     "<file_suffix_#>" : {
>       "plugin_name"   : "<plugin_NAME>",
>       "plugin_version": "<plugin_VERSION>" // If different from global version 
>     },
>     {
>       [...]
>     }
>   }
> }
> 
> ```



<a name="loioc1df57a55f774cbea9097bded789fd36__section_ogr_2c2_1t"/>

## file\_suffixes

Define one or more file suffixes which you want to bind to a build plug-in for deployment to an HDI container. The file suffix specifies the **type** of database artifact, for example, `.hdbsequence` or `.hdbview`.

> ### Sample Code:  
> ```
> {
>   "file_suffixes" : {
>     "<file_suffix_1>" : {
>       "plugin_name"   : "<plugin_NAME>",
>       "plugin_version": "<plugin_VERSION>" //optional
>     }
>   }
> }
> 
> ```

You can use the asterisk character \(\*\) to define a **global** file suffix which binds all remaining, unbound file suffixes to a specific build plug-in, for example, to bind all unbound file suffixes to the `Copy Only` plug-in.

> ### Restriction:  
> All “`hdi*`” file suffixes \(for example, `.hdiconfig` or `hdinamespace`\) are reserved for use with HDI; these file suffixes cannot be \(re\)configured.

The following example of an abbreviated HDI configuration file illustrates how the design-time artifact types \(for example, `.hdbsynonym`, `.hdbtable`, `.hdbcalculationview`\) are mapped to their corresponding HDI build plug-in:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```
> {
>   "plugin_version" : "2.0.20.0",   // global, optional, defaults to 0.0.0.0
>   "file_suffixes" : {
> 
>       "hdbsynonym" : { 
>         "plugin_name" : "com.sap.hana.di.synonym"
>       }, 
>       "hdbsynonymconfig" : { 
>         "plugin_name" : "com.sap.hana.di.synonym.config" 
>       }, 
>       "hdbtable" : { 
>         "plugin_name" : "com.sap.hana.di.table" 
>       }, 
>       "hdbcalculationview" : {
>         "plugin_name" : "com.sap.hana.di.calculationview" 
>       },
>       "<file suffix 2>" : {
>        "plugin_name"   : "<plugin name>",
>        "plugin_version": "<plugin_version>" //local, optional
>       }
> }
> ```



<a name="loioc1df57a55f774cbea9097bded789fd36__section_hhw_2c2_1t"/>

## plugin\_name

Use the `plugin_name` key to specify the name of the HDI build plug-in that you want to associate with a specific HDI artifact type.

> ### Sample Code:  
> ```
> 
> "plugin_name"   : "<plugin_NAME>", 
> 
> ```

For example, you can associate the artifact suffix for the HDB SQL view \(`.hdbview`\) with the build plug-in `com.sap.hana.di.view`.

> ### Sample Code:  
> ```
> 
> "plugin_name"   : "com.sap.hana.di.view", 
> 
> ```



<a name="loioc1df57a55f774cbea9097bded789fd36__section_gmb_fc2_1t"/>

## plugin\_version \(optional\)

Use the optional `plugin_version` key to specify the version number of the HDI build plug-in that you want to associate with one HDI plug-in.

> ### Sample Code:  
> ```
>  
> "plugin_version": "<Major_Version>.<Minor_Version>.<Revision_Version>.<Patch_Version>" 
> 
> ```

> ### Tip:  
> To specify one plug-in version for **all** configured plug-ins, define `"plugin_version"` globally at the start of the configuration file. To specify a specific version for a particular plug-in, define `"plugin_version"` locally alongside the plug-in name to which the specific version refers. The locally defined plug-in version takes precedence over the globally defined version.

The value of the `plugin_version` key is interpreted as a minimal required version of the build plug-in. Version numbers follow the format <code><i class="varname">&lt;major&gt;</i>.<i class="varname">&lt;minor&gt;</i>.<i class="varname">&lt;Revision_Version&gt;</i>.<i class="varname">&lt;patch&gt;</i></code>. An installed build plug-in with the same major version is considered to be compatible if its minor version is greater than the requested minor version, or its minor version is equal to the requested version and the revision or patch number is greater than \(or equal to\) the requested version.

> ### Sample Code:  
> HDI Plug-in Version for SAP HANA Cloud
> 
> ```
>  
> "plugin_version": "4.0.0.0"
> 
> ```

For Cloud versions of HANA DI \(HDI\) build plug-ins, the version number is optional. However, as illustrated in the example above, you can use the global `"plugin_version"` number `4.0.0.0`, if you want to ensure that all HDI build plug-ins are only intended for use in the Cloud. Using the format `4.0.0.0` will prevent this version of the build plug-in from being deployed in an on-premise environment. The same rule applies for the specification of a particular plug-in version at the local level, for example, if you want to specify a particular version for an individual HDI build plug-in.

> ### Note:  
> The version number defined at the local level for a specific HDI build plug-in overrides the version defined at the global level for all HDI build plug-ins.

**Related Information**  


[Set up an SAP HDI Container for a Multitarget Application](set-up-an-sap-hdi-container-for-a-multitarget-application-1ca6415.md "Set up the environment required for the deployment to the SAP HANA Deployment Infrastructure (HDI) of a multitarget application's database artifacts.")

[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2024_1_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

