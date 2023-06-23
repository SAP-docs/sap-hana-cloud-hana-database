<!-- loiof11927de04b44bfa9a12bb85850c39d9 -->

# Import an SAP HDI Container for Copy Purposes from a Cloud Store

An HDI container administrator can import an HDI container from a Cloud store.



<a name="loiof11927de04b44bfa9a12bb85850c39d9__prereq_cmk_233_qqb"/>

## Prerequisites

-   The user performing this task requires the privileges of an HDI **container** administrator on the target system.
-   Understand the information that describes how to prepare the SSL certificates required for the supported Cloud-storage scenario, which you can find in the following links in *Related Information* below:
    -   *Importing and Exporting with Amazon S3* 
    -   *Importing and Exporting with Azure Storage*

-   If the imported HDI container has any dependencies to other HDI containers or normal database schemas, then the other containers and schemas must also be made available in the target database first.
-   If the imported HDI container has been granted privileges to other containers or schemas, the granted privileges must also be assigned in the database before you import the dependent HDI container.

> ### Note:  
> While the export or import operation in running, it is not possible to run any other HDI API on the affected HDI container.



## Context

The HDI container administrator can import a source container from a Cloud store, for example, Amazon Simple Storage Service \(Amazon S3\) or Azure Cloud Storage, by calling the built-in procedure `C2#DI.IMPORT_CONTAINER_FOR_COPY`. This procedure expects as input a table containing any necessary parameters.

The import procedure removes the contents of the target container, writes the data from the Cloud store to the target container, and runs a make. Any existing objects and data in the target container will be deleted before the import procedure starts. After the import procedure has completed successfully, the target container will be a copy of the source container including all the data of the original run-time schema.

To import a container for copy purposes from a Cloud Store in Amazon S3, perform the following steps:



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

4.  Prepare the container import.

    > ### Note:  
    > The target system should be the same Cloud version as the source system \(or more recent\), and the target HDI container must already exist, or be created before the import operation. If the target HDI container is not empty, the content is overwritten.

    Working with the HDI container API, open an SQL console and connect to the target system as an HDI container administrator user.

5.  Set up any required dependencies and privileges.

    All external objects referenced by design-time objects in the imported container \(as well as the remote container\(s\) in which the external objects are located\) must already be available in the target database and accessible to the object owner of the imported container when the import operation starts. So, if necessary, grant the object owner <code><i class="varname">&lt;ContainerName&gt;</i>#OO</code> of the imported container any privileges required for access to the external objects in any remote containers.

    > ### Note:  
    > If remote container "C3" exposes a role for enabling cross-container access, this role must be granted to the dependent container "C2"’s user `C2#OO`. The role can be granted to user `C2#OO` either by a role administrator \(`ROLE ADMIN`\) or by using the HDI Container API for role assignment.
    > 
    > If remote container "C3" does not expose a role, the required privileges must be granted to the dependent container "C2"’s user `C2#OO` by other means, for example, using the HDI Container API for granting schema privileges.

6.  Import the container

    > ### Note:  
    > If the HDI container you want to import \(for example, container C2\) has dependencies to objects in another container \(for example, container C3\), then you need to import the other container \(C3\) first and set up any required privileges, as described above.

    Working with the HDI container API, call the container's `IMPORT_CONTAINER_FOR_COPY` procedure with the Cloud path you generated in a previous step, as illustrated in the following example:

    Working with the HDI **Container** API, open an SQL console and run the following SQL code:

    ```
    CREATE LOCAL TEMPORARY COLUMN TABLE #PARAMETERS LIKE _SYS_DI.TT_PARAMETERS; 
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('source_path', 's3-<region>://<access_key>:<secret_key>@<bucket_name>/<object_id>');
    INSERT INTO #PARAMETERS (KEY, VALUE) VALUES ('original_container_name', '<CONTAINER_NAME>'); 
    CALL <TARGET_CONTAINER_NAME>#DI.IMPORT_CONTAINER_FOR_COPY('', '', #PARAMETERS, ?, ?, ?);
    DROP TABLE #PARAMETERS;
    ```

    > ### Tip:  
    > Check that the first integer result is 0, which indicates success. One of the results is also a log with further information.

7.  Confirm that the container now has all the data from the source system.


**Related Information**  


[Importing and Exporting with Amazon S3 \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/41d9c51cc69a4178b01db4bda77fb94a.html)

[Importing and Exporting with Azure Storage \(SAP HANA Cloud Admin Guide\)](https://help.sap.com/viewer/f9c5015e72e04fffa14d7d4f7267d897/latest/en-US/fd45a3b7917349a1a8cbc81e202c5cdd.html)

[Export an SAP HDI Container for Copy Purposes to a Cloud Store](export-an-sap-hdi-container-for-copy-purposes-96d3500.md "An HDI container administrator can export an HDI container to a table or a file, which can then be used to import the container into a Cloud Store.")

