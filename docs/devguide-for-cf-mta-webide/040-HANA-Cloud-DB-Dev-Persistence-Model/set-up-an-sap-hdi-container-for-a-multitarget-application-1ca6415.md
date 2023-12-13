<!-- loio1ca64155ec5a465294e0d8b10383cea8 -->

# Set up an SAP HDI Container for a Multitarget Application

Set up the environment required for the deployment to the SAP HANA Deployment Infrastructure \(HDI\) of a multitarget application's database artifacts.



## Context

In SAP HDI, the design-time artifact types for multitarget applications are distinguished by the artifact's file suffix \(for example, `.hdbtable` or `.hdbview`\). These artifact types must be associated with a corresponding build plug-in to ensure the successful build and deployment. The binding between an artifact type and a corresponding build plug-in is established by the contents of the `.hdiconfig` file, which must be deployed into the target container, too.

In the context of Cloud Foundry, the service broker is used to create HDI containers for the deployed application. An HDI container is a set of schemata and a set of users that, together, enable an isolated deployment of database artifacts. From an application perspective, it is just a technical user and a schema.

For backward compatibility with legacy applications, the deployed objects can also be assigned to a run-time name space, which is defined in the `.hdinamespace` file that also has to be deployed to the target HDI container.

> ### Tip:  
> If you are using *SAP Web IDE Full-Stack*, the configuration described here is available by default. If you are working in a command shell, use the `cf` command \(SAP Cloud Foundry\) in the following steps.



## Procedure

1.  Check that the HDI service plan `hdi-shared` is available for your organization or space.

    ```sh
    cf marketplace
    
    Getting services from marketplace...
    
    service       plans                                  description
    ---------------------------------------------------------------------------------
    hana          hdi-shared, schema, securestore  SAP HANA database
    xsuaa         space, application, apiaccess          Manage app authorization...
    ...
    ```

2.  Create an HDI container using the service broker.

    <code>cf create-service hana hdi-shared <i class="varname">&lt;myHDIcontainer&gt;</i></code>

3.  Bind the new HDI container to the application that you want to use the container.

    <code>cf bind-service <i class="varname">&lt;myApplication&gt;</i> <i class="varname">&lt;myHDIcontainer&gt;</i></code>

4.  Configure the build plug-ins required for the artifacts deployed to the HDI container.

    By default, a file suffix \(for example, `.hdbprocedure`\) is not bound to a specific version of a build plug-in. Instead, the binding is established by the contents of the `.hdiconfig` file, which must be deployed into a container along with the database artifacts it lists. An `.hdiconfig` file is a JSON file with the structure illustrated in the following example:

    > ### Sample Code:  
    > Example `.hdiconfig` File
    > 
    > ```json
    > {
    > "plugin_version": "2.0.30.0"
    > "file_suffixes" : {
    >     "hdbtable" : { 
    >         "plugin_name" : "com.sap.hana.di.table"},
    >     "hdbview" : { 
    >         "plugin_name" : "com.sap.hana.di.view"},
    >     "hdbprocedure" : { 
    >         "plugin_name" : "com.sap.hana.di.procedure"},
    >     "<hdb_file_suffix_#>" : {
    >         "plugin_name"   : "<plugin_NAME>",
    >         "plugin_version": "<local_plugin_VERSION>"}
    >     }
    > }
    > ```

    > ### Tip:  
    > Add to the `.hdiconfig` file, the file-suffixes of the design-time artifacts deployed by your applications. The `.hdiconfig` file must be placed in the root folder of the database source-files, for example, `app1/db/.hdiconfig`.

5.  Configure the run-time name spaces for the objects added to the run-time container during application deployment.

    In SAP HANA HDI, name-space rules are defined in one or more file resources named `.hdinamespace`, which must be located in the design-time folder to which the naming rules apply - or the root folder of a hierarchy to which the naming rules apply. The content of the `.hdinamespace` file is specified according to the JSON format with the following structure:

    > ### Tip:  
    > Change the path defined in `name` and, for `subfolder`, choose between `append` \(add sub-folder name to object name space\) and `ignore` \(do **not** add sub-folder name to the object name space\).

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

6.  Deploy the application.

    The deployment operation pushes the specified application's database objects to the HDI container to which it is bound.

    -   Command-line interface:

        `cf deploy`

    -   SAP Web IDE Full-Stack:

        *Build* \> *Build*

        > ### Note:  
        > You can use the *Database Explorer* tool to view the contents of the application's run-time container.



**Related Information**  


[The SAP HDI Container Configuration File](the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[SAP HDI Container Configuration File Syntax](sap-hdi-container-configuration-file-syntax-c1df57a.md "In SAP HANA Deployment Infrastructure (HDI), the JSON syntax is used to format the content of the HDI container-configuration file (.hdiconfig).")

[SAP HDI Artifact Types and Build Plug-ins Reference](https://help.sap.com/viewer/c2cc2e43458d4abda6788049c58143dc/2023_4_QRC/en-US/9789224788a34d93a86080cab993575c.html "The SAP HANA Cloud, SAP HANA database deployment infrastructure (HDI) supports a wide variety of database artifact types, for example, tables, indexes, and views.") :arrow_upper_right:

[Managing SAP HDI Containers and Artifacts](managing-sap-hdi-containers-and-artifacts-23f1f40.md "In SAP HANA Deployment Infrastructure (HDI), database development artifacts are deployed to so-called containers.")

