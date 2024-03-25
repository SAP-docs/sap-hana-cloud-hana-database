<!-- loio6a6f59bbfbb64ade84d83d7f87789753 -->

# EXPORT INTO Statement \(Data Import Export\)

Exports a table or view into a single-file, multi-file, or directory.



## Syntax

```
EXPORT INTO [ <export_format> ] <cloud_provider_path>
    FROM <export_into_from_option>
   [ WITH <export_into_option_list> ]
```



<a name="loio6a6f59bbfbb64ade84d83d7f87789753__section_zv4_dfv_bgb"/>

## Syntax Elements


<dl>
<dt><b>

*<export\_format\>*

</b></dt>
<dd>

Specifies the format of the data being exported.

```
<export_format> ::= 
   {CSV FILE | PARQUET FILE | JSON FILE}
```

If not specified, the default format is CSV.



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


<dl>
<dt><b>

*<storage\_path\>*

</b></dt>
<dd>

Specifies a path to the object for the export using one of the supported formats:

```
<storage_path> ::= 
   { <filename>.csv
   | <filename>.parquet
   | <filename>.json
   | <directory>/
   | <directory>/<prefix> }
```


<dl>
<dt><b>

*<filename\>*.csv, *<filename\>*.parquet or *<filename\>*.json

</b></dt>
<dd>

Data is exported as a single file into the specified file name that must end in either .csv, .parquet, or .json.



</dd><dt><b>

*<directory\>*/

</b></dt>
<dd>

Data is exported as multiple files into the specified directory, with the ROW GROUP SIZE value used to divide the data into multiple files, with each file containing 1 row group. The path must end with a forward slash \(/\). The format of the output filename for each file is as follows:

-   **Parquet output filename format:** 

    ```
    <directory>/ ::= part-<partition_number>-<row_group_number>.<compression>.parquet
    ```

    For example: `part-00001-00001.snappy.parquet, part-00002-00002.snappy.parquet, ...`

-   **CSV output filename format:**

    ```
    <directory>/ ::= part-<partition_number>-<row_group_number>.csv
    ```

    For example: `part-00001-00001.csv, part-00002-00002.csv, ...`



<dl>
<dt><b>

*<partition\_number\>*

</b></dt>
<dd>

Specifies the logical partition id of the containing table data, or 0 if not partitioned. The *<partition\_number\>* value is a zero-padded 5 digit value, starting at 0 and incrementing by 1 for each new row group.

> ### Note:  
> In scenarios where the export target is accessed indirectly, such as through a query string, view, or virtual table, the `<partition_number>` in the exported file name will default to 0, regardless of the partition status of the target table. This behavior applies uniformly to both CSV and Parquet file formats and is an important consideration in export operations.



</dd><dt><b>

*<row\_group\_number\>*

</b></dt>
<dd>

Specifies the logical group number of the containing table data. The *<row\_group\_number\>* value is a zero-padded 5 digit value, starting at 0 and incrementing by 1 for each new row group.



</dd><dt><b>

*<compression\>*

</b></dt>
<dd>

Specifies the compression algorithms for the export.

```
<compression> ::= { none | snappy | gzip | lz4 }
```



</dd>
</dl>



</dd><dt><b>

*<directory\>*/*<prefix\>*

</b></dt>
<dd>

Data is exported as multiple files into the specified directory, with the ROW GROUP SIZE value used to divide the data into multiple files, with each file containing 1 row group. The prefix is added to each file in the directory. The format of the output filename for each file is as follows:

-   **Parquet output filename format:** 

    ```
    <directory>/<prefix> ::= <prefix>-part-<partition_number>-<row_group_number>.<compression>.parquet
    ```

    For example: `my_prefix-part-00001-00001.snappy.parquet, my_prefix-part-00002-00002.snappy.parquet, ...`

-   **CSV output filename format:**

    ```
    <directory>/<prefix> ::= <prefix>-part-<partition_number>-<row_group_number>.csv
    ```

    For example: `my_prefix-part-00001-00001.csv, my_prefix-part-00002-00002.csv, ...`


If not specified, *<prefix\>* is empty. *<partition\_number\>* and *<row\_group\_number\>* start at 0, and increment by 1 for each new partition/row group.

CSV format does not support the concept of a row group, but for syntax consistency between filename formats, a value is still used to divide data into multiple CSV files. This value is equal to or smaller than the WITH ROW GROUP SIZE value.



</dd>
</dl>



</dd><dt><b>

*<azure\_path\>*

</b></dt>
<dd>

Specifies the location for the Azure export file.

```
<azure_path> ::= 
'azure://[<azure_credentials>@]<azure_container_name>/<storage_path>
```


<dl>
<dt><b>

*<azure\_credentials\>*

</b></dt>
<dd>

Required when not using the CREDENTIAL parameter.

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

*<storage\_path\>*

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
's3-<amazon_region>://[<amazon_credentials>@]<amazon_bucket_name>/<storage_path>
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

*<storage\_path\>*

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
'gs://[<google_credentials>@]<google_bucket_name>/<storage_path>'
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

*<storage\_path\>*

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

*<export\_into\_from\_option\>*

</b></dt>
<dd>

Specifies where the data to be exported exists.

```
<export_into_from_option> ::= { <table_or_view_name> | '(' <select_stmt_no_hint> ')' }
```


<dl>
<dt><b>

table\_or\_view\_name

</b></dt>
<dd>

Specifies the name of the table or view to be exported.

```
<table_or_view_object_name> ::= [ <schema_name>.]<identifier>
```



</dd><dt><b>

*<select\_stmt\_no\_hint\>*

</b></dt>
<dd>

Specifies the query string to be used to export the data. Supported query strings are simple SELECT statements that can include selection, projection and a join query without a hint and type casting. All schema objects included in the query string should be qualified with schema name. Temporary tables are not supported.



</dd>
</dl>



</dd><dt><b>

*<export\_into\_option\_list\>*

</b></dt>
<dd>

Specifies a list of options that control export behavior.

```
<export_into_option_list> ::= <export_into_option> [ <export_into_option> […] ] 

<export_into_option> ::= 
  { THREADS <number_of_threads> 
  | COLUMN LIST IN FIRST ROW 
  | RECORD DELIMITED BY <string_for_record_delimiter> 
  | FIELD DELIMITED BY <string_for_field_delimiter> 
  | OPTIONALLY ENCLOSED BY <character_for_optional_enclosure> 
  | ESCAPE <escape_character> 
  | COMPRESSION '{none | snappy | gzip | lz4 }' 
  | ROW GROUP SIZE <integer> 
  | CREDENTIAL '<purpose_def> 
  | REPLACE }
```


<dl>
<dt><b>

THREADS *<number\_of\_threads\>*

</b></dt>
<dd>

Specifies the number of threads that can be used for the export. The default value is the smaller of: 10 or the number of CPU cores.

This option is valid for CSV and parquet formats.

```
THREADS <number_of_threads>

<number_of_threads> ::= <unsigned_integer>
```



</dd><dt><b>

COLUMN LIST IN FIRST ROW

</b></dt>
<dd>

Indicates that the column list is stored in the first row of the CSV export file.

This option is valid for CSV format only.



</dd><dt><b>

RECORD DELIMITED BY *<string\_for\_record\_delimiter\>*

</b></dt>
<dd>

```
RECORD DELIMITED BY <string_for_record_delimiter>

<string_for_record_delimiter> ::= <string_literal>
```

This option is valid for CSV format only.



</dd><dt><b>

FIELD DELIMITED BY *<string\_for\_field\_delimiter\>*

</b></dt>
<dd>

Specifies the field delimiter of the CSV file.

```
FIELD DELIMITED BY <string_for_field_delimiter>

<string_for_field_delimiter> ::= <string_literal>
```

This option is valid for CSV format only.



</dd><dt><b>

OPTIONALLY ENCLOSED BY *<character\_for\_optional\_enclosure\>*

</b></dt>
<dd>

Specifies the optional enclosure character that delimits field data.

```
OPTIONALLY ENCLOSED BY <character_for_optional_enclosure>

<character_for_optional_enclosure> ::= <character_literal>
```

This option is valid for CSV format only.



</dd><dt><b>

*<escape\_character\>*

</b></dt>
<dd>

Specifies the escape character used in the export data.

```
<escape_character> ::= <character_literal>
```

This option is valid for CSV format only.



</dd><dt><b>

COMPRESSION

</b></dt>
<dd>

The default value is snappy. This option is valid for parquet format only.



</dd><dt><b>

ROW GROUP SIZE

</b></dt>
<dd>

Specifies the number of rows per each row group. This option is valid for single-file exports in parquet format, or multi-file exports for both parquet and CSV formats \(1 file per row group\).

```
<ROW GROUP SIZE> ::= <integer>
```

The default value is 1,000,000. If a ROW GROUP SIZE is not specified, then it is calculated based on the size of the table data, with each row group containing 100 MB for parquet, or 256 MB for CSV. If an invalid ROW GROUP SIZE is specified \(for example, a value < 0\), then the default value of 1,000,000 is used.



</dd><dt><b>

CREDENTIAL *<purpose\_def\>*

</b></dt>
<dd>

Specifies the name of the credential defined in the CREATE CREDENTIAL statement. Since the credentials are defined within the credential, they no longer appear as plain text as part of export statements. The CREDENTIAL clause cannot be specified when *<cloud\_provider\_path\>* contains credentials. The CREDENTIAL clause is required for exports from SAP HANA Cloud, Data Lake Files, but is optional for all other cloud platforms.



</dd><dt><b>

REPLACE

</b></dt>
<dd>

If the export file already exists in the specified directory, then it is overwritten when REPLACE is specified. If REPLACE is not specified and a previously exported file exists in the specified directory, an error is returned. If the export filename already exists as a directory in the specified location, an error is returned, regardless of the use of the REPLACE clause.



</dd>
</dl>



</dd>
</dl>



<a name="loio6a6f59bbfbb64ade84d83d7f87789753__section_fvd_zlc_ycb"/>

## Permissions

Requires:

-   EXPORT system privilege
-   SELECT privilege on the objects being exported.



<a name="loio6a6f59bbfbb64ade84d83d7f87789753__section_ffp_dfv_bgb"/>

## Description

Use the EXPORT INTO statement to export the data from a table or view into a single CSV, Parquet, or JSON file, or into a directory with multiple CSV, Parquet, or JSON files.

The EXPORT INTO command does not support parameterized views.

The values of calculated columns defined as `C AS A+B` and generated columns defined as `GENERATED ALWAYS AS A+B` are not exported.



<a name="loio6a6f59bbfbb64ade84d83d7f87789753__section_xmp_dfv_bgb"/>

## Examples

This statement exports a table into CSV file in an Azure bucket.

```
EXPORT INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1_lineitem.csv' 
   FROM TPCH1.LINEITEM WITH FIELD DELIMITED BY',' THREADS 4;
```

The following example creates a table and view, populates them, and exports each of them to a separate CSV file.

```
CREATE TABLE T1 (A INT, B NVARCHAR(50));
INSERT INTO T1 VALUES (0, 'test!@#$%');
CREATE VIEW V AS SELECT * FROM T1;
EXPORT INTO 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1_lineitem.csv' FROM V;
EXPORT INTO 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/tpch1_lineitem.csv' FROM T1 WITH COLUMN LIST IN FIRST ROW FIELD DELIMITED BY '!' ESCAPE '@';
```

This example exports a table into a CSV file in an Azure bucket.

```
EXPORT INTO 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/DEMO_TBL1.csv'
   FROM "IMEX_DEMO"."DEMO_TBL1" WITH FIELD DELIMITED BY ',' THREADS 4;

```

This example exports a table into a CSV file in Google bucket.

```
EXPORT INTO 'gs://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/DEMO_TBL1.csv'
   FROM "IMEX_DEMO"."DEMO_TBL1" WITH FIELD DELIMITED BY ',' THREADS 4;

```

The following example exports multiple parquet files, one file per row group, with 100 records per file in an Amazon bucket.

```
EXPORT INTO PARQUET FILE 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/my_dir/' 
   FROM SCH.NORMAL_TBL WITH ROW GROUP SIZE 100;
```

The following example exports multiple parquet files, one file per row group in a partition, with 100 records per file in an Amazon bucket.

```
EXPORT INTO PARQUET FILE 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/my_dir/' 
   FROM SCH.PARTITIONED_TBL WITH ROW GROUP SIZE 100;
```

The following example exports data to a CSV file, in an Azure bucket, based on a query string.

```
EXPORT INTO CSV FILE 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/export.csv' 
   FROM (SELECT SCHEMA_NAME, TABLE_NAME FROM SYS.TABLES);
```

The following example exports multiple parquet files, one file per row group in a partition, with 100 records per file with a prefix specified, in an Amazon bucket.

```
EXPORT INTO PARQUET FILE 's3-region2://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_bucket/my_demo/my_dir/my-prefix' 
   FROM SCH.PARTITIONED_TBL WITH ROW GROUP SIZE 100;
```

**Related Information**  


[EXPORT Statement \(Data Import Export\)](export-statement-data-import-export-20da0be.md "Exports catalog objects.")

[IMPORT Statement \(Data Import Export\)](import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

[IMPORT FROM Statement \(Data Import Export\)](import-from-statement-data-import-export-20f712e.md "Imports external data into an existing table.")

[IMPORT SCAN Statement \(Data Import Export\)](import-scan-statement-data-import-export-20f79b2.md "Searches the specified path for exported objects.")

[Importing and Exporting Data](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/LATEST/en-US/261937915fa5438ca545b8278b2979b7.html)

