<!-- loiobfd0969cda584ef4a62453b7f47533b1 -->

# WRITE

Write or create files or folders in an HDI container.



The SAP HDI Container API includes the `WRITE` command, which enables you to create files or folders in an HDI container's **work** file system.



## Signature

> ### Sample Code:  
> ```sql
> WRITE 
>  ( 
>   IN  PATHS        _SYS_DI.TT_FILESFOLDERS_CONTENT,
>   IN  PARAMETERS   _SYS_DI.TT_PARAMETERS, 
>   OUT RETURN_CODE  INT, 
>   OUT REQUEST_ID   BIGINT, 
>   OUT MESSAGES     _SYS_DI.TT_MESSAGES
>  ) 
> ```



<a name="loiobfd0969cda584ef4a62453b7f47533b1__section_gg2_zfw_f2b"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `WRITE` command:



### PATHS \[IN\]

Specifies the list of files or folders to write, including the content.

**\_SYS\_DI.TT\_FILESFOLDERS\_CONTENT**


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

CONTENT



</td>
<td valign="top">

BLOB



</td>
<td valign="top">

The content of a file is either binary or UTF8 text. The content of a folder **must** be NULL and is ignored during the write operation.



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



<a name="loiobfd0969cda584ef4a62453b7f47533b1__section_acb_1gw_f2b"/>

## Examples

The following example shows how to create files and folders in the work file system of a container named "C":

-   Folder: `src1/`

    -   Table file: `src1/t.hdbtable`

    -   View file: `src1/v.hdbview`


-   Folder: `src2/`

    -   Procedure file: `src2/p.hdbprocedure`



> ### Note:  
> For the sake of completeness, the `.hdiconfig` and `.hdinamespace` files are also included in the example. A folder must be specified, only if it does not yet exist.

> ### Sample Code:  
> Write folders and files to an HDI container's work file system
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
> 
> ```

To update \(overwrite\) existing files, you only need to specify the changed files. The following example shows how to update the procedure `src2/p.hdbprocedure`:

> ### Sample Code:  
> Update files in an HDI container's work file system
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS_CONTENT;
> INSERT INTO #PATHS (PATH, CONTENT) VALUES ('src2/p.hdbprocedure', 'PROCEDURE P (OUT RESULT INT)
> LANGUAGE SQLSCRIPT AS BEGIN SELECT COUNT(*)+2 INTO RESULT FROM V; end');
> CALL C#DI.WRITE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS;
> 
> ```

**Related Information**  


[DELETE](delete-d5c50df.md "Delete files or folders from an HDI container.")

[STATUS](status-e14a40c.md "Show the status of files or folders in an HDI container.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

