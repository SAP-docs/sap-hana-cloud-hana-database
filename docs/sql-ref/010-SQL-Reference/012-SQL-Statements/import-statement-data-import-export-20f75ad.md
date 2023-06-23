<!-- loio20f75ade751910148492a90e5e375b8f -->

# IMPORT Statement \(Data Import Export\)

Imports catalog objects.



<a name="loio20f75ade751910148492a90e5e375b8f__sql_import_1sql_import_syntax"/>

## Syntax

```
IMPORT <import_object_name_list> 
 [ HAVING <object_condition> ] [ AS <import_format> ]
  FROM <storage_path>
 [ WITH <import_option_list> ] 
 [ AT [ LOCATION ] <indexserver_host_port> ]
 [ IGNORE NUMA NODE ]
```



<a name="loio20f75ade751910148492a90e5e375b8f__sql_import_1sql_import_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<import\_object\_name\_list\>*

</b></dt>
<dd>

Specifies the list of objects to be imported. The ALL and \* options import all objects from a specified schema.

```
<import_object_name_list> ::= 
 <import_object_name>[, <import_object_name>[,...] ]
 | { ALL | * }
```


<dl>
<dt><b>

*<import\_object\_name\>*

</b></dt>
<dd>

Specifies objects to import data from. Specify *<schema\_name\>*."\*" to select all objects within a schema for import. Specify ALL \(without *<schema\_name\>*\) to select all objects from all schemas in the system for export. *<schema\_name\>*,"\*" is not supported with the HAVING clause.

```
<import_object_name> ::= [ <schema_name>.]{<identifier> | "*" | ALL} 
```



</dd>
</dl>

If you use SAP\_TIMEZONE\_DATASET as the *<format-option\>* for the AS clause, then you can only specify \* or ALL for *<import\_object\_name\_list\>*.



</dd><dt><b>

HAVING

</b></dt>
<dd>

Imports a subset of data from a specified object type.

```
HAVING <object_condition>
```

The HAVING clause cannot be used with *<schema\>*."\*".

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
<expression>> ::= <identifier> | <type_name> | <expression>
<type_name> ::= TABLE | VIEW | PROCEDURE | FUNCTION | LIBRARY | SEQUENCE 
     | SYNONYM | TASK | GRAPH WORKSPACE | EPMMODEL | EPMQUERYSOURCE | DATA STATISTICS 
     | ANALYTIC_PRIVILEGE | 
```



</dd><dt><b>

AS *<import\_format\>*

</b></dt>
<dd>

Specifies the file type of the input source. CSV, PARQUET, and BINARY are automatically detected if they are not specified.

```
<import_format> ::= { CSV | PARQUET | BINARY [ <binary_type> ] }

<binary_type> ::= {DATA | RAW}
```

If *<binary\_type\>* is not specified, then RAW \(default\) is used.



</dd><dt><b>

FROM *<storage\_path\>*

</b></dt>
<dd>

Specifies the cloud platform for the import.

```
<storage_path> ::=
   { <azure_path> 
   | <amazon_path>
   | <google_path>
   | <hdlfs_path> }
```


<dl>
<dt><b>

*<azure\_path\>*

</b></dt>
<dd>

Specifies the location for the Azure import file.

```
<azure_path> ::= 
'azure://[<azure_credentials>]<azure_container_name>/<azure_object_id>'
```


<dl>
<dt><b>

*<azure\_credentials\>*

</b></dt>
<dd>

Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported when using the WITH CREDENTIAL parameter.

```
<azure_credentials> ::= 
<azure_storage_account_name>:<SAS-token>@
```



</dd><dt><b>

*<azure\_container\_name\>*

</b></dt>
<dd>

Specifies the Azure credentials to access storage.



</dd><dt><b>

*<azure\_object\_id\>*

</b></dt>
<dd>

Specifies a path within the Azure storage.



</dd>
</dl>



</dd><dt><b>

*<amazon\_path\>*

</b></dt>
<dd>

Specifies the location for the Amazon \(AWS\) import file.

```
<amazon_path> ::= 
's3-<amazon_region>://[<amazon_credentials>]<amazon_bucket_name>/<amazon_object_id>'
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

Specifies the credential key pair for API access from the AWS IAM Management Console. This is not the AWS account. Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported with the WITH CREDENTIAL parameter.

```
<amazon_credentials> ::= 
<amazon_access_key>:<amazon_secret_key>@
```



</dd><dt><b>

*<amazon\_bucket\_name\>*

</b></dt>
<dd>

Specifies the name assigned to the bucket when it was created.



</dd><dt><b>

*<amazon\_object\_id\>*

</b></dt>
<dd>

Specifies a path within the named bucket.



</dd>
</dl>



</dd><dt><b>

*<google\_path\>*

</b></dt>
<dd>

Specifies the location for the Google Cloud storage import file.

```
<google_path> ::=
'gs://[<google_credentials>]<google_bucket_name>/<google_object_id>'
```


<dl>
<dt><b>

*<google\_credentials\>*

</b></dt>
<dd>

Specifies the credential key pair for access from the Google IAM Management Console. This is not the Google Cloud account. Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported with the WITH CREDENTIAL parameter.

```
<google_credentials> ::=
<google_service_account>:<google_private_key>@
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

**Prerequisites:**

-   Data lake Files file container
-   Client certificate and private key pair, registered in the data lake Files container and the root certificate
-   Data lake Files SSL Certificate


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

Specifies a path or file name within the data lake Files container. For example, `hdlfs://example-file-container.files.hdl.hc-XXX.XXX.hanacloud.ondemand.com/directory/sample.dat`



</dd>
</dl>



</dd>
</dl>



</dd><dt><b>

WITH *<import\_option\_list\>*

</b></dt>
<dd>

Specifies a list of import options.

```
<import_option_list> ::= <import_option>[, <import_option>[,...] ]

<import_option> ::=
 { REPLACE 
 | CATALOG ONLY 
 | DATA ONLY 
 | NO DEPENDENCIES
 | DEPENDENCIES <object_condition>
 | THREADS <number_of_threads> 
 | RENAME SCHEMA <rename_schema_list> 
 | FAIL ON INVALID DATA 
 | IGNORE EXISTING
 | PERSISTENT MEMORY
 | STATISTICS ONLY
 | NO STATISTICS
 | RENAME REMOTE OBJECT
 | CREDENTIAL '<purpose_def> }
```


<dl>
<dt><b>

REPLACE

</b></dt>
<dd>

Defines the behavior if the import data already exists in the database. When REPLACE is specified, if a table defined in the import data currently exists in the database, then it is dropped and recreated before the data is imported. If the REPLACE option is not specified, then an error is thrown if an existing database table is defined in the import data.



</dd><dt><b>

CATALOG ONLY

</b></dt>
<dd>

Imports only the database catalog.

This option interacts with the STATISTICS ONLY and NO STATISTICS options.



</dd><dt><b>

DATA ONLY

</b></dt>
<dd>

Specifies that only the data in the import file should be imported, without updating or changing the metadata. This option is only valid when the specified target object has its own data, such as a table or a data statistics \(as opposed to procedures and views, whose data is materialized from other objects at runtime\). The target objects must exist in the database and their definition must match that of the data being imported.

When specifying <code>IMPORT <i class="varname">&lt;schema_name&gt;</i>."*"...</code> and `IMPORT ALL...` with DATA ONLY, other objects that do not have records are ignored.

For BINARY data, the existing table data is overwritten with the imported data. For CSV data without the REPLACE option, the import data is appended to the existing table data.

This option interacts with the STATISTICS ONLY and NO STATISTICS option and is not supported for virtual tables.



</dd><dt><b>

NO DEPENDENCIES

</b></dt>
<dd>

Specifies to not import the underlying dependencies of an import object.



</dd><dt><b>

DEPENDENCIES

</b></dt>
<dd>

Specifies the underlying dependencies of an object to import.

```
DEPENDENCIES <object_condition>
```

For the types of conditions you can specify, see *<condition\_list\>*.



</dd><dt><b>

THREADS *<number\_of\_threads\>* 

</b></dt>
<dd>

Specifies how many objects are imported in parallel; the default is 1.

```
<number_of_threads> ::= <unsigned_integer>
```

Increasing the number of threads reduces import time, but can also negatively affect database system performance. Consider these items when you use this parameter:

-   When importing a single table, THREADS has no effect.

-   When importing a view or procedure, two or more threads should be used, up to the number of dependent objects.

-   When importing a schema, consider using more than 10 threads. With a maximum being the number of CPU cores in the system.

-   When importing a whole BW/ERP system database with tens of thousands of tables by using the ALL keyword, a large number of threads can be used \(up to 256\).




</dd><dt><b>

RENAME SCHEMA *<rename\_schema\_list\>*

</b></dt>
<dd>

Specifies whether to rename the object's schema during the import.

```
<rename_schema_list> ::= <rename_schema_token>[, <rename_schema_token>[,...] ]

<rename_schema_token> ::= <source_schema> TO <target_schema>
```

You cannot specify the same schema as both *<source\_schema\>* and *<target\_schema\>* in the same or a different *<rename\_schema\_token\>*.



</dd><dt><b>

FAIL ON INVALID DATA

</b></dt>
<dd>

Fails the import operation if not all data is imported successfully.



</dd><dt><b>

IGNORE EXISTING

</b></dt>
<dd>

Does not import objects that already exist in the database. The IGNORE EXISTING option is ignored if it is used in combination with REPLACE.



</dd><dt><b>

PERSISTENT MEMORY

</b></dt>
<dd>

Imports persistent memory data files from exported data into persistent memory. If no persistent memory data files are found, then this clause is ignored. If this option is specified and persistent memory is not configured for the database, then the IMPORT statement fails.



</dd><dt><b>

STATISTICS ONLY

</b></dt>
<dd>

Data statistics objects are imported by default, along with the objects they reference in *<import\_object\_name\_list\>* \(for example, tables\). When you specify STATISTICS ONLY, the metadata and data for non-statistics objects in *<import\_object\_name\_list\>* are excluded from the import.

If you specify STATISTICS ONLY without DATA ONLY or CATALOG ONLY, then the data and metadata for data statistics objects are imported.

If you specify STATISTICS ONLY and DATA ONLY, then only the data for the data statistics objects is imported.

If you specify STATISTICS ONLY and CATALOG ONLY, then only the metadata for the data statistics objects is imported.

This option is not supported with the *<file\_type\>* parquet.



</dd><dt><b>

NO STATISTICS

</b></dt>
<dd>

Excludes data statistics objects from the import. Metadata and data for non-statistics objects in *<import\_object\_name\_list\>* are still imported, and they are impacted as normal by whether CATALOG ONLY or DATA ONLY is specified.



</dd><dt><b>

RENAME REMOTE OBJECT

</b></dt>
<dd>

Specify a mapping of the old remote object to new remote object when importing virtual tables into another system.

When importing virtual tables, each virtual table is created by using the same remote source and remote object when it was exported by default. Before importing virtual tables, remote sources and remote objects used by the virtual tables should exist.



</dd><dt><b>

CREDENTIAL *<purpose\_def\>*

</b></dt>
<dd>

Specifies the name of the credential defined in the CREATE CREDENTIAL statement. Since the credentials are defined within the credential, they no longer appear as plain text as part of import statements. The WITH CREDENTIAL clause cannot be specified when *<cloud\_path\>* contains credentials. The WITH CREDENTIAL clause is required for imports to SAP HANA Cloud, Data Lake Files, but is optional for all other cloud platforms.



</dd>
</dl>



</dd><dt><b>

AT LOCATION *<indexserver\_host\_port\>*

</b></dt>
<dd>

Specifies the index server on which tables are created and imported.

```
<indexserver_host_port> ::= '<host_name>:<port_number>'
```

If you specify the hostname and port, then the tables are created and imported at that location.



</dd><dt><b>

IGNORE NUMA NODE

</b></dt>
<dd>

By default, SAP HANA attempts to apply the NUMA node preferences that were set in the source system for the table you are importing. If the number of NUMA nodes on the target system is greater than or equal to the number on the source system, then the NUMA node preferences are applied. If the target system has fewer NUMA nodes, then the NUMA node preferences are ignored.

Specify IGNORE NUMA NODE to override the default behavior and not import NUMA location preferences into the target system.



</dd>
</dl>



<a name="loio20f75ade751910148492a90e5e375b8f__section_opr_ddt_5cb"/>

## Permissions

Requires the following:

-   IMPORT system privilege
-   CREATE SCHEMA privilege if the schema for the import object does not exist
-   CREATE privilege on the schema for each object type to import

    DROP privilege on object to drop if object already exists and WITH REPLACE option is used

    CREATE TEMPORARY TABLE privilege on the current schema

-   CREATE TEMPORARY TABLE privilege on the schema containing the object to export.



<a name="loio20f75ade751910148492a90e5e375b8f__sql_import_1sql_import_description"/>

## Description

The IMPORT statement imports catalog objects \(tables, views, synonyms, sequences, and procedures\) that have previously been exported with the EXPORT statement. To import external data into existing tables, use the IMPORT FROM statement. The IMPORT statement can also import load history data that is stored in `nameserver_history.trc` files and timezone definitions according to SAP note [198411](https://launchpad.support.sap.com/#/notes/198411).

When using CSV format to export/import tables that have columns of type GENERATED ALWAYS AS *<expression\>*, verify that the imported records match what was exported. If there are anomalies:

-   For column tables, switch to exporting/importing as BINARY.

-   For row tables, change the table to be a column table and export/import as BINARY.


Detailed results of the last successful execution of the IMPORT statement are stored in the following session-local temporary table *<current\_schema\>*.\#IMPORT\_RESULT. If IMPORT has not been executed in the current session, then selecting from *<current\_schema\>*.\#IMPORT\_RESULT returns an error. If *<current\_schema\>* of the session is invalid, then IMPORT throws an exception as it cannot create its result table for the *<current\_schema\>*.

**current\_schema.\#IMPORT\_RESULT**


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

The database of the imported object



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

The schema of the imported object



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

The name of the imported object



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

The type of the imported object \(TABLE, VIEW, and so on\)



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

The location \(*<host\>*:*<port\>*\) where the object was imported



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

The import status \(done, skipped, or failed\)



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

The error text in the case of an import failure



</td>
</tr>
</table>



<a name="loio20f75ade751910148492a90e5e375b8f__sql_import_from_1sql_import_from_examples"/>

## Examples

This statement imports from Azure storage, all objects from the exported location.

```
IMPORT ALL FROM 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1' WITH THREADS 4 REPLACE;
```

This example imports, from Amazon storage, all tables from the schema `TESTSCH` by using the REPLACE option and ten execution threads.

```
IMPORT TESTSCH."*" AS CSV FROM 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH REPLACE THREADS 10;
```

This example imports, from Google storage, the schema from table T14, but ignores the NUMA NODE preferences.

```
IMPORT SYSTEM."T14" FROM 'gs://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH REPLACE THREADS 40 IGNORE NUMA NODE;
```

In this example, `MY_SCHEMA` has two tables, `T1` and `T2`, each with column `A`, and two views. V1 selects T1.a from T1 and T2. V2 selects \* from T2. The following syntax imports, from Azure storage, the object type `VIEW` and all object names not equal to `V2`. It also imports its dependency `T1`.

```
IMPORT ALL HAVING schema_name = 'my_schema' AND object_type = 'VIEW' AND object_name != 'V2' 
    FROM 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1' WITH REPLACE DEPENDENCIES object _name = 'T1';
```

This example imports objects from a file in Amazon storage using 4 threads.

```
IMPORT ALL FROM 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1' WITH THREADS 4 REPLACE;
```

**Related Information**  


[SAP HANA Cloud, SAP HANA Database Spatial Reference](https://help.sap.com/viewer/bc9e455fe75541b8a248b4c09b086cf5/2023_2_QRC/en-US/e1c934157bd14021a3b43b5822b2cbe9.html "This guide is the entry point for SAP HANA Spatial capabilities.") :arrow_upper_right:

[EXPORT Statement \(Data Import Export\)](export-statement-data-import-export-20da0be.md "Exports catalog objects.")

[IMPORT FROM Statement \(Data Import Export\)](import-from-statement-data-import-export-20f712e.md "Imports external data into an existing table.")

[IMPORT SCAN Statement \(Data Import Export\)](import-scan-statement-data-import-export-20f79b2.md "Searches the specified path for exported objects.")

[Importing and Exporting Data](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/LATEST/en-US/261937915fa5438ca545b8278b2979b7.html)

[ALTER SYSTEM CANCEL \[WORK IN\] SESSION Statement \(System Management\)](alter-system-cancel-work-in-session-statement-system-management-20d0eb2.md "Cancels the currently executing statement of a session.")

