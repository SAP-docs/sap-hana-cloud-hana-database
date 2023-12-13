<!-- loioca95868629874225b32c8c05c3ccf7e6 -->

# Set up an SAP HDI Container with the HDI API

Set up the environment required for the deployment to the SAP HANA Deployment Infrastructure \(HDI\) of database artifacts.



<a name="loioca95868629874225b32c8c05c3ccf7e6__prereq_y5r_lrj_kgb"/>

## Prerequisites

To complete this task, bear in mind the following prerequisites:

-   SAP HDI is enabled

-   The SAP HDI administrator has created an SAP HDI **group** administrator

-   The SAP HDI group administrator has created an SAP HDI **container** administrator

-   You can connect to the SAP HANA database where you want to maintain HDI containers.




## Context

In SAP HDI, the design-time artifact types are distinguished by the artifact's file suffix \(for example, `.hdbtable` or `.hdbview`\). These artifact types must be associated with a corresponding build plug-in to ensure that the artifacts can be successfully built and deployed to the run-time environment. The binding between an artifact type and a corresponding build plug-in is defined in the contents of the `.hdiconfig` file, which must be deployed into the target container, too.

For backward compatibility with legacy applications, the deployed objects can also be assigned to a run-time name space, which is defined in the `.hdinamespace` file that also has to be deployed to the target HDI container.



<a name="loioca95868629874225b32c8c05c3ccf7e6__steps_jrs_2rj_kgb"/>

## Procedure

1.  Check that HDI is enabled in your SAP HANA instance and that all necessary administration users are available with the required roles and privileges.

    The `diserver` process must usually be enabled by the database administrator before HDI can be used. If required by the usage scenario, other database process may also need to be started as well. The database administrator SYSTEM is needed for the first-time enabling of HDI in SAP HANA and for creating an HDI administrator; it is the HDI administrator who is then responsible for performing the tasks required to set up and maintain other HDI administrators, for example, container \(and container-group\) administrators.

2.  Create an HDI container group.

    > ### Note:  
    > This step must be performed by a user with the privileges of an HDI administrator.

    To create an HDI container group named "G", run the following SQL code in an SQL console:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI.CREATE_CONTAINER_GROUP('G', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

3.  Create an HDI container.

    > ### Note:  
    > This step must be performed by a user with the privileges of an HDI container-group administrator.

    To create an HDI container named "C" in container group "G", run the following SQL code in an SQL console:

    > ### Sample Code:  
    > ```sql
    > CALL _SYS_DI#G.CREATE_CONTAINER('C', _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > ```

4.  Configure the build plug-ins required for the artifacts deployed to an HDI container.

    By default, a file suffix \(for example, `.hdbprocedure`\) is not bound to a specific version of a build plug-in. Instead, the binding is established by the contents of the `.hdiconfig` file, which must be deployed into a container along with the database artifacts it lists. The `.hdiconfig` file must be placed in the root folder of the database source-files, for example, `myApp/db/.hdiconfig`. The contents of the `.hdiconfig` file must be specified in the JSON format illustrated in the following example; the JSON content is included as `VALUES` for the `CONTENT` parameter in the `INSERT` command shown later in this tutorial:

    > ### Sample Code:  
    > Example `.hdiconfig` File
    > 
    > ```json
    > {
    > "plugin_version" : "4.0.0.0",
    > "file_suffixes" : {
    >     "hdbtable" : { 
    >         "plugin_name" : "com.sap.hana.di.table" },
    >     "hdbview" : {  
    >         "plugin_name" : "com.sap.hana.di.view"},
    >     "hdbprocedure" : { 
    >         "plugin_name" : "com.sap.hana.di.procedure",
    >     "<hdb_file_suffix_#>" : {
    >         "plugin_name"   : "<plugin_NAME>",
    >         "plugin_version": "<optional_plugin_VERSION>" }
    >     }
    > }
    > ```

    > ### Note:  
    > The HDI container administrator can display a list of the build and plug-in libraries currently available in an HDI container \(and the version\) by using the `LIST_CONFIGURED_LIBRARIES` API. The HDI container administrator can also configure a default \(or custom\) set of build and plug-in libraries for an HDI container. For more information, see *Maintaining SAP HDI Containers* in *Related Information*.

5.  Configure the run-time name spaces for the objects added to the HDI run-time container during application deployment.

    In SAP HANA HDI, name-space rules are defined in one or more file resources named `.hdinamespace`, which must be located in the design-time folder to which the naming rules apply or the root folder of a folder hierarchy to which the naming rules apply. The content of the `.hdinamespace` file is specified according to the JSON format with the following structure; the JSON content is included as `VALUES` for the `CONTENT` parameter in the `INSERT` command shown later in this tutorial:

    > ### Sample Code:  
    > `src/.hdinamespace`
    > 
    > ```json
    > {
    >    "name"      : "com.sap.hana.example",
    >    "subfolder" : "<[append | ignore]>"
    > }
    > 
    > ```

    > ### Tip:  
    > Change the path defined in `name` and, for `subfolder`, choose between `append` \(add sub-folder name to object name space\) and `ignore` \(do **not** add sub-folder name to the object name space\).

6.  Write an application's design-time files to the work file system of the target HDI container.

    The following example shows how to use the HDI's `WRITE` API to create design-time content in HDI container C's “work” file system; a file is created by specifying the file name \(with the `PATH` parameter\) and its content \(in the `CONTENT` parameter\) and providing the corresponding data as `VALUES` in the required format:

    > ### Restriction:  
    > This step requires the privileges of an HDI container administrator.

    > ### Sample Code:  
    > Write File Content to the Work File System of Container “C”
    > 
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PATHS LIKE _SYS_DI.TT_FILESFOLDERS_CONTENT;
    > INSERT INTO #PATHS (PATH, CONTENT) VALUES ('.hdiconfig', '{ "plugin_version" : "4.0.0.0", "file_suffixes" : { "hdbtable" : { "plugin_name" : "com.sap.hana.di.table" }, "hdbview" : { "plugin_name" : "com.sap.hana.di.view" }, "hdbprocedure" : { "plugin_name" : "com.sap.hana.di.procedure" } } }');
    > INSERT INTO #PATHS (PATH, CONTENT) VALUES ('.hdinamespace', '{ "name": "", "subfolder": "ignore" }');
    > CALL C#DI.WRITE(#PATHS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #PATHS; 
    > ```

    > ### Note:  
    > In the Cloud, the HDI plug-in version is optional. However, you can use the version number `"4.0.0.0"` to ensure that the plug-ins are only deployable in the Cloud. HDI plug-ins with the version number `"4.0.0.0"` cannot be deployed in an on-premise environment.

7.  Deploy an application's design-time files to the target HDI container.

    The following example shows how to use the HDI's `MAKE` API to deploy design-time content to an HDI container. The deployment operation pushes the specified application's database objects from the “work” file system to the “deployed” file system of the target HDI container \(“C”\). This operation also uses the build plug-in libraries to create the corresponding database objects in the catalog.

    To deploy the newly created files with the `MAKE` API, you must provide the file paths in the `DEPLOY_PATHS` parameter.

    > ### Restriction:  
    > This step requires the privileges of an HDI container administrator. Only files can be deployed; it is not possible to deploy folders.

    > ### Sample Code:  
    > Deploy Files to the "Deployed" File System of Container “C” 
    > 
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #DEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
    > INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('.hdiconfig');
    > INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('.hdinamespace');
    > CREATE LOCAL TEMPORARY COLUMN TABLE #UNDEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
    > CREATE LOCAL TEMPORARY COLUMN TABLE #PATH_PARAMETERS LIKE _SYS_DI.TT_FILESFOLDERS_PARAMETERS;
    > CALL C#DI.MAKE(#DEPLOY_PATHS, #UNDEPLOY_PATHS, #PATH_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #DEPLOY_PATHS;
    > DROP TABLE #UNDEPLOY_PATHS; 
    > DROP TABLE #PATH_PARAMETERS; 
    > ```


**Related Information**  


[Set up an SAP HDI Container for a Multitarget Application](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2023_4_QRC/en-US/1ca64155ec5a465294e0d8b10383cea8.html "Set up the environment required for the deployment to the SAP HANA Deployment Infrastructure (HDI) of a multitarget application's database artifacts.") :arrow_upper_right:

[Maintaining SAP HDI Container Groups](../10-HDI-Cloud-Administration/14-HDI-Cloud-Admin-Maintain-Container-Groups/maintaining-sap-hdi-container-groups-4e9d597.md "The administrator of an SAP HDI container group is responsible for managing the SAP HDI containers that are organized into one or more HDI container groups.")

[Maintaining SAP HDI Containers](../10-HDI-Cloud-Administration/15-HDI-Cloud-Admin-Maintain-Containers/maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[The HDI Container API](the-hdi-container-api-40ba784.md "Maintain HDI containers and container content using the HDI container API.")

