<!-- loio96d3500aff614d878ef919badd2a53fd -->

# Export an SAP HDI Container for Copy Purposes to a Cloud Store

An HDI container administrator can export an HDI container to a table or a file, which can then be used to import the container into a Cloud Store.



<a name="loio96d3500aff614d878ef919badd2a53fd__prereq_cmk_233_qqb"/>

## Prerequisites

-   The user performing this task requires the privileges of an HDI **container** administrator.
-   Understand the information that describes how to prepare the SSL certificates required for the supported Cloud-storage scenario, which you can find in the following links in *Related Information* below:
    -   *Importing and Exporting with Amazon S3* 
    -   *Importing and Exporting with Azure Storage*

-   If the exported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the exported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While an export or import operation is running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The HDI container administrator can export a source container, for example, `C1`, to a Cloud store, for example, Amazon Simple Storage Service \(Amazon S3\) or Azure Cloud Storage, by calling the built-in procedure `C1#DI.EXPORT_CONTAINER_FOR_COPY`. The procedure expects as input a table containing any parameters. After the export procedure has completed successfully, the specified Cloud store contains not only the objects of the source container’s API schema \(`C1#DI`\) but also the deployed objects of the source container’s run-time schema \(`C1`\), including all dependent data..

To export a container `C1` for copy purposes to a Cloud Store in Amazon S3, perform the following steps:



## Procedure

1.  Collect the following information from your Amazon S3 account:


    <table>
    <tr>
    <th valign="top">

    Parameter


    
    </th>
    <th valign="top">

    Example


    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
        Region


    
    </td>
    <td valign="top">
    
        eu-central-1


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Access Key


    
    </td>
    <td valign="top">
    
        KHDD8BIWJN938HJHAJ


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Secret Key


    
    </td>
    <td valign="top">
    
        nD-TI089LahksfjhZWQfgeuG4dAU


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Bucket Name


    
    </td>
    <td valign="top">
    
        hc-container-export


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Object ID


    
    </td>
    <td valign="top">
    
        Specifies a path or file name within the named bucket, for example,"MY\_HDI\_EXPORT"


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
        Certificate


    
    </td>
    <td valign="top">
    
         


    
    </td>
    </tr>
    </table>
    
2.  Assemble the S3 Cloud path based on the information you collected in the previous step.

    ```
    's3-<region>://<access_key>:<secret_key>@<bucket_name>/<object_id>'
    ```

    For example:

    ```
    's3-eu-central-1://KHDD8BIGFN938KWODJO:nD-TI089LagfnfjhZWQnfguG4dAU@hc-container-export/MY_HDI_EXPORT'
    ```

3.  Register the SSL certificates for the Cloud service both in the source and target databases.

    This example targets an Amazon S3 service:

    ```
    create pse HTTPS; 
    
    create certificate from ' 
    ----BEGIN CERTIFICATE---- 
    <obtain the correct S3 certificate from AWS support> 
    ----END CERTIFICATE---- 
    ' comment 'S3'; 
    
    select CERTIFICATE_ID from CERTIFICATES where COMMENT = 'S3'; 
    // - copy the returned ID into <SELECTED_CERTIFICATE_ID> of the next statement. 
    
    alter pse HTTPS add certificate <SELECTED_CERTIFICATE_ID>; 
    // – e.g. alter pse HTTPS add certificate 123456; 
    
    set pse HTTPS purpose REMOTE SOURCE;
    ```

4.  Prepare the container export.

    Working with the HDI Container API, open an SQL console and connect to the source system as the HDI container's `*DT` user

    > ### Tip:  
    > This is the `hdi_user` from the service binding.

5.  Export the container

    > ### Note:  
    > If the exported container depends on other containers, you need to export those other containers, too.

    Working with the HDI **Container** API, call the container's `EXPORT_CONTAINER_FOR_COPY` procedure with the Cloud path you generated in a previous step, as illustrated in the following example:

    ```
    CREATE LOCAL TEMPORARY COLUMN TABLE #PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('target_path', 's3-<region>://<access_key>:<secret_key>@<bucket_name>/<object_id>');
    CALL <CONTAINER_NAME>#DI.EXPORT_CONTAINER_FOR_COPY('', '', #PARAMETERS, ?, ?, ?); 
    DROP TABLE #PARAMETERS;
    ```

    > ### Tip:  
    > Check that the first integer result is 0, which indicates success. One of the results is also a log with further information.


**Related Information**  


[Importing and Exporting with Amazon S3 \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/41d9c51cc69a4178b01db4bda77fb94a.html)

[Importing and Exporting with Azure Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/fd45a3b7917349a1a8cbc81e202c5cdd.html)

[Import an SAP HDI Container for Copy Purposes from a Cloud Store](import-an-sap-hdi-container-for-copy-purposes-f11927d.md "An HDI container administrator can import an HDI container from a Cloud store.")

