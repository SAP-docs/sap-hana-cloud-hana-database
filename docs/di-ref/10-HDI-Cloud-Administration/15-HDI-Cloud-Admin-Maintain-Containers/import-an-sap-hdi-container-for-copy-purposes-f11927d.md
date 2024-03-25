<!-- loiof11927de04b44bfa9a12bb85850c39d9 -->

# Import an SAP HDI Container for Copy Purposes from a Cloud Store

An HDI container administrator can import an HDI container from a Cloud store.



<a name="loiof11927de04b44bfa9a12bb85850c39d9__prereq_cmk_233_qqb"/>

## Prerequisites

-   The user performing this task requires the privileges of an HDI **container** administrator on the target system.
-   Understand the information that describes how to prepare the SSL certificates required for the supported Cloud-storage scenario, which you can find in the following links in *Related Information* below:
    -   *Importing and Exporting with Amazon S3* 
    -   *Importing and Exporting with Azure Storage*
    -   *Importing and Exporting with Google Cloud Platform Storage*
    -   *Importing and Exporting with SAP HANA Cloud Data Lake Files Storage*

-   If the imported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the imported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While the export or import operation in running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The HDI container administrator can import a source container from a Cloud store, for example, Amazon Simple Storage Service \(Amazon S3\) or Azure Cloud Storage, by calling the built-in procedure <code><i class="varname">&lt;target_container name&gt;</i>#DI.IMPORT_CONTAINER_FOR_COPY</code>. The procedure expects as input a table containing any necessary parameters.

The import procedure removes the contents of the target container, writes the data from the Cloud store to the target container, and runs a make. Any existing objects and data in the target container will be deleted before the import procedure starts. After the import procedure has completed successfully, the target container will be a copy of the source container including all the data of the original run-time schema.

To import a container *<source\_container\_name\>* for copy purposes from a Cloud Store such as Amazon S3, Microsoft Azure, Google Cloud Platform, or SAP HANA Data Lake Cloud files, perform the following steps:



## Procedure

1.  Prepare the credentials and certificates required to enable access to the target Cloud storage.

    For detailed information about how to set up the tokens, permissions, credentials, certificates, and connection points required to enable access to the Cloud storage target that you want to import from, for example, Amazon S3, see *Related Information* below.

2.  Prepare the container import.

    > ### Note:  
    > The target system should be the same Cloud version as the source system \(or more recent\), and the target HDI container *<target\_container\_name\>* must already exist, or be created before the import operation, for example, by an HDI container-group administrator. If the target HDI container is not empty, the content is overwritten.

    Working with the HDI container API, open an SQL console and connect to the target system as an HDI container administrator user.

3.  Set up any required dependencies and privileges.

    All external objects referenced by design-time objects in the imported container \(as well as the remote container\(s\) in which the external objects are located\) must already be available in the target database and accessible to the object owner of the imported container when the import operation starts. So, if necessary, grant the object owner <code><i class="varname">&lt;source_container_name&gt;</i>#OO</code> of the imported container any privileges required to access the external objects in any remote containers.

    > ### Note:  
    > If remote container *<remote\_container\_name\>* exposes a role for enabling cross-container access, this role must be granted to the dependent target container’s user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code>. The role can be granted to user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code> either by a role administrator \(`ROLE ADMIN`\) or by using the HDI **container** API for role assignment.
    > 
    > If remote container *<remote\_container\_name\>* does not expose a role, the required privileges must be granted to the dependent target container’s user <code><i class="varname">&lt;target_container_name&gt;</i>#OO</code> by other means, for example, using the HDI **container** API for granting schema privileges.

4.  Import the container.

    > ### Note:  
    > If the HDI container you want to import \(for example, *<source\_container\_name\>*\) has dependencies to objects in another remote container \(for example, in *<remote\_container\_name\>*\), then you need to import *<remote\_container\_name\>* first and set up any required privileges, as described above.

    Working with the HDI container API, call the container's `IMPORT_CONTAINER_FOR_COPY` procedure with the Cloud path you generated in a previous step, as illustrated in the following example:

    Working with the HDI **Container** API, open an SQL console and run the following SQL code after replacing the various PSE and container names \(for example, *<source\_container\_name\>* and *<source\_container\_name\>*\) with the names of your source and target containers:

    ```
    CREATE LOCAL TEMPORARY COLUMN TABLE #PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('source_path', 's3-<region>://<access_key>:<secret_key>@<bucket_name>/<object_id>');
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('original_container_name', '<source_container_name>'); 
    grant REFERENCES on PSE <PSE_name> to <target_container_name>; -- for authentication via credential stored in the PSE (only for HDLFS)
    grant REFERENCES on PSE <PSE_name> to <target_container_name>#DI; -- for authentication via credential stored in the PSE (only for HDLFS) 
    grant REFERENCES on PSE <PSE_name> to <target_container_name>#OO; -- for authentication via credential stored in the PSE (only for HDLFS) 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('credential', '<credential_purpose>'); -- optional for authentication via credential stored in the PSE (required for HDLFS and GCS)
    CALL <target_container_name>#DI.IMPORT_CONTAINER_FOR_COPY('', '', #PARAMETERS, ?, ?, ?);
    DROP TABLE #PARAMETERS;
    ```

    > ### Tip:  
    > Check that the first integer result is 0, which indicates success. One of the results is also a log with further information.

5.  Confirm that the container now has all the data from the source system.


**Related Information**  


[Importing and Exporting with Amazon S3 \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/41d9c51cc69a4178b01db4bda77fb94a.html)

[Importing and Exporting with Azure Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/fd45a3b7917349a1a8cbc81e202c5cdd.html)

[Importing and Exporting with Google Cloud Platform Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/f975e58e44354dbfb21028532555da4b.html)

[Importing and Exporting with SAP HANA Cloud Data Lake Files Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/docs/HANA_CLOUD_DATABASE/f9c5015e72e04fffa14d7d4f7267d897/462c861413b043bd93b9e8e838249b6e.html)

[Export an SAP HDI Container for Copy Purposes to a Cloud Store](export-an-sap-hdi-container-for-copy-purposes-96d3500.md "An HDI container administrator can export an HDI container to a Cloud Store.")

