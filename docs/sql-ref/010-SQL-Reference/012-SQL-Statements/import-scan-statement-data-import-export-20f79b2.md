<!-- loio20f79b2175191014a45f9947577a2e85 -->

# IMPORT SCAN Statement \(Data Import Export\)

Searches the specified path for exported objects.



## Syntax

```
IMPORT SCAN <cloud_provider_path> [ <file> ] [ WITH <import_scan_option_list> ] 
```



<a name="loio20f79b2175191014a45f9947577a2e85__sql_import_scan_1sql_import_scan_syntax_elements"/>

## Syntax Elements

Specifies the cloud storage location for the import.

```
<cloud_provider_path> ::=
   { <azure_path> 
   | <amazon_path>
   | <google_path>
   | <hdlfs_path> }
```

Refer to the local temporary table \#IMPORT\_SCAN\_RESULT to check the list of tables.


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


<dl>

</dl>


<dl>
<dt><b>

*<file\>*

</b></dt>
<dd>

Specifies the file to be scanned for import data. Supported file formats are CSV and parquet.

```
<file> ::= <string_literal>
```

Refer to the local temporary table \#IMPORT\_SCAN\_FILE\_RESULT to check the list of column names. If the length of a column name exceeds the maximum SAP HANA Cloud-supported column length, the value in COLUMN\_NAME is truncated to the maximum supported length followed by an ellipsis. The table \#IMPORT\_SCAN\_FILE\_RESULT consists only of single column named COLUMN\_NAME.



</dd>
</dl>


<dl>
<dt><b>

*<import\_scan\_option\_list\>*

</b></dt>
<dd>

Specifies additional options for the import.

```
<import_scan_option_list> ::= <import_scan_option> [,<import_scan_option> [,...] ]
```

```
<import_scan_option> ::= 
 { COLUMN LIST IN FIRST ROW
 | RECORD DELIMITED BY <string_for_record_delimiter>
 | FIELD DELIMITED BY <string_for_field_delimiter>
 | CREDENTIAL '<purpose_def> }
```

If COLUMN LIST IN FIRST ROW is not specified, the column names from \#IMPORT\_SCAN\_FILE\_RESULT will be COLUMN\_<N\>s.

*<import\_scan\_option\_list\>* is only supported with a CSV file.


<dl>
<dt><b>

CREDENTIAL *<purpose\_def\>*

</b></dt>
<dd>

Specifies the name of the credential defined in the CREATE CREDENTIAL statement. Since the credentials are defined within the credential, they no longer appear as plain text as part of import statements. The CREDENTIAL clause cannot be specified when *<cloud\_provider\_path\>* contains credentials. The CREDENTIAL clause is required for imports to SAP HANA Cloud, Data Lake Files, but is optional for all other cloud platforms.



</dd>
</dl>



</dd>
</dl>



<a name="loio20f79b2175191014a45f9947577a2e85__section_ffx_knl_ctb"/>

## Permissions

Requires:

-   IMPORT system privilege

    CREATE TEMPORARY TABLE privilege on the current schema




<a name="loio20f79b2175191014a45f9947577a2e85__sql_import_scan_1sql_import_scan_description"/>

## Description

The IMPORT SCAN statement searches the given path for objects exported with the EXPORT statement and stores the results in the following session-local temporary table at current\_schema of the session if the statement is executed successfully. If current\_schema of the session is invalid, then IMPORT SCAN throws an exception as it cannot create its result table of the current\_schema.

***<current\_schema\>*.\#IMPORT\_SCAN\_RESULT** 


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

The schema of the object

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

The name of the object

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

The type of the object \(TABLE, VIEW, and so on\)

</td>
</tr>
<tr>
<td valign="top">

EXISTS

</td>
<td valign="top">

TINYINT

</td>
<td valign="top">

Does the object already exist in the system? \(0/1\)

</td>
</tr>
</table>

***<current\_schema\>*.\#IMPORT\_SCAN\_FILE\_RESULT** 


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

COLUMN\_NAME

</td>
<td valign="top">

NVARCHAR\(256\)

</td>
<td valign="top">

Displays the name of the column.

</td>
</tr>
</table>



<a name="loio20f79b2175191014a45f9947577a2e85__sql_import_scan_1sql_import_examples"/>

## Example

Scan the file in Azure for import data.

```
IMPORT SCAN 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@my_demo/tpch1_lineitem.csv';
```

Select the data in the \#IMPORT\_SCAN\_RESULT table to get the result of the scan.

```
SELECT * FROM #IMPORT_SCAN_RESULT;
```


<table>
<tr>
<th valign="top">

DATABASE\_NAME

</th>
<th valign="top">

SCHEMA\_NAME

</th>
<th valign="top">

OBJECT\_NAME

</th>
<th valign="top">

OBJECT\_TYPE

</th>
<th valign="top">

EXISTS

</th>
</tr>
<tr>
<td valign="top">

OP2

</td>
<td valign="top">

IMEX\_RESTTEST

</td>
<td valign="top">

TEST\_TBL\_COLUMN

</td>
<td valign="top">

TAABLE

</td>
<td valign="top">

0

</td>
</tr>
<tr>
<td valign="top">

OP2

</td>
<td valign="top">

IMEX\_RESTTEST

</td>
<td valign="top">

TEST\_TBL\_ROW

</td>
<td valign="top">

TABLE

</td>
<td valign="top">

0

</td>
</tr>
</table>

Scan the file data.parquet in the path `'/data/import_path'` Azure storage for import data.

```
IMPORT SCAN 'azure://AKIAxxxxxxxxxx:xl6WWxxxxxxxxxx@/data/import_path/data.parquet';
```

Select the data in the \#IMPORT\_SCAN\_FILE\_RESULT table to get the result of the scan.

```
SELECT * FROM #IMPORT_SCAN_FILE_RESULT;
```


<table>
<tr>
<th valign="top">

COLUMN\_NAME

</th>
</tr>
<tr>
<td valign="top">

field\_bool

</td>
</tr>
<tr>
<td valign="top">

field\_uint8

</td>
</tr>
<tr>
<td valign="top">

field\_int16

</td>
</tr>
<tr>
<td valign="top">

field\_int32

</td>
</tr>
<tr>
<td valign="top">

field\_int64

</td>
</tr>
<tr>
<td valign="top">

field\_float

</td>
</tr>
<tr>
<td valign="top">

field\_double

</td>
</tr>
<tr>
<td valign="top">

field\_string

</td>
</tr>
</table>

**Related Information**  


[EXPORT Statement \(Data Import Export\)](export-statement-data-import-export-20da0be.md "Exports catalog objects.")

[EXPORT INTO Statement \(Data Import Export\)](export-into-statement-data-import-export-6a6f59b.md "Exports a table or view into a single-file, multi-file, or directory.")

[IMPORT Statement \(Data Import Export\)](import-statement-data-import-export-20f75ad.md "Imports catalog objects.")

[IMPORT FROM Statement \(Data Import Export\)](import-from-statement-data-import-export-20f712e.md "Imports external data into an existing table.")

[Importing and Exporting Data](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/LATEST/en-US/261937915fa5438ca545b8278b2979b7.html)

