<!-- loio20da0bec751910148e69c9668ea3ccb8 -->

# EXPORT Statement \(Data Import Export\)

Exports catalog objects.



<a name="loio20da0bec751910148e69c9668ea3ccb8__sql_export_1sql_export_syntax"/>

## Syntax

```
EXPORT <export_object_name_list> 
 [ WHERE <condition> | HAVING <condition_list> ]
 AS <export_format>
 INTO <cloud_provider_path>
 [ WITH <export_option_list> ]
 [ <query_export_specification> ]
```



<a name="loio20da0bec751910148e69c9668ea3ccb8__sql_export_1sql_export_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<export\_object\_name\_list\>*

</b></dt>
<dd>

Specifies a list of objects to export. The ALL and \* options export all objects from a specified schema.

```
<export_object_name_list> ::= 
 <export_object_name>[, <export_object_name> [,...]]
 | { ALL | * }

<export_object_name> ::= [<schema_name>.]{<identifier> | "*" } 
<schema_name> ::= <identifier>
```


<dl>
<dt><b>

*<export\_object\_name\>*

</b></dt>
<dd>

Specifies objects in a schema for export. Specify *<schema\_name\>*."\*" to select all objects within the specified schema for export. Specify ALL \(without *<schema\_name\>*\) to select all objects from all schemas in the system for export. *<schema\_name\>*,"\*" is not supported with the HAVING clause.



</dd>
</dl>



</dd><dt><b>

WHERE *<condition\>*

</b></dt>
<dd>

Exports a subset of table data.

```
WHERE <condition> ::= 
 <condition> OR <condition> 
 | <condition> AND <condition>
 | NOT <condition>
 | ( <condition> )
 | <predicate>

<predicate> ::= 
 <comparison_predicate>
 | <range_predicate>
 | <in_predicate> 
 | <exist_predicate>
 | <like_predicate> 
 | <null_predicate>
 
<comparison_predicate> ::= 
 <expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( { <expression_list> | <subquery> } )
 
<range_predicate> ::= 
 <expression> [ NOT ] BETWEEN <expression> AND <expression>
 
<in_predicate> ::= 
 <expression> [ NOT ] IN ( { <expression_list> | <subquery> } )
 
<exist_predicate> ::= 
 [NOT] EXISTS ( <subquery> )
 
<like_predicate> ::= 
 <expression> [ NOT ] LIKE <expression> [ ESCAPE <expression> ]
 
<null_predicate> ::= 
 <expression> IS [ NOT ] NULL

<expression_list> ::= <expression> [, <expression> [,...] ]
```

The WHERE clause follows, and is associated with, a single table in the EXPORT statement. If at least one table has a WHERE clause specified, then the following restrictions are enforced:

-   Only the CSV format is supported for export

-   The following options are not allowed: CATALOG ONLY, STATISTICS ONLY, and NO DEPENDENCIES


The WHERE clause cannot be used in conjunction with ALL or \*.



</dd><dt><b>

HAVING

</b></dt>
<dd>

Exports a subset of data from a specified object.

```
HAVING <condition_list>
```

The HAVING clause cannot be used in conjunction with *<schema\>*.*<identifier\>* or *<schema\>*."\*".

For the types of conditions you can specify, see *<condition\_list\>*.



</dd><dt><b>

*<condition\_list\>*

</b></dt>
<dd>

Specifies the conditions defined for the HAVING and DEPENDENCIES clauses.

```
<condition_list> ::=
<condition> OR <condition>
| <condition> AND <condition>
| NOT <condition>
| ( <condition> )
| <predicate>

<predicate> ::=
<comparison_predicate>
| <range_predicate>
| <in_predicate>
| <like_predicate>
| <null_predicate>

<comparison_predicate> ::=
<column_expression> { = | != | <> | > | < | >= | <= } [ ANY | SOME | ALL ] ( { <expression_list>  | <subquery> } )

<range_predicate> ::=
<column_expression> [NOT] BETWEEN <expression> AND <expression>

<in_predicate> ::=
<column_expression> [NOT] IN ( { <expression_list> | <subquery> } )

<like_predicate> ::=
<column_expression> [NOT] LIKE <expression> [ ESCAPE <expression> ]

<null_predicate> ::=
<column_expression> IS [NOT] NULL

<expression_list> ::= <expression>[, <expression>[,...] ]

<column_expression> ::= SCHEMA_NAME | OBJECT_NAME | OBJECT_TYPE
<expression>> ::= <identifier> |  | <expression>
<type_name> ::= TABLE | VIEW | PROCEDURE | FUNCTION | LIBRARY | SEQUENCE 
     | SYNONYM | TASK | GRAPH WORKSPACE | EPMMODEL | EPMQUERYSOURCE | DATA STATISTICS 
     | ANALYTIC_PRIVILEGE 
```



</dd><dt><b>

AS *<export\_format\>*

</b></dt>
<dd>

Specifies the format to export the data to. The default value is BINARY.

```
<export_format> ::= CSV | PARQUET | BINARY [ <binary_type> ]

<binary_type> ::= DATA | RAW
```


<table>
<tr>
<th valign="top">

Format Type

</th>
<th valign="top">

Details

</th>
</tr>
<tr>
<td valign="top">

BINARY

</td>
<td valign="top">

Table data is exported in an internal binary format. Exporting in BINARY RAW format is orders of magnitude faster than exporting the same table in CSV format. Only column non-temporary tables can be exported in binary format. Row tables are always exported in CSV format regardless of the format specified. If *<binary\_type\>* is not specified, RAW \(default\) is used. BINARY data is compatible between SAP HANA on-premise and cloud systems.

</td>
</tr>
<tr>
<td valign="top">

CSV

</td>
<td valign="top">

Table data is exported in CSV format. With this export format the exported data can be scrambled. Both column and row tables can be exported in CSV format.

</td>
</tr>
<tr>
<td valign="top">

PARQUET

</td>
<td valign="top">

Table data is exported in PARQUET format.

</td>
</tr>
</table>



</dd><dt><b>

*<cloud\_provider\_path\>*

</b></dt>
<dd>

Specifies the cloud provider path for the export.

```
<cloud_provider_path> ::=
   { <azure_path> 
   | <amazon_path>
   | <google_path>
   | <hdlfs_path> }
```



</dd>
<dd>


<dl>
<dt><b>

*<azure\_path\>*

</b></dt>
<dd>

Specifies the location for the Azure export file.

```
<azure_path> ::= 
'azure://[<azure_credentials>@]<azure_container_name>/<azure_object_id>
```


<dl>
<dt><b>

*<azure\_credentials\>*

</b></dt>
<dd>

Required when not using the CREDENTIAL clause.

```
<azure_credentials> ::= 
<azure_storage_account_name>:<SAS-token>
```



</dd><dt><b>

*<azure\_container\_name\>*

</b></dt>
<dd>

Specifies the name of the Azure container to access storage.



</dd><dt><b>

*<azure\_object\_id\>*

</b></dt>
<dd>

Specifies a path to the object within the Azure storage.



</dd>
</dl>



</dd><dt><b>

*<amazon\_path\>*

</b></dt>
<dd>

Specifies the location for the Amazon \(AWS\) export file.

```
<amazon_path> ::= 
's3-<amazon_region>://[<amazon_credentials>@]<amazon_bucket_name>/<amazon_object_id>
```


<dl>
<dt><b>

*<amazon\_region\>*

</b></dt>
<dd>

Specifies the geographical region the bucket is located in. Refer to [Regions and Availability Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html).



</dd><dt><b>

*<amazon\_credentials\>*

</b></dt>
<dd>

Not supported with the CREDENTIAL clause. Specifies the credential key pair for API access from the AWS IAM Management Console. This is not the AWS account.

```
<amazon_credentials> ::= 
'<amazon_access_key>:<amazon_secret_key>
```



</dd><dt><b>

*<amazon\_bucket\_name\>*

</b></dt>
<dd>

Specifies the name assigned to the Amazon storage bucket when it was created.



</dd><dt><b>

*<amazon\_object\_id\>*

</b></dt>
<dd>

Specifies a path to the object within the named bucket.



</dd>
</dl>



</dd><dt><b>

*<google\_path\>*

</b></dt>
<dd>

Specifies the location for the Google Cloud storage export file.

```
<google_path> ::=
'gs://[<google_credentials>@]<google_bucket_name>/<google_object_id>'
```


<dl>
<dt><b>

*<google\_credentials\>*

</b></dt>
<dd>

Not supported with the CREDENTIAL clause. Specifies the credential key pair for access from the Google IAM Management Console. This is not the Google Cloud account.

```
<google_credentials> ::=
<google_service_account>:<google_private_key>
```



</dd><dt><b>

*<google\_bucket\_name\>*

</b></dt>
<dd>

Specifies the name assigned to the Google Cloud storage bucket when it was created.



</dd><dt><b>

*<google\_object\_id\>*

</b></dt>
<dd>

Specifies a path to the object within the named bucket.



</dd>
</dl>



</dd><dt><b>

*<hdlfs\_path\>*

</b></dt>
<dd>

Specifies the location for the SAP HANA Cloud, Data Lake Files \(HDLFS\).

```
<hdlfs_path> ::=
hdlfs://<hdlfs_endpoint>/<hdlfs_object_id>

```


<dl>
<dt><b>

*<hdlfs\_endpoint\>*

</b></dt>
<dd>

Specifies the server address given from data lake Files. It consists of the data lake Files container id and the landscape.



</dd><dt><b>

*<hdlfs\_object\_id\>*

</b></dt>
<dd>

Specifies a path or file name within the data lake Files container.



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

WITH *<export\_option\_list\>*

</b></dt>
<dd>

Specifies a list of export options.

```
WITH <export_option_list> ::=
  <export_option>[, <export_option>[,...] ]

<export_option> ::= 
 { REPLACE 
 | CATALOG ONLY 
 | NO DEPENDENCIES 
 | DEPENDENCIES <condition_list>
 | THREADS <number_of_threads>
 | [ SYSTEM | ALL ] STATISTICS [ COLUMNS <column_list> ] [ TYPE <dstat_type> ] [ ONLY ]
 | NO STATISTICS
 | PERSISTENT MEMORY
 | CREDENTIAL '<purpose_def>' }
```


<dl>
<dt><b>

REPLACE

</b></dt>
<dd>

Defines the behavior if the export data already exists in the specified directory. If REPLACE is not specified, then an error is returned if previously exported data exists in the specified export directory.



</dd><dt><b>

CATALOG ONLY

</b></dt>
<dd>

Specifies to export only the database catalog.

This option interacts with the STATISTICS ONLY and NO STATISTICS options.



</dd><dt><b>

NO DEPENDENCIES

</b></dt>
<dd>

Specifies to not export the underlying dependencies of an export object.



</dd><dt><b>

DEPENDENCIES

</b></dt>
<dd>

Specifies the underlying dependencies of an object to export.

```
DEPENDENCIES <condition_list>
```

For the types of conditions you can specify, see [*<condition\_list\>*](export-statement-data-import-export-20da0be.md#loio20da0bec751910148e69c9668ea3ccb8__condition_list).

DEPENDENCIES is not supported with the WHERE clause.



</dd><dt><b>

THREADS *<number\_of\_threads\>*

</b></dt>
<dd>

Specifies the number of process threads to be used for concurrent export processing.

```
THREADS <number_of_threads>

<number_of_threads> ::= <unsigned_integer>
```

The THREADS parameter specifies how many objects are exported in parallel; the default is 1. Increasing the number of threads reduces export time, but can also negatively affect database system performance. Consider the following items when you use this parameter:

-   When exporting a single table. THREADS has no effect.

-   When exporting a view or procedure, two or more threads should be used, up to the number of dependent objects.

-   When exporting a whole schema, consider using more than 10 threads, with a maximum being the number of CPU cores in the system.

-   When exporting a whole BW/ERP system database with tens of thousands of tables by using the ALL keyword, a large number of threads can be used \(up to 256\).




</dd><dt><b>

PERSISTENT MEMORY

</b></dt>
<dd>

Exports the persistent memory data as files for columns that are actively using persistent memory. If this option is specified and persistent memory is not configured for the database, then the EXPORT statement fails.



</dd><dt><b>

\[ SYSTEM | ALL \] STATISTICS \[ COLUMNS *<column\_list\>* \] \[ TYPE *<dstat\_type\>* \] \[ ONLY \]

</b></dt>
<dd>

User-defined data statistics objects are exported by default, along with the objects they reference in *<export\_object\_name\_list\>* \(for example, tables\).

```
[ SYSTEM | ALL ] STATISTICS [ COLUMNS <column_list> ] [ TYPE <dstat_type> ] [ ONLY ]

<column_list> ::= <col_name1>[, <col_name2>[,...] ]
<col_name> ::= <identifier>
<dstat_type> ::= { SIMPLE | TOPK | HISTOGRAM | SKETCH | SAMPLE | RECORD COUNT }
```

SYSTEM statistics are only available on column and row tables.

If you specify SYSTEM, then system statistics that were automatically generated for the specified data sources are exported. If no system statistics are available for a data source, then no data statistics objects are exported. If you specify ALL, then both system- and user-defined data statistics are exported, where available. If both system- and user-defined statistics are available on a data source, then only the user-defined statistics are exported. If neither SYSTEM nor ALL is specified, then only user-defined data statistics are exported. This is the default behavior in the absence of the STATISTICS clause.

If *<column\_list\>* is specified, then any data statistics objects that reference all or some of the specified columns, but none of the other columns are exported. When you export SYSTEM data statistics, *<column\_list\>* is required when the statistics type SAMPLE is specified. If *<column\_list\>* is not specified and SYSTEM statistics are requested, then TOPK and SIMPLE data statistics for each column of the specified data object are exported, if available. If *<column\_list\>* is specified, then only a single data object can be specified. If *<column\_list\>* is specified and SYSTEM statistics are requested, then data statistics of type SIMPLE, TOPK, and SAMPLE are exported. SIMPLE and TOPK are generated for every eligible column on the list, while a single SAMPLE covering all eligible columns from the specified list is generated.

*<dstat\_type\>* filters exported data statistics to only the specified type. For SYSTEM data statistics, supported types are SIMPLE, TOPK, and SAMPLE.

If you specify STATISTICS ONLY without CATALOG ONLY, then both the data and metadata for user-defined data statistics objects are exported, as well as the metadata for the objects in *<export\_object\_name\_list\>*.

If you specify STATISTICS ONLY and CATALOG ONLY, then only the metadata for the data statistics objects and the objects in *<export\_object\_name\_list\>* are exported; no data is exported.



</dd><dt><b>

NO STATISTICS

</b></dt>
<dd>

Excludes both system- and user-defined data statistics objects from the export. Metadata and data for the objects in *<export\_object\_name\_list\>* are still exported, and they are impacted as normal by whether CATALOG ONLY is specified.



</dd><dt><b>

CREDENTIAL *<purpose\_def\>*

</b></dt>
<dd>

Specifies the name of the credential defined in the CREATE CREDENTIAL statement. Since the credentials are defined within the credential, they no longer appear as plain text as part of export statements. The CREDENTIAL clause cannot be specified when *<cloud\_provider\_path\>* contains credentials. The CREDENTIAL clause is required for exports from SAP HANA Cloud, Data Lake Files, but is optional for all other cloud storage locations.



</dd>
</dl>



</dd><dt><b>

*<query\_export\_specification\>*

</b></dt>
<dd>

Specifies a query to use for the export.

```
<query_export_specification> ::= 
 [ ON <sqlscript_location_list> ] FOR <procedure_call_statement>
```

For information on query exports, see the *SAP HANA Cloud, SAP HANA Database SQLScript Reference*.



</dd>
</dl>



<a name="loio20da0bec751910148e69c9668ea3ccb8__section_fvd_zlc_ycb"/>

## Permissions

Requires the following:

-   EXPORT system privilege
-   Privilege to access the object to export:
    -   SELECT object privilege on the TABLE, VIEW, SEQUENCE, or GRAPH WORKSPACE
    -   EXEUCTE privilege on PROCEDURE or FUNCTION

-   CREATE TEMPORARY TABLE privilege on the current schema



<a name="loio20da0bec751910148e69c9668ea3ccb8__sql_export_1sql_export_description"/>

## Description

For information on creating the Amazon S3 bucket, which is required to use EXPORT statement, see *Importing and Exporting with Amazon S3* in the *SAP HANA Cloud, SAP HANA Database Administration Guide*.

The EXPORT command exports tables, views, column views, synonyms, data statistics objects, sequences, procedures, or column encryption keys. It does not support parameterized views.

Data stored in "no logging" tables can only be exported in CSV format. For global temporary tables, only the table catalog can be exported. The export of local temporary tables is not supported. When the EXPORT statement references virtual tables, remote table data is not included in the export.

Detailed results of the last successful execution of the EXPORT statement are stored in the session-local temporary table *<current\_schema\>*.\#EXPORT\_RESULT. If EXPORT has not been executed in the current session, then selecting from *<current\_schema\>*.\#EXPORT\_RESULT returns an error. If *<current\_schema\>* of the session is invalid, then EXPORT throws an exception as it cannot create its result table in *<current\_schema\>*.

**current\_schema.\#EXPORT\_RESULT**


<table>
<tr>
<th valign="top">

Column Name

</th>
<th valign="top">

Data type

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

DATABASE\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The database of the exported object

</td>
</tr>
<tr>
<td valign="top">

SCHEMA\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The schema of the exported object

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

The name of the exported object

</td>
</tr>
<tr>
<td valign="top">

OBJECT\_TYPE

</td>
<td valign="top">

VARCHAR\(32\)

</td>
<td valign="top">

The type of the exported object \(TABLE, VIEW, and so on\)

</td>
</tr>
<tr>
<td valign="top">

LOCATION

</td>
<td valign="top">

VARCHAR\(75\)

</td>
<td valign="top">

The location \(*<host\>*:*<port\>*\) where the object was exported

</td>
</tr>
<tr>
<td valign="top">

STATUS

</td>
<td valign="top">

VARCHAR\(16\)

</td>
<td valign="top">

The export status \(done, skipped, failed\)

</td>
</tr>
<tr>
<td valign="top">

ERROR

</td>
<td valign="top">

VARCHAR\(512\)

</td>
<td valign="top">

The error text if there is an export failure

</td>
</tr>
</table>



<a name="loio20da0bec751910148e69c9668ea3ccb8__sql_import_from_1sql_import_from_examples"/>

## Examples

This statement exports all objects of the schema TPCH1 to the Azure bucket.

```
EXPORT TPCH1."*" AS CSV INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH THREADS 4 REPLACE;
```

This example exports all the database objects in schema A and B, replacing any existing export that may be present in the `tmp` directory.

```
 EXPORT a."*", b."*" AS CSV INTO 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH REPLACE;
```

The following two examples show how to filter the data exported from tables by using the WHERE clause:

```
EXPORT SYSTEM.TBL_A WHERE COL_A > 5 INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1' WITH REPLACE;
EXPORT SYSTEM.TBL_A WHERE COL_B LIKE '%ch%' AND MOD(COL_C, 2) = 0, SYSTEM.TBL_B AS CSV INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1' WITH REPLACE;
```

In this example, `my_schema` has two tables, `T1` and `T2`, each with column `a`, and two views. V1 selects T1.a from T1 and T2. V2 selects \* from T2. The following syntax exports the object type `VIEW` and all object names not equal to `V2`. It also exports its dependency `T1`.

```
EXPORT ALL HAVING schema_name = 'my_schema' AND object_type = 'VIEW' AND object_name != 'V2' AS CSV 
    INTO 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH REPLACE DEPENDENCIES object _name = 'T1';
```

This example exports all objects in the schema IMX\_DEMO into Azure storage.

```
EXPORT IMEX_DEMO."*" INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/IMEX_DEMO' WITH THREADS 4 REPLACE;
```

**Related Information**  


[Security Recommendations for SAP HANA Database](https://help.sap.com/viewer/a1317de16a1e41a6b0ff81849d80713c/2023_4_QRC/en-US/bc54d87673bc484faadb8330f43edc40.html "Recommendations to help you operate and configure the SAP HANA database securely") :arrow_upper_right:

[EXPORT INTO Statement \(Data Import Export\)](export-into-statement-data-import-export-6a6f59b.md "Exports a table or view into a single-file, multi-file, or directory.")

[IMPORT Statement \(Data Import Export\)](import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

[IMPORT FROM Statement \(Data Import Export\)](import-from-statement-data-import-export-20f712e.md "Imports external data into an existing table.")

[IMPORT SCAN Statement \(Data Import Export\)](import-scan-statement-data-import-export-20f79b2.md "Searches the specified path for exported objects.")

[Importing and Exporting Data](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/LATEST/en-US/261937915fa5438ca545b8278b2979b7.html)

[SAP Note 2907201](https://me.sap.com/notes/2907201 "Importing Data From Compressed Format Throws Error: &quot;Archive is incomplete&quot;")

[CREATE CREDENTIAL Statement \(Access Control\)](create-credential-statement-access-control-20d3f46.md "Creates a component-specific or application-specific credential.")

