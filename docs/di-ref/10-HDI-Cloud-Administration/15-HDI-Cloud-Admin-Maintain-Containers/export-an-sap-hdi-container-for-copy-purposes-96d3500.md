<!-- loio96d3500aff614d878ef919badd2a53fd -->

# Export an SAP HDI Container for Copy Purposes to a Cloud Store

An HDI container administrator can export an HDI container to a Cloud Store.



<a name="loio96d3500aff614d878ef919badd2a53fd__prereq_cmk_233_qqb"/>

## Prerequisites

-   The user performing this task requires the privileges of an HDI **container** administrator.
-   Understand the information that describes how to prepare the SSL certificates required for the supported Cloud-storage scenario, which you can find in the following links in *Related Information* below:
    -   *Importing and Exporting with Amazon S3* 
    -   *Importing and Exporting with Azure Storage*
    -   *Importing and Exporting with Google Cloud Platform Storage*
    -   *Importing and Exporting with SAP HANA Cloud Data Lake Files Storage*

-   If the exported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the exported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While an export or import operation is running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The HDI container administrator can export a source container, for example, *<source\_container\_name\>*, to a Cloud store, for example, Amazon Simple Storage Service \(Amazon S3\) or Azure Cloud Storage, by calling the built-in procedure <code><i class="varname">&lt;source_container_name&gt;</i>#DI.EXPORT_CONTAINER_FOR_COPY</code>. The procedure expects as input a table containing any parameters. After the export procedure has completed successfully, the specified Cloud store contains not only the objects of the source container’s API schema \(<code><i class="varname">&lt;source_container_name&gt;</i>#DI</code>\) but also the deployed objects of the source container’s run-time schema \(*<source\_container\_name\>*\), including all dependent data..

To export the container *<source\_container\_name\>* for copy purposes to a Cloud Store in Amazon S3, Microsoft Azure, Google Cloud Platform, or SAP HANA Data Lake Cloud files, perform the following steps:



## Procedure

1.  Prepare the credentials and certificates required to enable access to the target Cloud storage.

    For detailed information about how to set up the tokens, permissions, credentials, certificates, and connection points required to enable access to the Cloud storage target that you want to export to, for example, Amazon S3, see *Related Information* below.

2.  Prepare the container export.

    Working with the HDI Container API, open an SQL console and connect to the source system as the HDI container's `*DT` user

    > ### Tip:  
    > This is the `hdi_user` from the service binding.

3.  Export the container.

    > ### Note:  
    > If the exported container depends on other containers, you need to export those other containers, too.

    Working with the HDI **container** API, call the container's `EXPORT_CONTAINER_FOR_COPY` procedure with the Cloud path you generated in a previous step, as illustrated in the following example:

    ```
    CREATE LOCAL TEMPORARY COLUMN TABLE #PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('target_path', 's3-<region>://<access_key>:<secret_key>@<bucket_name>/<object_id>');
    grant REFERENCES on PSE <PSE_name> to <source_container_name>; -- for authentication via credential stored in the PSE (only for HDLFS)
    grant REFERENCES on PSE <PSE_name> to <source_container_name>#DI; -- for authentication via credential stored in the PSE (only for HDLFS) 
    grant REFERENCES on PSE <PSE_name> to <source_container_name>#OO; -- for authentication via credential stored in the PSE (only for HDLFS) 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('credential', '<credential purpose>'); -- optional for authentication via credential stored in the PSE (required for HDLFS and GCS)
    CALL <source_container_name>#DI.EXPORT_CONTAINER_FOR_COPY('', '', #PARAMETERS, ?, ?, ?); 
    DROP TABLE #PARAMETERS;
    ```

    > ### Tip:  
    > Check that the first integer result is 0, which indicates success. One of the results is also a log with further information.


**Related Information**  


[Importing and Exporting with Amazon S3 \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/41d9c51cc69a4178b01db4bda77fb94a.html)

[Importing and Exporting with Azure Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/fd45a3b7917349a1a8cbc81e202c5cdd.html)

[Importing and Exporting with Google Cloud Platform Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/f975e58e44354dbfb21028532555da4b.html)

[Importing and Exporting with SAP HANA Cloud Data Lake Files Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/462c861413b043bd93b9e8e838249b6e.html)

[Import an SAP HDI Container for Copy Purposes from a Cloud Store](import-an-sap-hdi-container-for-copy-purposes-f11927d.md "An HDI container administrator can import an HDI container from a Cloud store.")

