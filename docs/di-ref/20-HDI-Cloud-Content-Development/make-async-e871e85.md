<!-- loioe871e85b48f940b8a4fbf356f85013b5 -->

# MAKE ASYNC

Trigger an asynchronous `MAKE` operation in an HDI container with a specified set of files or folders.



The SAP HDI Container API includes the `MAKE ASYNC` command, which enables you to start a `MAKE` operation in asynchronous mode in an HDI container using a specified set of files or folders. The call returns with a `REQUEST_ID` while the `MAKE ASYNC` command continues to run in the background.



<a name="loioe871e85b48f940b8a4fbf356f85013b5__section_ylt_tjw_f2b"/>

## Signature

> ### Sample Code:  
> ```sql
> MAKE ASYNC 
>  ( 
>   IN   DEPLOY_PATHS    _SYS_DI.TT_FILESFOLDERS, 
>   IN   UNDEPLOY_PATHS  _SYS_DI.TT_FILESFOLDERS, 
>   IN   PATH_PARAMETERS _SYS_DI.TT_FILESFOLDERS_PARAMETERS,
>   IN   PARAMETERS      _SYS_DI.TT_PARAMETERS, 
>   OUT  RETURN_CODE     INT, 
>   OUT  REQUEST_ID      BIGINT, 
>   OUT  MESSAGES        _SYS_DI.TT_MESSAGES
>  ) 
> ```



<a name="loioe871e85b48f940b8a4fbf356f85013b5__section_gg2_zfw_f2b"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `MAKE ASYNC` command:



### DEPLOY\_PATHS \[IN\]

Specifies a list of files or folders to be deployed:

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

A single path is either a fully qualified file path \(for example, `/path/to/a/file.txt`'\), or a fully qualified folder path \(for example, `/path/to/`\).



</td>
</tr>
</table>



### UNDEPLOY\_PATHS \[IN\]

Specifies a list of files or folders to be **un**deployed:

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

A single path is either a fully qualified file path \(for example, `/path/to/a/file.txt`'\), or a fully qualified folder path \(for example, `/path/to/`\).



</td>
</tr>
</table>



### PATH\_PARAMETERS \[IN\]

The following table lists path parameters you can use with the `MAKE ASYNC` command at the file or folder level:

**\_SYS\_DI.TT\_FILESFOLDERS\_PARAMETERS**


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

-   `max_parallel_jobs`

-   `optimized_redeploy`

-   `simulate_make`

-   `skip_unchanged_expansions`

-   `trace_context`

-   `trace_level.<trace topic>`

-   `treat_warnings_as_errors`

-   `undeploy_dependent_recursively`

-   `use_redeploy_for_unchanged`

-   `enable_make_enforcer`

-   `message_severity`




### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



<a name="loioe871e85b48f940b8a4fbf356f85013b5__section_qsw_lm3_w2b"/>

## Examples

The following examples show how to use the `MAKE_ASYNC` API to deploy files from the work file system to the deployed file system; this operation also creates the corresponding database objects in the catalog. The following content is written to the file system:

-   Folder: `src1/`

    -   Table file: `src1/t.hdbtable`

    -   View file: `src1/v.hdbview`


-   Folder: `src2/`

    -   Procedure file: `src2/p.hdbprocedure`



> ### Note:  
> For the sake of completeness, the `.hdiconfig` and `.hdinamespace` files are also included in the following example.

The following example shows how to create the files in container C's work file system:

> ### Sample Code:  
> Write Files to the Work File System of Container C
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

To deploy the newly created files with the `MAKE_ASYNC` API, you must provide the file paths in the `DEPLOY_PATHS` parameter.

> ### Restriction:  
> Only files can be deployed; it is not possible to deploy folders.

> ### Sample Code:  
> Deploy Files to the Work File System of Container C
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
> CALL C#DI.MAKE_ASYNC(#DEPLOY_PATHS, #UNDEPLOY_PATHS, #PATH_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #DEPLOY_PATHS;
> DROP TABLE #UNDEPLOY_PATHS; 
> DROP TABLE #PATH_PARAMETERS; 
> ```

To undeploy files with the `MAKE_ASYNC` API, the file paths must be provided in the `UNDEPLOY_PATHS` parameter. Undeploying a file will drop the corresponding database object and remove the file from the deployed file system. A `STATUS` call would then show the file as existing in the work file system only.

> ### Restriction:  
> Only files can be undeployed; it is not possible to undeploy folders.

> ### Sample Code:  
> Undeploy the File `src2/p.hdbprocedure` from the Work File System of Container C
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #DEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> CREATE LOCAL TEMPORARY COLUMN TABLE #UNDEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #UNDEPLOY_PATHS (PATH) VALUES ('src2/p.hdbprocedure');
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATH_PARAMETERS LIKE _SYS_DI.TT_FILESFOLDERS_PARAMETERS;
> CALL C#DI.MAKE_ASYNC(#DEPLOY_PATHS, #UNDEPLOY_PATHS, #PATH_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #DEPLOY_PATHS;
> DROP TABLE #UNDEPLOY_PATHS; 
> DROP TABLE #PATH_PARAMETERS; 
> ```

> ### Tip:  
> It is possible to combine the deployment and undeployment of files in the same `MAKE_ASYNC` call except where the same files are being deployed and undeployed.

**Related Information**  


[WRITE](write-bfd0969.md "Write or create files or folders in an HDI container.")

[MAKE](make-7a0b4c5.md "Trigger a make operation in an HDI container with a specified set of files or folders.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

