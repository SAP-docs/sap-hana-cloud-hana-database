<!-- loio20f712e175191014907393741fadcb97 -->

# IMPORT FROM Statement \(Data Import Export\)

Imports external data into an existing table.



<a name="loio20f712e175191014907393741fadcb97__sql_import_from_1sql_import_from_syntax"/>

## Syntax

```
IMPORT FROM [ <file_type> ] [ IN <directory_type> ] { <cloud_provider_path> } 
 [ INTO <database_object_name> ] 
 [ WITH <import_from_option_list> ]
```



<a name="loio20f712e175191014907393741fadcb97__sql_import_from_1sql_import_from_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

*<file\_type\>*

</b></dt>
<dd>

Specifies the type of file being imported from.

```
<file_type> ::= 
   {CSV FILE | CONTROL FILE | PARQUET FILE | JSON FILE }
```

When *<file\_type\>* is CSV, you can also import from a GZIP \(.gz\) file containing the CSV data.

When importing data statistics objects, you can only import from a control file.

In the IMPORT FROM command, if the *<file\_type\>* is not explicitly specified, it will default to CONTROL FILE. This means that the system will treat the input file as a control file in the absence of a specified file type.



</dd><dt><b>

*<directory\_type\>*

</b></dt>
<dd>

Specifies the directory format. When *<directory\_type\>* is set, specify a directory in *<cloud\_provider\_path\>*.

```
<directory_type> ::= { HIVE PARTITION | DELTA LAKE }
```

HIVE PARTITION only supports default encodings. NULL value encoding = \_\_HIVE\_DEFAULT\_PARTITION\_\_.



</dd><dt><b>

*<cloud\_provider\_path\>*

</b></dt>
<dd>

Specifies the cloud provider for the import.

```
<cloud_provider_path> ::=
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
'azure://[<azure_credentials_path>]<azure_container_name>/<azure_object_id>'
```


<dl>
<dt><b>

*<azure\_credentials\>*

</b></dt>
<dd>

Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported when using the CREDENTIAL clause.

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

Specifies the credential key pair for API access from the AWS IAM Management Console. This is not the AWS account. Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported with the CREDENTIAL clause.

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

Specifies the credential key pair for access from the Google IAM Management Console. This is not the Google Cloud account. Credentials are required when accessing private storage, but are not applicable when accessing publicly readable cloud storage. Not supported with the CREDENTIAL clause.

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



</dd>
</dl>


<dl>
<dt><b>

*<database\_object\_name\>*

</b></dt>
<dd>

Specifies the target table name into which the imported data will be imported.

```
<database_object_name> ::= 
 [<schema_name>.]<table_name>

<schema_name> ::= <unicode_name>
<table_name> ::= <identifier>
```



</dd><dt><b>

*<import\_from\_option\_list\>*

</b></dt>
<dd>

Specifies a list of options that control import behavior.

```
WITH <import_from_option_list>

<import_from_option_list> ::= <import_from_option>[, <import_from_option> [,…] ]

<import_from_option> ::=
 { THREADS <number_of_threads>
 | BATCH <number_of_records_of_each_commit>
 | SKIP FIRST <number_of_rows_to_skip> ROW
 | COLUMN LIST IN FIRST ROW 
 | COLUMN LIST ( <column_name_list> ) 
 | RECORD DELIMITED BY <string_for_record_delimiter>
 | FIELD DELIMITED BY <string_for_field_delimiter>
 | OPTIONALLY ENCLOSED BY <character_for_optional_enclosure>
 | ESCAPE <escape_character>
 | DATE FORMAT <string_for_date_format>
 | TIME FORMAT <string_for_time_format>
 | TIMESTAMP FORMAT <string_for_timestamp_format>
 | FAIL ON INVALID DATA
 | CREDENTIAL '<purpose_def> }
```


<dl>
<dt><b>

THREADS *<number\_of\_threads\>*

</b></dt>
<dd>

Specifies the number of threads that can be used for concurrent import. The default value is 1 and the maximum allowed value is 256.

```
THREADS <number_of_threads>

<number_of_threads> ::= <unsigned_integer>
```



</dd><dt><b>

BATCH *<number\_of\_records\_of\_each\_commit\>*

</b></dt>
<dd>

Specifies the number of records to be inserted in each commit.

```
BATCH <number_of_records_of_each_commit>

<number_of_records_of_each_commit> ::= <unsigned_integer>
```

This option is not supported with the *<file\_type\>* parquet.

THREADS and BATCH provide high loading performance by enabling parallel loading and also by committing many records at once. In general, for column tables, a good setting to use is 10 parallel loading threads, with a commit frequency of 10,000 records or greater.



</dd><dt><b>

SKIP FIRST *<number\_of\_rows\_to\_skip\>* ROW

</b></dt>
<dd>

```
SKIP FIRST <number_of_rows_to_skip> ROW

Skips the specified number of rows in the import
                              file.<number_of_rows_to_skip> ::= <unsigned_integer>
```

This option is not supported with the *<file\_type\>* parquet or JSON.



</dd><dt><b>

COLUMN LIST IN FIRST ROW

</b></dt>
<dd>

Indicates that the column list is stored in the first row of the CSV import file.

This option is not supported with the *<file\_type\>* parquet or JSON.



</dd><dt><b>

COLUMN LIST

</b></dt>
<dd>

Specifies the list of table columns for the data being imported.

```
COLUMN LIST (<column_name_list>)

<column_name_list> ::= <column_name> [, <column_name>...]

<column_name> ::= <identifier>
```

This option is not supported with the *<file\_type\>* JSON.

The name list has one or more column names. The ordering of the column names has to match the order of the column data in the CSV file from the leftmost column. The column names must exist in the target table, and the data types must match those in the CSV file. Unmatched columns in the target table have NULL values. If the number of column names is larger than the number of columns in the CSV file, unmatched columns have NULL values.



</dd><dt><b>

RECORD DELIMITED BY *<string\_for\_record\_delimiter\>* and FIELD DELIMITED BY *<string\_for\_field\_delimiter\>*

</b></dt>
<dd>

This option is not supported with the *<file\_type\>* parquet or JSON.

Skips the specified number of rows in the importSpecifies the record and field delimiters used in the CSV file, respectively. Supported delimiters are as follows:

-   \\Uhhhhhhhh: 8 hexadecimal digits

-   \\uhhhh: 4 hexadecimal digits

-   \\xhh…: 1 or more hexadecimal digits

-   \\nnn: one, two, or three octal numbers


Special characters such as '\\036' or '\\u0007' are useful when importing datafiles that have special characters like '\\u0001' or chr\(1\). These values are then converted to non-escaped values and used as the delimiter.



</dd><dt><b>

OPTIONALLY ENCLOSED BY *<character\_for\_optional\_enclosure\>*

</b></dt>
<dd>

Specifies the optional enclosure character that delimits field data.

```
OPTIONALLY ENCLOSED BY <character_for_optional_enclosure>

<character_for_optional_enclosure> ::= <character_literal>
```

This option is not supported with the *<file\_type\>* parquet or JSON.



</dd><dt><b>

ESCAPE *<escape\_character\>*

</b></dt>
<dd>

Specifies the escape character used in the import data.

```
<escape_character> ::= <character_literal>
```

This option is not supported with the *<file\_type\>* parquet or JSON.



</dd><dt><b>

DATE FORMAT *<string\_for\_date\_format\>*

</b></dt>
<dd>

Specifies the format that date strings are encoded with in the import data.

```
DATE FORMAT <string_for_date_format>

<string_for_date_format> ::= <string_literal>
```

This option is not supported with the *<file\_type\>* parquet or JSON.

Values can include:

-   Y: year
-   MM: month
-   MON: name of month
-   DD: day

For example:

-   'YYYYMMDD' = 20120520
-   'YYYY-MM-DD' = 2012-05-20
-   'YYYY-MON-DD' : 2012-MAY-20



</dd><dt><b>

TIME FORMAT *<string\_for\_time\_format\>*

</b></dt>
<dd>

Specifies the format that time strings are encoded with in the import data.

```
TIME FORMAT <string_for_time_format>

<string_for_time_format> ::= <string_literal>
```

This option is not supported with the *<file\_type\>* parquet or JSON.

Values can include:

-   HH24: hour
-   MI: minute
-   SS: second

For example:

-   'HH24MISS': 143025
-   'HH24:MI:SS': 14:30:25



</dd><dt><b>

TIMESTAMP FORMAT *<string\_for\_timestamp\_format\>*

</b></dt>
<dd>

```
TIMESTAMP FORMAT <string_for_timestamp_format>

<string_for_timestamp_format> ::= <string_literal>
```

This option is not supported with the *<file\_type\>* parquet or JSON.



</dd><dt><b>

ERROR LOG

</b></dt>
<dd>

The default location of the log file is the same location as the file being imported.

This option is not supported with the *<file\_type\>* JSON.



</dd><dt><b>

FAIL ON INVALID DATA

</b></dt>
<dd>

Specifies that the IMPORT FROM command fails unless all the entries import successfully. This option is optional for all *<file\_type\>* except JSON, for which it is required.



</dd><dt><b>

CREDENTIAL *<purpose\_def\>*

</b></dt>
<dd>

This option is not supported with the *<file\_type\>* JSON.

Specifies the name of the credential defined in the CREATE CREDENTIAL statement. Since the credentials are defined within the credential, they no longer appear as plain text as part of import statements. The CREDENTIAL clause cannot be specified when *<cloud\_provider\_path\>* contains credentials. The CREDENTIAL clause is required for imports from SAP HANA Cloud, Data Lake Files, but is optional for all other cloud platforms.



</dd>
</dl>



</dd>
</dl>



<a name="loio20f712e175191014907393741fadcb97__sql_import_from_1sql_import_from_description"/>

## Description

Use the IMPORT FROM statement to import data into database objects, such as tables from CSV files.

To import catalog objects \(tables, views, and so on\) that have been exported with the EXPORT statement, use the IMPORT statement instead.

All *<string\_literals\>* in the *<import\_from\_option\>* support UTF-8 except surrogate-pair encoding.



<a name="loio20f712e175191014907393741fadcb97__section_opr_ddt_5cb"/>

## Permissions

Requires:

-   IMPORT system privilege
-   INSERT privilege on the object that is being imported into.



<a name="loio20f712e175191014907393741fadcb97__sql_import_from_1sql_import_from_examples"/>

## Examples

This statement imports data in a CSV file in an Azure bucket into table TPCH1.LINEITEM. The CSV file is delimited by a comma and the import uses 4 threads.

```
IMPORT FROM CSV FILE 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1_lineitem.csv' 
    INTO TPCH1.LINEITEM WITH FIELD DELIMITED BY ',' THREADS 4;

```

This example imports data from the exported CSV file in Azure storage.

```
IMPORT FROM CSV FILE 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/DEMO_TBL1.csv'
    INTO "IMEX_DEMO"."DEMO_TBL1" WITH FIELD DELIMITED BY ',' THREADS 4;

```

This example imports data using a HIVE directory in an Amazon bucket.

```
IMPORT FROM PARQUET FILE IN HIVE PARTITION ' s3-region://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_hive_dir' 
   INTO TEST.TARGET_TABLE;

```

This example imports data using a DELTA LAKE directory in an Amazon bucket.

```
IMPORT FROM PARQUET FILE IN DELTA LAKE' s3-region://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_delta_dir' 
   INTO TEST.TARGET_TABLE;

```

**Related Information**  


[EXPORT Statement \(Data Import Export\)](export-statement-data-import-export-20da0be.md "Exports catalog objects.")

[EXPORT INTO Statement \(Data Import Export\)](export-into-statement-data-import-export-6a6f59b.md "Exports a table or view into a single-file, multi-file, or directory.")

[IMPORT Statement \(Data Import Export\)](import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

[IMPORT SCAN Statement \(Data Import Export\)](import-scan-statement-data-import-export-20f79b2.md "Searches the specified path for exported objects.")

[Importing and Exporting Data](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/LATEST/en-US/261937915fa5438ca545b8278b2979b7.html)

[SAP HANA Cloud, SAP HANA Database JSON Document Store Guide](https://help.sap.com/viewer/f2d68919a1ad437fac08cc7d1584ff56/LATEST/en-US/dca379e9c94940e998d9d4b5c656d1bd.html)

