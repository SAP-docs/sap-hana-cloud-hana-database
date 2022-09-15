<!-- loio5e638d4f297b4be2a51086c1d1e34202 -->

# Define Run-Time Name-Space Rules for SAP HDI

Define rules for run-time name spaces in SAP HANA Deployment Infrastructure \(HDI\) containers.



## Prerequisites

For the definition and deployment of name space rules for run-time container objects in SAP HDI, the following prerequisites apply:

-   The design-time folder hierarchy contains application artifacts
-   The design-time containers exist
-   The corresponding run-time containers exist



## Context

In SAP HANA Deployment Infrastructure \(HDI\), the application objects deployed to an HDI container must also be assigned to a run-time name space, which is defined in the `.hdinamespace` file.



<a name="loio5e638d4f297b4be2a51086c1d1e34202__steps_tk5_s2g_bt"/>

## Procedure

1.  Create the name-space configuration file \(`.hdinamespace`\) in the design-time location of your choice.

    Design-time database objects are typically located in the `db/` folder of the application's design-time hierarchy, as illustrated in the following example:

    > ### Output Code:  
    > ```
    > app1-hello-world
    > |- db
    >    \- src
    >       |- .hdiconfig                       # HDI build-plugin configuration
    >       |- .hdinamespace                    # Run-time name-space configuration
    >       |- myTable.hdbtable                 # DB table definition
    >       |- mySQLView.hdbview                # SQL view definition
    >       |- mySynonym.hdbsynonym             # DB synonym definition
    >       |- mySynoConfig.hdbsynonymconfig    # DB synonym configuration file
    >       |- myProcedure.hdbprocedure         # DB procedure definition
    >       \- myImportData.hdbtabledata        # Data-import definition
    > ```

    > ### Note:  
    > If you are using the SAP HDI API to create content, you first use the `WRITE` API to create the `.hdinamespace` in the HDI container's "work" file system and then deploy the name-space configuration to the "deployed" file system of the same HDI container, for example, with the `MAKE` command as described below.

2.  Configure the run-time name spaces for the objects added to the run-time container during application deployment.

    In SAP HANA, name-space rules are defined in one or more file resources named `.hdinamespace`, which must be located in the design-time folder to which the naming rules apply - or the root folder of a hierarchy to which the naming rules apply. The content of the `.hdinamespace` file is specified according to the JSON format with the following structure:

    > ### Sample Code:  
    > `src/.hdinamespace`
    > 
    > ```
    > {
    >    "name"      : "com.sap.hana.example",
    >    "subfolder" : "<[append | ignore]>"
    > }
    > 
    > ```

    > ### Tip:  
    > Change the path defined in `name` and, for `subfolder`, choose between `append` \(add sub-folder name to object name space\) and `ignore` \(do **not** add sub-folder name to the object name space\).

3.  Deploy the name-space configuration to the container where the rules apply.

    The deployment operation pushes the specified application's database objects to the HDI container to which it is bound.

    -   Command-line interface:

        `cf deploy`

    -   HDI SQL API

        To deploy the newly created files with the HDI `MAKE` API, you must provide the file name in the `PATH` parameter.

        > ### Restriction:  
        > This step requires the privileges of an HDI container administrator. Only files can be deployed; it is not possible to deploy folders.

        > ### Sample Code:  
        > Deploy Files to the Work File System of Container "C"
        > 
        > ```sql
        > CREATE LOCAL TEMPORARY COLUMN TABLE #DEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
        > INSERT INTO #DEPLOY_PATHS (PATH) VALUES ('.hdinamespace');
        > CREATE LOCAL TEMPORARY COLUMN TABLE #UNDEPLOY_PATHS LIKE _SYS_DI.TT_FILESFOLDERS;
        > CREATE LOCAL TEMPORARY COLUMN TABLE #PATH_PARAMETERS LIKE _SYS_DI.TT_FILESFOLDERS_PARAMETERS;
        > CALL C#DI.MAKE(#DEPLOY_PATHS, #UNDEPLOY_PATHS, #PATH_PARAMETERS, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
        > DROP TABLE #DEPLOY_PATHS;
        > DROP TABLE #UNDEPLOY_PATHS; 
        > DROP TABLE #PATH_PARAMETERS; 
        > ```



**Related Information**  


[The HDI Name-Space Configuration File](the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[The SAP HDI Name-space Configuration Syntax](the-sap-hdi-name-space-configuration-syntax-c38cbef.md "In SAP HANA Deployment Infrastructure (HDI), the contents of the .hdinamespace file are formatted with the JSON syntax")

