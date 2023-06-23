<!-- loio35c4dd829d2046f29fc741505302f74d -->

# Table Data \(.hdbtabledata\)

Insert data from other files \(for example, CSV, `.properties`, or `.tags` files\) into database tables.



The table data plug-in can be used to insert data defined in other design-time artifacts \(for example, `.hdbtabledata` and `.csv` files\) into database tables which are managed by SAP HANA DI and are not system-versioned, temporary, or virtual tables. It is possible to import data from collection tables but only with restrictions. It is not recommended to use `.hdbtabledata` artifacts to import test content or demo data if you do not want to use those artifacts in the productive scenario.

> ### Caution:  
> Do not use the table data plug-in for data that you intend to later modify at run time.

Since the table data plug-in has ownership of the data it manages, any run-time modification matching the filter criteria of the table-data artifact is reverted on deployment \(or redeployment\) of the corresponding table-data artifacts. A redeployment is also triggered by any modification of the `CSV` file or table artifact.

> ### Tip:  
> If you want to import into the target table any data that is not defined in a CSV file, use the [Column-Import Scenario](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__subsection_iss_pqd_5bb) described below. This prevents data loss during any subsequent deployment.

This topic also includes information about how to import “simplified” key-value table data, for example, data for translation that is stored in `.properties` or `.tags` files. For more information, see [Simplified Key-Value Table Data \(.properties and .tags\)](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__section_b1f_srd_5bb)



## Example Artifact Code

The following code shows a simple \(incomplete\) example of a table-data design-time definition for HDI; the format adheres to the JSON syntax:

> ### Code Syntax:  
> `/src/TABLE.hdbtabledata`
> 
> ```
> {
>   "format_version": 1,
>   "imports": 
>    [
>     {
>     "column_mappings" : {
>         "tableCol1" : 1, 
>         "tableCol2" : "csvCol4", 
>         "tableCol3" : { 
>           "type" : "constant", 
>           "value" : "Constant"
>         },
>         "tableCol4" : { 
>           "type" : "function", 
>           "name" : "range", 
>           "parameters" : { 
>             "increment_by" : "1", 
>             "start_with" : "1" 
>           }
>         },
>         "tableCol5" : { 
>           "type" : "function", 
>           "name" : "decodeBase64String", 
>           "parameters" : { 
>             "column_name" : "csvCol2" 
>           } 
>         }
>      }, 
>      "import_settings" : {
>         "import_columns" : [ 
>            "tableCol1", 
>            "tableCol2",
>            "tableCol3"
>         ],
>         "include_filter" : [ 
>          { "tableCol1" : "de", // ( "de" and "X" ) 
>            "tableCol4" : "X" }
>         ],
>         "exclude_filter" : [ 
>          { "tableCol1" : "de", // ( "de" and "10" ) 
>            "tableCol3" : "10" 
>          } 
>         ]
>      }, 
>      "source_data" : { 
>        "data_type" : "CSV", 
>        "file_name" : "com.sap.hana.example.data::data.csv", 
>        "has_header" : true,
>        "no_data_import": false,
>        "delete_existing_foreign_data": false,
>        "dialect"   : "HANA",  
>        "type_config" : { 
>           "delimiter" : "," 
>         } 
>       }, 
>      "target_table" : "com.sap.hana.example::TABLE"  
>     }
>    ] 
> }
> ```



<a name="loio35c4dd829d2046f29fc741505302f74d__section_ann_np5_fz"/>

## Imports

The `imports` property defines the following objects:

-   `target_table`

    Specifies the name of the database table into which the data should be inserted. The given name must point to a database table which is also managed by SAP HDI, for example, the name cannot point to a database synonym or to a database table in another schema.

-   [`source_data`](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__section_rqz_f45_fz)

    Describes the structure of the data file which is used as data source for the import. It contains information about the general type of the data file, its name, and format details.

-   [`import_settings`](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__section_f3y_f45_fz)

    Specifies the target table columns and filters for the data that is inserted into the target table

-   [`column_mappings`](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__section_anj_jkb_4gb)

    “`import_settings`” with the data specified in “``”




<a name="loio35c4dd829d2046f29fc741505302f74d__section_rqz_f45_fz"/>

## source\_data

The data source to be used for the import operation is defined in the `source_data` attribute; it describes the structure of the data file which is used as data source for the import as well as the type of the data file, its file name, and additional format details.

**Source Data Attributes**


<table>
<tr>
<th valign="top">

Attribute



</th>
<th valign="top">

Description



</th>
<th valign="top">

Mandatory



</th>
</tr>
<tr>
<td valign="top">

 `data_type` 



</td>
<td valign="top">

The type of the data file. Supported values are: “CSV” and “PROPERTIES”

> ### Note:  
> The data type “PROPERTIES” specifies data stored in a `.properties` file format used, which is used in translation scenarios in HDI. Unlike the CSV data type, no configuration options are required for the “PROPERTIES” data type.



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

 `file_name` 



</td>
<td valign="top">

The name of a deployed table data source file, for example `data.csv`; the file has to be deployed via the table data source plug-in and follows the normal run-time naming scheme



</td>
<td valign="top">

Yes



</td>
</tr>
<tr>
<td valign="top">

 `has_header` 



</td>
<td valign="top">

Boolean flag to indicate whether the data file contains a header \(default = “`false`”\)



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `no_data_import` 



</td>
<td valign="top">

“`false`”\).

> ### Caution:  
> If set to “true”, all data in the target table is overwritten even if matches are found in the key reservations. For more information, see Boolean flag to indicate that the data file should not be imported and an undeploy-call does not delete entries according to the key specifications \(default = "false"\). For more information, see *Key-Reservation Import Scenario* below.



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `delete_existing_foreign_data` 



</td>
<td valign="top">

Boolean flag to indicate that in the deploy phase existing data in the target table will be deleted according to the current key specifications \(defined in the `include_filters`\); that is, the keys are used to delete foreign entries and no check is performed for existing matching foreign data.

> ### Caution:  
> If set to “true”, all data in the target table is overwritten even if matches are found in the key reservations. For more information, see *Key-Reservation Import Scenario* below.



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `type_config` 



</td>
<td valign="top">

Object to further configure the data parser to match the data file format



</td>
<td valign="top">

No



</td>
</tr>
<tr>
<td valign="top">

 `dialect` 



</td>
<td valign="top">

Specifies the type of data to import. Possible dialects are: `HANA`. Note that the default configuration can be overwritten by `type_config`.



</td>
<td valign="top">

No



</td>
</tr>
</table>

The <code>“data_type” : “CSV”</code> specifies a source file whose contents are formatted with comma-separated values \(CSV\). For CSV source files, the settings allowed for the configuration type \(`type_config`\) attribute are described in the following table:

**Configuration Type Attributes for the Data Type CSV**


<table>
<tr>
<th valign="top">

CSV Attribute



</th>
<th valign="top">

Description



</th>
<th valign="top">

Default Value



</th>
</tr>
<tr>
<td valign="top">

 `line_terminator` 



</td>
<td valign="top">

Character to use as line terminator, for example, “\\n” or “\\r” 



</td>
<td valign="top">

auto detect: \\n, \\r, \\r\\n



</td>
</tr>
<tr>
<td valign="top">

 `delimiter` 



</td>
<td valign="top">

Character to use as record delimiter, for example, “,” \(comma\) or “;” \(semi-colon\)

> ### Caution:  
> *<delimiter\>**<delimiter\>* \(,,\) or \(;;\) is treated as NULL.
> 
> *<delimiter\>**<quote\_character\>**<quote\_character\>**<delimiter\>* \(,"",\) or \(;"";\) is treated as an empty value.
> 
> *<delimiter\>**<space\>**<delimiter\>* \(, ,\) or \(; ;\) is treated as a space



</td>
<td valign="top">

,



</td>
</tr>
<tr>
<td valign="top">

 `do_quote` 



</td>
<td valign="top">

Flag to enable quoting



</td>
<td valign="top">

true



</td>
</tr>
<tr>
<td valign="top">

 `quote_character` 



</td>
<td valign="top">

Character to use as quoting character for records, for example, " \(double quote\) for records like “value,1” 



</td>
<td valign="top">

"



</td>
</tr>
<tr>
<td valign="top">

 `do_escape` 



</td>
<td valign="top">

Flag to enable escaping



</td>
<td valign="top">

false



</td>
</tr>
<tr>
<td valign="top">

 `escape_character` 



</td>
<td valign="top">

Character to use as escaping character, for example, \\ \(backslash\) for escaped records such as “a\\nb” \(to escape the “n” character\)



</td>
<td valign="top">

\\



</td>
</tr>
<tr>
<td valign="top">

 `do_weak_escape` 



</td>
<td valign="top">

Flag to enable a weak-mode of escaping; only the record delimiter, the quote character, and the escape character are considered to be escaped



</td>
<td valign="top">

true



</td>
</tr>
<tr>
<td valign="top">

 `use_escape_sequences` 



</td>
<td valign="top">

Flag to enable the standard set of escape characters sequences for example, “\\n” “\\r” “\\t” 



</td>
<td valign="top">

true



</td>
</tr>
</table>

The `hdbtabledata` file brings the content specified in the corresponding CSV file and takes ownership of the content regarding the key restrictions. For import operations where applications still want to be able to add content manually to the table but also want to ensure that no-one else can interfere with the content, the following scenarios are available:

-   [Key-Reservation Scenario](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__subsection_crs_pqd_5bb)
-   [Column-Import Scenario](table-data-hdbtabledata-35c4dd8.md#loio35c4dd829d2046f29fc741505302f74d__subsection_iss_pqd_5bb)



### Key-Reservation Import Scenario

The source-data parameters `no_data_import` and `delete_existing_foreign_data` are provided to enable you to implement the so-called Key-Reservation scenario, which enables you to import data manually into the target table and which is split into the following phases:

-   The table-building phase:

    In this phase, the key reservation is performed by the specifications in the `hdbtabledata` file, but no CSV data is imported into the target table. For this phase, you must set the following parameters:

    -   <code>“no_data_import”: true</code>

    -   <code>“delete_existing_foreign_data”: false</code>


-   The table-population phase:

    In this phase, the application adds data to the CVS file it wants to use to populate the target table. From this point, it is not recommended to manually insert content into the target table as the manually inserted data will be deleted on redeployment. For this phase, you must set the following parameters:

    -   <code>“no_data_import”: false</code>

    -   <code>“delete_existing_foreign_data”: true</code>





### Import Column Scenario

The parameters `column_mappings` and `import_columns` are provided to enable you to implement the so-called Import-Column scenario, where importing data using the “key-reservation” scenario is not appropriate.

In the “import-column” scenario, the target table is extended by adding a column indicating that content is imported \(for example, `column_name = IMPORTED (NVARCHAR(1))`\). Next, the application can extend its keys, so that the `hdbtabledata` file imports values into the indicated column with <code>“Y”</code>, and the application itself can **add** other values, for example, “IMPORTED='N'” \(<code>"<b>IMPORTED</b>": { "type": "constant", "value": "<b>N</b>" }</code>\).

In the following example, “`mytable`” has three columns: <code>"A", "B", "<b>IMPORTED</b>"</code>

> ### Sample Code:  
> ```
> 
> "imports": [ 
>   { "target_table": "myTable", 
>     "source_data": { 
>       "data_type": "CSV",  
>       "file_name": "sap.pdms_dss_content::package.csv",  
>       "has_header": true,  
>       "type_config": {  
>          "delimiter" : ";" 
>       }  
>     },  
>     "column_mappings": { "IMPORTED": { "type": "constant", "value": "Y" } 
>     }, 
>     "import_settings" : {  
>        "import_columns": ["A", "B", "IMPORTED"] 
>     }  
>   }, 
> ```



<a name="loio35c4dd829d2046f29fc741505302f74d__section_f3y_f45_fz"/>

## import\_settings

Both the `import_settings` and the `import_columns` attributes are mandatory.`import_settings` specifies the target table columns and defines filters for the data that is inserted into the target table;

> ### Sample Code:  
> Overview of Table-data Import Settings
> 
> ```
> "import_settings" : { 
>   "import_columns" : [ 
>     "tableCol1", 
>     "tableCol2", 
>     "tableCol3", 
>     "tableCol4", 
>     "tableCol5" 
>   ], 
>   "include_filter" : [ 
>     { 
>       "tableCol1" : "de",   // ( "de" and "X" ) 
>       "tableCol4" : "X" 
>     },                      // or 
>     { 
>       "tableCol1" : "en",   // ( "en" and "X" ) 
>       "tableCol4" : "X" 
>     } 
>   ], 
>   "exclude_filter" : [ 
>     { 
>       "tableCol1" : "de",   // ( "de" and "10" ) 
>       "tableCol3" : "10" 
>     } 
>   ] 
> }
> ```



<a name="loio35c4dd829d2046f29fc741505302f74d__section_s2s_d45_fz"/>

## import\_columns

The `import_columns` list is mandatory; it defines the columns of the target table which are relevant for the data import. More specifically, the `import_columns` attribute enables you to connect the target table’s columns \(specified in the “`import_settings`” with the data specified in the “`source_data`” section.

> ### Sample Code:  
> Defining the Names of Table Columns from which to Import Data
> 
> ```
> "import_settings" : { 
>   "import_columns" : [ 
>     "tableCol1", 
>     "tableCol2", 
>     "tableCol3", 
>     "tableCol4", 
>     "tableCol5" 
>   ], 
>   "include_filter" : [  
>   ], 
>   "exclude_filter" : [ 
>   ] 
> }
> ```

In the example above, the mapping between the target table columns and the source CSV file produces the following import results:

-   `"tableCol1" : 1,`

    “tableCol1” in the target table is filled with data taken from the first column of the source CSV file

-   `"tableCol2" : "csvCol4",`

    “tableCol12” in the target table is filled with data taken from the column named “csvCol4”in the source CSV file

-   `"tableCol3" : { "type" : "constant", "value" : "Constant" }`

    “tableCol3” in the target table is filled with data defined by the value “`Constant`”




<a name="loio35c4dd829d2046f29fc741505302f74d__section_qml_1kb_4gb"/>

## \[in|ex\]clude\_filter

It is also possible to specify filtering rules, for example `include_filter` and `exclude_filter`, which restrict the set of data rows inserted into the target table. If no `include_filter` is defined, then the data imported will collide with other imports into the target table. If both export and import filters are specified, the exclude filter is evaluated after the include filter. This enables you to filter out values that have a matching include filter.

> ### Caution:  
> To prevent the accidental or unwanted deletion of data, it is strongly recommended to use the `include_filter` to control the import of data into the target table, for example, by setting filters that specify what information is imported into which column. Without include filters the table-data import operation will always delete existing content and redeploy content from the source CSV file into the target table.

The following code example uses comments \(`// (comment)`\) to indicate how the include filters determine the data to be imported \(for example, `"de"` and `"X"`\) from the specified import columns \(`"tableCol1"` and `"tableCol4"`, respectively\).

> ### Sample Code:  
> Defining Filters to Include and Exclude Data During Table Import
> 
> ```
> "import_settings" : { 
>   "import_columns" : [ 
>     "tableCol1", 
>     "tableCol2", 
>     "tableCol3", 
>     "tableCol4", 
>     "tableCol5" 
>   ], 
>   "include_filter" : [ 
>     { 
>       "tableCol1" : "de",   // ( "de" and "X" ) 
>       "tableCol4" : "X" 
>     },                      // or 
>     { 
>       "tableCol1" : "en",   // ( "en" and "X" ) 
>       "tableCol4" : "X" 
>     } 
>   ], 
>   "exclude_filter" : [ 
>     { 
>       "tableCol1" : "de",   // ( "de" and "10" ) 
>       "tableCol3" : "10" 
>     } 
>   ] 
> }
> ```



<a name="loio35c4dd829d2046f29fc741505302f74d__section_anj_jkb_4gb"/>

## column\_mappings

The <code>“column_mappings”</code> object in the import description connects the target table’s columns specified in the <code>“import_settings”</code> with the data specified in the <code>“source_data”</code> section.

> ### Note:  
> In one exceptional case it is possible to omit the <code>“column_mappings”</code> object. In this case, the data file has a header \(defined in <code>“source_data”</code>\), the names of the columns in the target table are the same as those in the CSV header, and a 1:1 mapping must exist between the CSV columns and the table columns.

In all other cases, it is mandatory to specify column mappings, as illustrated in the following example:

> ### Sample Code:  
> Mapping Columns for Data Import from CSV Files
> 
> ```
> … 
> "column_mappings" : { 
>   "tableCol1" : 1, 
>   "tableCol2" : "csvCol4", 
>   "tableCol3" : { 
>     "type" : "constant", 
>     "value" : "Constant" 
>   }, 
>   "tableCol4" : { 
>     "type" : "function", 
>     "name" : "range", 
>     "parameters" : { 
>       "increment_by" : "1", 
>       "start_with" : "1" 
>     } 
>   }, 
>   "tableCol5": { 
>     "type" : "function", 
>     "name" : "decodeBase64", 
>     "parameters" : { 
>       "column_name" : "csvCol2" 
>     } 
>   } 
> } 
> … 
> ```

The following tables lists and describes the supported column mappings:

**Supported Table-Import Column Mappings**


<table>
<tr>
<th valign="top">

Mapping Type



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 *<columnName\>* - Integer X



</td>
<td valign="top">

Maps the data in column “X ”of the data file to the column with name “columnName” of the target table



</td>
<td valign="top">

CSV column 1 is mapped to target table column “tableCol1” 



</td>
</tr>
<tr>
<td valign="top">

 *<columnName\>* - String X



</td>
<td valign="top">

Maps the data in the column identified with header name “X” to the column with *<columnName\>* of the table \(requires headers in the data file\)



</td>
<td valign="top">

The data in the column specified with header name “csvCol4” is mapped to column “tableCol2” 



</td>
</tr>
<tr>
<td valign="top">

 *<columnName\>* - Function X



</td>
<td valign="top">

Calculates the value to map to the column *<columnName\>* by means of the function “X” 



</td>
<td valign="top">

Base16/base64 decodings



</td>
</tr>
</table>

The following functions can be used in a column mapping scenario to calculate the value to map to a specified column:

**Supported Column Mappings Functions**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Parameters



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

constant



</td>
<td valign="top">

 `value` 



</td>
<td valign="top">

Maps the column to a constant value



</td>
</tr>
<tr>
<td valign="top">

range



</td>
<td valign="top">

`start_with` 

`increment_by`



</td>
<td valign="top">

Uses a constant sequence to fill the column value, starting with the value “`start_with`”; for every row the value will be increased by “`increment_by`” 



</td>
</tr>
<tr>
<td valign="top">

decodeBase16



</td>
<td valign="top">

`column_name` 

`column_number` 



</td>
<td valign="top">

Decodes a given value from the data file as a base16 string; the value from the CSV file is determined by `column_name` or `column_number` 



</td>
</tr>
<tr>
<td valign="top">

decodeBase64



</td>
<td valign="top">

`char62` \(optional\)

`char63` \(optional\)

column\_name

`column_name` 

`column_number` 



</td>
<td valign="top">

Decodes a given value from the data file as a base64 string; the value from the CSV file is determined by `column_name` or `column_number`; the optional `char62` and `char63` parameters can be used to define the encoding characters for the values 62 and 63 \(defaults are “+” and “/”\)



</td>
</tr>
<tr>
<td valign="top">

getCurrentSchemaName



</td>
<td valign="top">

\-



</td>
<td valign="top">

Returns the name of the container’s run-time schema.



</td>
</tr>
<tr>
<td valign="top">

extractLanguageCodeFromFileName



</td>
<td valign="top">

 `file_name` 



</td>
<td valign="top">

Extracts the language code from the named file using the parameter `file_name` \(the original file name without suffix and language code\). The following file-name formats are supported:

-   *<file\_name\>*\_*<languageCode\>*
-   *<file\_name\>*

    No specified language code \(corresponds to the original language\)




</td>
</tr>
</table>



<a name="loio35c4dd829d2046f29fc741505302f74d__section_b1f_srd_5bb"/>

## Simplified Key-Value Table Data \(`.properties` and `.tags`\)

The Table Data Properties plug-in can be used to insert data from files in the "`.properties`" file format into database tables which are managed by SAP HANA DI, for example, to manage translated texts which must be available at the database layer. The information about the target table, additional constant values, and column mappings are provided by means of a special `!tabledata` header inside the file; this ensures that the file is self-contained and simplifies the translation process for language-based `.properties` files.

> ### Sample Code:  
> `OBJECT_en_US.properties`
> 
> ```
> #!tabledata 
> #{ 
> # "target_table"    : "TEXT_TABLE", 
> # "column_mappings" : { 
> #   "OBJECT"   : { "type" : "constant", 
> #                  "value" : "name.space::VIEW" }, 
> #   "LANGUAGE" : { "type" : "function", 
> #                  "name" : "extractLanguageCodeFromFileName", 
> #                  "parameters": { "file_name": "OBJECT"} }, 
> #   "KEY"   : 1, 
> #   "VALUE" : 2 
> # } 
> #} 
> 
> # Note: The table data header ends on the first empty line or
> # earlier on the second occurrence of the !tabledata marker 
> 
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

You can use the function `extractLanguageCodeFromFileName` to automate the extraction of the language code information from the name of the `.properties` file. For example, the language code “en\_US” would be extracted from the file name `OBJECT_en_US.properties`.

The file encoding for `.properties` files is UTF-8, and a `.properties` file does not support the use of the `\u` escape combination. The translation process for HDI artifacts treats `.properties` files as UTF-8 encoded files. In addition, the translation process copies the “`!tabledata`” header from the original `.properties` file into the translated `.properties` files.

The special “`target_table`” value “`#BIMC_DESCRIPTIONS`” must be used when translated texts are deployed for calculation views. This is because the translation text is stored inside the database-internal table `_SYS_BI.BIMC_DESCRIPTIONS`.

To enable support for `multi_key` properties, the JSON tag `"multi_key_separator"` is required in the `!tabledata` section, as illustrated in the following example:

```
"multi_key_separator": "<key_separator>"
```

The <code>"<i class="varname">&lt;key_separator&gt;</i>"</code> property is used to specify a single character \(the so-called key separator\) which is used to separate the key into a fixed number of subkeys, according to the columns specified in the `"column_mappings"` section. The "*<key\_separator\>*" **cannot** be one of the following characters: ‘=’ \(equals\), ‘:’ \(colon\), ‘\#’ \(hash\), ‘!’ \(exclamation mark\), ‘ ‘ \(space\). Note that you cannot escape the "*<key\_separator\>*" in a subkey definition, and a subkey that has no value assigned is treated as empty and not as NULL.

> ### Tip:  
> The Table Data Properties plug-in can also be used to model `.tags` files.

The following example of a `.properties` file shows the use of multiple keys with the `"multi_key_separator"` property:

> ### Sample Code:  
> `mkp_en_US.properties` 
> 
> ```
> #!tabledata 
> #{ 
> # "target_table"        : "sap::myPropertyTable", 
> # "multi_key_separator" : ".", 
> # "column_mappings"     : { 
> #   "OBJECT"   : { "type" : "constant", "value" : "SKPR07 object" }, 
> #   "LANGUAGE" : { "type" : "function", 
> #                  "name" : "extractLanguageCodeFromFileName", 
> #                  "parameters": { "file_name": "mkp" } 
> #                }, 
> #   "KEY1" : 1, 
> #   "KEY2" : 2, 
> #   "KEY3" : 3, 
> #   "VALUE" : 4 
> #} 
> #} 
> 
> #!tabledata 
> # 
> #<metadata> 
> # <key>.<key2>.<key3>=<value> 
> # XCOL, 120 
> .key2_2.key3_3=key1 is missing 
> # XCOL, 120 
> key_1.key2_2.key3_3=OK 
> # XCOL, 120 
> key_1..key3_3=key2 is missing 
> # XCOL, 120 
> key_1.key2_2.=key3 is missing 
> ```



<a name="loio35c4dd829d2046f29fc741505302f74d__section_bbg_j45_fz"/>

## Plug-in Configuration

In the configuration file for the HDI container \(`.hdiconfig`\), the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig`
> 
> ```
> 
> "hdbtabledata" : {
>   "plugin_name" : "com.sap.hana.di.tabledata"
> }, 
> "csv" : { 
>   "plugin_name" : "com.sap.hana.di.tabledata.source"
> }
> ```

To enable the import of data from `.properties` files, the plug-in configuration should look like the following example:

> ### Code Syntax:  
> `.hdiconfig` for `tabledata.properties`
> 
> ```
> 
> "hdbtabledata" : {
>   "plugin_name" : "com.sap.hana.di.tabledata.properties"
> }, 
> "csv" : { 
>   "plugin_name" : "com.sap.hana.di.tabledata.properties" 
> }
> ```

**Related Information**  


[SAP HDI Artifact Types and Build Plug-ins Reference](sap-hdi-artifact-types-and-build-plug-ins-reference-9789224.md "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.")

[SAP HANA Cloud JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/cloud/en-US)

