<!-- loiod5c50df72fd44c3d9a20a0b6cbd4af30 -->

# DELETE

Delete files or folders from an HDI container.



The SAP HDI Container API includes the `DELETE` command, which enables you to remove files or folders from an HDI container's **work** file system.



<a name="loiod5c50df72fd44c3d9a20a0b6cbd4af30__section_ylt_tjw_f2b"/>

## Signature

> ### Sample Code:  
> ```sql
> DELETE 
>  ( 
>   IN   PATHS        _SYS_DI.TT_FILESFOLDERS,
>   IN   PARAMETERS   _SYS_DI.TT_PARAMETERS, 
>   OUT  RETURN_CODE  INT, 
>   OUT  REQUEST_ID   BIGINT, 
>   OUT  MESSAGES     _SYS_DI.TT_MESSAGES
>  ) 
> ```



<a name="loiod5c50df72fd44c3d9a20a0b6cbd4af30__section_gg2_zfw_f2b"/>

## Parameters

The following parameters can be used with `IN` and `OUT` parameters in the `DELETE` command:



### PATH \[IN\]

Specifies the list of files or folders to delete.

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

-   `ignore_non_existing_paths`

-   `recursive`

-   `trace_context`

-   `trace_level.<trace topic>`

-   `message_severity`


> ### Tip:  
> For more information about all available SAP HANA HDI parameters, see *Available SAP HDI Parameters* in *Related Information* below.



### RETURN\_CODE \[OUT\]

The return code indicates if the procedure executed successfully. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



### REQUEST\_ID \[OUT\]

A unique ID is generated for each HDI container API call. For more details about which IDs are generated for API calls, see *The SQL API for SAP HDI* in *Related Information*.



### MESSAGES \[OUT\]

A table is used to display messages that contain information logged during \(and about\) the execution of the procedure. For more details about which codes are returned, see *The SQL API for SAP HDI* in *Related Information*.



<a name="loiod5c50df72fd44c3d9a20a0b6cbd4af30__section_acb_1gw_f2b"/>

## Examples

The following example shows how to **delete** files and folders from the work \(design-time\) file system of a container named "C" that contains the following content:

-   Folder: `src1/`

    -   Table file: `src1/t.hdbtable`

    -   View file: `src1/v.hdbview`


-   Folder: `src2/`

    -   Procedure file: `src2/p.hdbprocedure`



> ### Note:  
> For the sake of completeness, the `.hdiconfig` and `.hdinamespace` files are also included in the following example.

In the following example, we first create the content, and then show how to delete selected files and folders from the created content.

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
> CALL <container name>#DI.WRITE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS;
> ```

The following example shows how to delete the view file `src1/v.hdbview` and the folder `src2/` from the content created in container "C".

> ### Note:  
> It is not possible to delete a folder that contains content. Before deleting a folder, you first have to ensure that it is empty, for example, by deleting any files in the folder intended for deletion.

In this example, to remove the folder `src2/`, the file `src2/p.hdbprocedure` has to be deleted, too.

> ### Sample Code:  
> Delete files and folders from an HDI container's work file system
> 
> ```sql
> CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
> INSERT INTO #PATHS (PATH) VALUES ('src1/v.hdbview');
> INSERT INTO #PATHS (PATH) VALUES ('src2/p.hdbprocedure');
> INSERT INTO #PATHS (PATH) VALUES ('src2/');
> CALL <container name>#DI.DELETE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
> DROP TABLE #PATHS;
> 
> ```

**Related Information**  


[WRITE](write-bfd0969.md "Write or create files or folders in an HDI container.")

[STATUS](status-e14a40c.md "Show the status of files or folders in an HDI container.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

[The SQL API for SAP HANA Deployment Infrastructure \(HDI\)](../the-sql-api-for-sap-hana-deployment-infrastructure-hdi-035dbbe.md "An SQL application programming interface (API) is available to help maintain the SAP HANA Deployment Infrastructure (HDI).")

[Available SAP HDI Parameters](https://help.sap.com/docs/HANA_CLOUD_DATABASE/c2cc2e43458d4abda6788049c58143dc/e2d3e543067e4f3282bf6dbf880c6b2d.html?version=2023_3_QRC#available-sap-hdi-parameters)

