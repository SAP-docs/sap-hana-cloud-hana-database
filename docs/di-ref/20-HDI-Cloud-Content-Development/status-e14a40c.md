<!-- loioe14a40cb7db048f99b5cea2548fc89ee -->

# STATUS

Show the status of files or folders in an HDI container.



The SAP HDI Container API includes the `STATUS` command, which enables you to display the status of specified files or folders in either the **work** or **deployed** file systems of an HDI container.



<a name="loioe14a40cb7db048f99b5cea2548fc89ee__section_ylt_tjw_f2b"/>

## Signature

> ### Sample Code:  
> ```sql
> STATUS 
>  ( 
>   IN   PATHS        _SYS_DI.TT_FILESFOLDERS,
>   IN   PARAMETERS   _SYS_DI.TT_PARAMETERS, 
>   OUT  RETURN_CODE  INT, 
>   OUT  REQUEST_ID   BIGINT, 
>   OUT  MESSAGES     _SYS_DI.TT_MESSAGES,
>   OUT  RESULT       _SYS_DI.TT_FILESFOLDERS_STATUS 
>  ) 
> ```



<a name="loioe14a40cb7db048f99b5cea2548fc89ee__section_gg2_zfw_f2b"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `STATUS` command:



### PATH \[IN\]

Specifies the list of files or folders whose status you want to check:

**\_SYS\_DI.TT\_FILESFOLDERS**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

PATH



</td>
<td valign="top">

NVARCHAR\(511\)



</td>
<td valign="top">

A single path is either a fully qualified file path \(for example, `/path/to/a/file.txt`\), or a fully qualified folder path \(for example, `/path/to/`\).



</td>
</tr>
</table>



### PARAMETERS \[IN\]

Additional parameters can be used to control various aspects of the procedure execution. If no parameters are needed, the empty predefined parameters table `_SYS_DI.T_NO_PARAMETERS` can be used.

**\_SYS\_DI.TT\_PARAMETERS**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The key name of the parameter



</td>
</tr>
<tr>
<td valign="top">

VALUE



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

The value assigned to the parameter



</td>
</tr>
</table>

The following additional parameters are available:

-   `container_lock_wait_timeout`

-   `trace_context`

-   `trace_level.<trace topic>`

-   `message_severity`




### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### RESULT \[OUT\]

Returns the result of the operation, with the details specified in the following table:

**\_SYS\_DI.TT\_FILESFOLDERS\_STATUS**


<table>
<tr>
<th valign="top">

Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

PATH



</td>
<td valign="top">

NVARCHAR\(511\)



</td>
<td valign="top">

A single path is either a fully qualified file path \(for example, `/path/to/a/file.txt`'\), or a fully qualified folder path \(for example, `/path/to/`\).



</td>
</tr>
<tr>
<td valign="top">

STATUS



</td>
<td valign="top">

NVARCHAR\(1\)



</td>
<td valign="top">

The status of the file or folder, for example:

-   A: Added

-   D: Deleted

-   M: Modified




</td>
</tr>
<tr>
<td valign="top">

SHA256



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

SHA256 hash of the file, if present in the **work** file system.



</td>
</tr>
<tr>
<td valign="top">

SHA256\_DEPLOYED



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

SHA256 hash of the file, if present in the **deployed** file system.



</td>
</tr>
</table>



<a name="loioe14a40cb7db048f99b5cea2548fc89ee__section_cfg_ypn_v2b"/>

## Examples

The following examples show how to use `C#DI.STATUS` command to compare the work \(design-time\) and deployed file systems in the HDI container "C" and display any differences. The examples show the following steps:

1.  Create content in the work file system of HDI container "C" and display the status.

2.  Deploy the newly created files and compare the status of the content in the work and deployed file systems of HDI container "C".

3.  Change content in the work file system, for example, by modifying and deleting design-time files and compare the status of the content in the work and deployed file systems of HDI container "C".


To see any meaningful information about the status, the respective file systems require some content. In this example, we create and use the following content:

-   Folder: `src1/`

    -   Table file: `src1/t.hdbtable`

    -   View file: `src1/v.hdbview`


-   Folder: `src2/`

    -   Procedure file: `src2/p.hdbprocedure`



> ### Note:  
> For the sake of completeness, the `.hdiconfig` and `.hdinamespace` files are also included in the following examples.



### Create Content in an HDI container "C" and Display its Status

In the following example, we first create content in HDI container "C':

> ### Sample Code:  
> Write folders and files to the work file system of container C
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS_CONTENT;
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('.hdiconfig', '{ "file_suffixes" : { "hdbtable" : { "plugin_name" : "com.sap.hana.di.table" }, "hdbview" : { "plugin_name" : "com.sap.hana.di.view" }, "hdbprocedure" : { "plugin_name" : "com.sap.hana.di.procedure" } } }');
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('.hdinamespace', '{ "name": "", "subfolder": "ignore" }');
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src1/', NULL);
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src1/t.hdbtable', 'COLUMN TABLE T ( A INTEGER )');
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src1/v.hdbview', 'VIEW V AS SELECT A FROM T');
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src2/', '');
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src2/p.hdbprocedure', 'PROCEDURE P (OUT RESULT INT) LANGUAGE SQLSCRIPT AS BEGIN SELECT COUNT(*) INTO RESULT FROM V; end');
> CALL C#DI.WRITE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS;
> ```

Assuming HDI container C's **deployed** file system is empty, a call to STATUS \(without asking for the status of a specific file or folder\) will show that three new files have been added to the work file system, as illustrated in the following example:

> ### Sample Code:  
> Status of Content in the Work File System of Container "C"
> 
> ```sql
> CALL C#DI.STATUS(_SYS_DI.T_NO_FILESFOLDERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
> 
> PATH                  STATUS   SHA256                    SHA256_DEPLOYED
> ---------------------------------------------------------------------------------
> src1/t.hdbtable       A        fb86b3a6c5e2ac98361d8...
> src1/v.hdbview        A        22273fb8a0684f93faa05...
> src2/p.hdbprocedure   A        b1b5c23366f73e8c6edc3...
> ```

> ### Note:  
> The value "A" in the ***STATUS*** column indicates that a file has been added to the work file system; the files corresponding hash value is displayed in the ***SHA256*** column.



### Deploy Content to an HDI Container and Display its Status

In this example, we deploy the newly created files to the deployed file system in HDI container "C" \(for example, using the `MAKE` API\).

> ### Sample Code:  
> Deploy Files to the Deployed File System of Container "C"
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #DEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('.hdiconfig');
> INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('.hdinamespace');
> INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('src1/t.hdbtable');
> INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('src1/v.hdbview');
> INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('src2/p.hdbprocedure');
> CREATE LOCAL TEMPORARY COLUMN TABLE #UNDEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATH_PARAMETERS LIKE _SYS_DI.TT_FILESFOLDERS_PARAMETERS;
> CALL C#DI.MAKE(#DEPLOY_PATHS, #UNDEPLOY_PATHS, #PATH_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #DEPLOY_PATHS;
> DROP TABLE #UNDEPLOY_PATHS;
> DROP TABLE #PATH_PARAMETERS; 
> ```

Comparing the content status at this point does not display any results because the content of the work file system in container "C" is identical to the content of container C's deployed file system.



### Display Content Status after Modification or Deletion

To demonstrate other status types, in this example we modify one of the files \(`src1/t.hdbtable`\) and deletion another file \(`src2/p.hdbprocedure`\) in the HDI container' s design-time work file system.

> ### Sample Code:  
> Modify `src1/t.hdbtable` in the Work File System of Container "C"
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS_CONTENT
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src1/t.hdbtable', 'COLUMN TABLE T ( A INTEGER, B INTEGER )');
> CALL C#DI.WRITE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS; 
> ```

> ### Sample Code:  
> Delete `src2/p.hdbprocedure` from the Work File System of Container "C"
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #PATHS (PATH) VALUES ('src2/p.hdbprocedure');
> CALL C#DI.DELETE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS; 
> ```

The `STATUS` API shows deleted files with the status ***D*** and modified files with the status of ***M***.

> ### Tip:  
> If files exist in both the work and deployed file system, then a hash value is shown for both file versions, otherwise only a hash value is displayed from the file system where the file is present.

> ### Sample Code:  
> Status of Files in the Work File System of Container "C"
> 
> ```sql
> CALL C#DI.STATUS(_SYS_DI.T_NO_FILESFOLDERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
> 
> PATH                  STATUS   SHA256                 SHA256_DEPLOYED
> ---------------------------------------------------------------------------------
> src2/p.hdbprocedure   D                               b1b5c23366f73e8c6edc3514...
> src1/t.hdbtable       M        13e1efb1fea4d951a2...  fb86b3a6c5e2ac98361d8c71...
> ```

Since no `PATH` has been specified to the `STATUS` API, the API returns the status for the entire work and deployed file systems. By passing specific file or folder names, only the status for the given `PATHS` is returned. The status for the folder `src1/` returns only the status of all files below the `src1` folder.

> ### Sample Code:  
> Status of the Contents of Folder `src1/` in Container "C"
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #PATHS (PATH) VALUES ('src1/');
> CALL C#DI.STATUS(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
> DROP TABLE #PATHS; 
> 
> PATH                 STATUS   SHA256                  SHA256_DEPLOYED
> ---------------------------------------------------------------------------------
> src1/t.hdbtable      M        13e1efb1fea4d951a2...   fb86b3a6c5e2ac98361d8c71...
> ```

You can display the status for specific files in an HDI container, for example, `src1/v.hdbview` and `src2/p.hdbprocedure`\). Note that results are displayed only for those files that have been changed.

> ### Sample Code:  
> Status of the Specific Files in Container "C"
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #PATHS (PATH) VALUES ('src1/v.hdbview');
> INSERT INTO #PATHS (PATH) VALUES ('src2/p.hdbprocedure');
> CALL C#DI.STATUS(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?, ?);
> DROP TABLE #PATHS; 
> 
> PATH                  STATUS   SHA256                 SHA256_DEPLOYED
> ---------------------------------------------------------------------------------
> src2/p.hdbprocedure   D                               b1b5c23366f73e8c6edc3514...
> ```

**Related Information**  


[WRITE](write-bfd0969.md "Write or create files or folders in an HDI container.")

[DELETE](delete-d5c50df.md "Delete files or folders from an HDI container.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

