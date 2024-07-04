<!-- loioeb019bb757404a0591182ac7acf05400 -->

# Enterprise Search Configurations \(.hdbeshconfig\)

Create and deploy a search configuration with the SAP HANA database's deployment infrastructure \(HDI\).



The enterprise-search-configuration plug-in transforms a design-time, enterprise-search configuration resource \(specified in an `.hdbeshconfig` artifact\) into a search database object. The plug-in reads the search configuration defined in a `.hdbeshconfig` file and passes it to the `SYS.ESH_CONFIG()` procedure to create the search configuration in SAP HANA.



## Example Artifact Code

The `.hdbeshconfig` file uses the same syntax as the built-in procedure `SYS.ESH_CONFIG()` except for the envelope part, which is not required with HDI. The `.hdbeshconfig` file contains everything from the content part of a JSON configuration used for `esh_config()`. The following example shows the contents of an `.hdbeshconfig file`:

> ### Code Syntax:  
> `.hdbeshconfig`
> 
> ```json
> {
>   "Fullname": "awards",
>   "EntityType": {
>     "@Search.searchable": true,
>     "@EnterpriseSearch.enabled": true,
>     "Properties": [
>       {
>         "@EnterpriseSearch.key": true,
>         "@UI.identification": [ { "position": 1 } ],
>         "Name": "id"
>       },
>       {
>         "@UI.identification": [ { "position": 2 } ],
>         "@Search.defaultSearchElement": true,
>         "Name": "title"
>       },
>       {
>         "@UI.identification": [ { "position": 3 } ],
>         "@Search.defaultSearchElement": true,
>         "Name": "abstract"
>       }
>     ]
>   }
> }
> ```

The view "`awards`" referenced in the search configuration example above can be created using an SQL view \(`.hdbview`\) file. However, there can only be one search configuration for a single view. Object names may be prefixed with a name space, for example, `"Fullname": "com.sap.search.example::awards"`.

In contrast to the interface of the `esh_config()` procedure, each `.hdbeshconfig` file contains a single search configuration. All references to other database objects are provided without a schema prefix since these objects are located withing the schema of the same HDI container.

> ### Tip:  
> It is possible to reference objects outside the HANA DI container schema. However, this would require an `.hdbsynonym` file \(and optionally a `.hdbsynonymconfig`\) file that defines synonyms for the objects stored in the remote schema.



## Plug-in Configuration

To deploy search configurations with HDI, the design-time artifact type for enterprise search configurations \(`.hdbeshconfig`\) has to be included in the HDI container configuration file \(`.hdiconfig`\), as shown in the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> {
>   "file_suffixes": {
>     "hdbtable": {
>       "plugin_name": "com.sap.hana.di.table"
>     },
>     "hdbview": {
>       "plugin_name": "com.sap.hana.di.view"
>     },
>     "hdbeshconfig": {
>       "plugin_name": "com.sap.hana.di.eshconfig"
>     }
>   }
> }
> ```

In addition to this configuration, the HDI plug-in library `com.sap.hana.di.eshconfig` must be added to the HDI container.

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Search Developer Guide](https://help.sap.com/viewer/05c9edaee7fe4d28ab3627d0b1583df6/2024_3_QRC/en-US/ce86ef2fd97610149eaaaa0244ca4d36.html "With SAP HANA Cloud, your users can search tables and views much like they would when searching for information on the Internet. In SAP HANA, you can either query data using OData service definitions, directly with SQL queries, or via the built-in procedure sys.esh_search().") :arrow_upper_right:

