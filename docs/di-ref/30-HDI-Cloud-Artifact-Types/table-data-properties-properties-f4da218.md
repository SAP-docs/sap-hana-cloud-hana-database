<!-- loiof4da2181909f48a6a36904b7f5599780 -->

# Table Data Properties \(.properties\)

Insert data from files referenced in the “`.properties`” file format into database tables which are managed by SAP HDI.



The Table Data Properties plug-in can be used to insert data from files listed in the “`.properties`” file format into database tables which are managed by SAP HDI, for example, to manage translated texts which must be available at the database layer. The information about the target table, additional constant values, and column mappings are provided by means of a special “`!tabledata`” header inside the file in order to make the file self-contained and to simplify the translation process for language `.properties` files.

The special `extractLanguageCodeFromFileName` function can be used to automatically extract language-code information from the file’s name. For example, for “`OBJECT_en_US.properties`” the language code “`en_US`” gets extracted. The file encoding is UTF-8, and not ISO-8859-1/Latin-1. The translation process for HDI artifacts can also handle `.properties` files as UTF-8 encoded files. In addition, the translation process copies the `!tabledata` header from the original `.properties` file into the translated `.properties` files.

> ### Restriction:  
> A `.properties` file does not support the `\u` escape sequence.

The special `target_table` value “`#BIMC_DESCRIPTIONS`” must be used when translated texts should be deployed for calculation views, because these translations are stored inside the database-internal table `_SYS_BI.BIMC_DESCRIPTIONS`. For the `BIMC_DESCRIPTIONS` table, a schema entry in the HDI properties file is ignored and always replaced by the name of the container's runtime schema., unless the schema name `_SYS_BIC` is used, as shown in the code sample below.

To support so-called "multi-key" properties in the `.properties` file, it is possible to use the `"multi_key_separator"` tag in the `!tabledata` section. For example, in <code>"multi_key_separator": "<i class="varname">&lt;key_separator&gt;</i>"</code>, the value specified in <code><i class="varname">&lt;key_separator&gt;</i></code> defines a single character that is used to separate the key into a fixed number of subkeys according to the columns specified in the `"column_mappings"` section of the `.properties` file. When using the `"multi_key_separator"` property, bear in mind the following restrictions:

-   <code><i class="varname">&lt;key_separator&gt;</i></code> cannot be any of the following characters: ‘=’, ‘:’, ‘\#’, ‘!’, or ‘ ‘ \(space\)

-   It is not permitted to "escape" the `key_separator` in subkeys.

-   A subkey that has no value is treated as empty and not as NULL.


> ### Note:  
> The Table Data Properties plug-in can also be used to model `.tags` files.



<a name="loiof4da2181909f48a6a36904b7f5599780__section_w1k_2f3_1hb"/>

## Example Artifact Code

The following code shows a simple example of a design-time properties definition for SAP HDI. In this example, `TEXT_TABLE` is a table that was created by an HDI table definition which has at least the columns `"OBJECT"`, `"LANGUAGE"`, `"KEY"`, and `"VALUE"`, and where the primary key consists of at least `"OBJECT"`, `"LANGUAGE"`, and `"KEY"`.

> ### Code Syntax:  
> `/src/OBJECT_en_US.properties`
> 
> ```json
> #!tabledata 
> #{ 
> # "target_table" : "TEXT_TABLE", 
> # "column_mappings" : { 
> #    "OBJECT" : { "type" : "constant", 
> #                 "value" : "name.space::VIEW" }, 
> #    "LANGUAGE" : { "type" : "function", 
> #                   "name" : "extractLanguageCodeFromFileName", 
> #                   "parameters": { "file_name": "OBJECT"} }, 
> #    "KEY" : 1, 
> #    "VALUE" : 2 
> # } 
> #} 
> # Note: The table data header ends on the first empty line or  
> # earlier on the second occurrence of the !tabledata marker 
> # Note: Format of .properties entries: 
> # 
> # 
> # <metadata for translation process> 
> # <key>=<value> 
> # 
> # XCOL, 120 
> KEY_1=First Key 
> # XCOL, 120 
> KEY_2=Second Key 
> # XCOL, 120 
> PARAMETER_1=Parameter One 
> # XCOL, 120 
> CUSTOMERS_HIERARCHY=CUSTOMERS Hierarchy
> ```

In the following example, the texts for calculation views are imported into `_SYS_BI.BIMC_DESCRIPTIONS`.

> ### Code Syntax:  
> `/src/BASE_CV_en_US.properties`
> 
> ```json
> #!tabledata
> #{
> #  "target_table"     : "#BIMC_DESCRIPTIONS",
> #  "column_mappings"  : {
> #    "QUALIFIED_NAME" : { "type"  : "constant", "value" : "BASE_CV" },
> #    "LANG"           : { "type"  : "function", "name"  : "extractLanguageCodeFromFileName", "parameters": { "file_name": "BASE_CV" } },
> #    "SCHEMA_NAME"    : { "type"  : "constant", "value" : "_SYS_BIC" },
> #    "ID"             : 1,
> #    "DESCRIPTION"    : 2
> #}
> #}
> #!tabledata
> # #<metadata>
> # <ID>=<DESCRIPTION>
> 
> # XCOL, 120
> K1=K1 Desc
> # XCOL, 120
> K2=K2 Desc
> # XCOL, 120
> &&VIEW_NAME&&=BASE_CV Description
> # XCOL, 120
> K3=K3 Desc
> # XCOL, 120
> K4=K4 Desc
> 
> ```

The following example shows how to use the `"multi_key_separator"` tag to define "." \(dot\) as the character to use to separate the subkeys. In this example, `"sap::myPropertyTable"` is a table created by an SAP HDI table definition that has at least the columns `"OBJECT"`, `"LANGUAGE"`, `"KEY1"`, `"KEY2"`, `"KEY3"`, and `"VALUE"`, where the primary key consists of at least `"OBJECT"`, `"LANGUAGE"`, and `"KEY1"`, `"KEY2"`, `"KEY3"`.

> ### Code Syntax:  
> `/src/mkp_en_US.properties`
> 
> ```json
> #!tabledata
> #{ 
> #  "target_table"     : "sap::myPropertyTable",
> #  "multi_key_separator" : ".",
> 
> #  "column_mappings"  : {
> #    "OBJECT" :    { "type"  : "constant", "value" : "SKPR07 object" },
> #    "LANGUAGE"  : { "type"  : "function", 
> #		        "name"  : "extractLanguageCodeFromFileName", 
> #                     "parameters": { "file_name": "mkp" } 
> #                  },
> #    "KEY1"     : 1,
> #    "KEY2"     : 2,
> #    "KEY3"     : 3,
> #    "VALUE"    : 4
> #}
> #}
> 
> #!tabledata
> 
> # #<metadata>
> # <key>.<key2>.<key3>=<value>
> 
> # XCOL, 120 
> .key2_2.key3_3=key1 is missing
> # XCOL, 120 
> key_1.key2_2.key3_3=OK
> # XCOL, 120
> key_1..key3_3=key2 is missing
> # XCOL, 120 
> key_1.key2_2.=key3 is missing
> 
> ```



<a name="loiof4da2181909f48a6a36904b7f5599780__section_wlm_df3_1hb"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```json
> "properties" : {
>    "plugin_name" : "com.sap.hana.di.tabledata.properties" 
> }, 
> "tags" : { 
>    "plugin_name" : "com.sap.hana.di.tabledata.properties"
> }
> ```

**Related Information**  


[Table Data \(.hdbtabledata\)](table-data-hdbtabledata-35c4dd8.md "Insert data from other files (for example, CSV, .properties, or .tags files) into database tables.")

[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

