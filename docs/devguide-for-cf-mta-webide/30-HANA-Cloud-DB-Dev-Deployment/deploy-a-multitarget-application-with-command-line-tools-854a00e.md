<!-- loio854a00eb1193486383fc4a97b998dabd -->

# Deploy a Multitarget Application \(with Command-Line Tools\)

Install a multi-target application \(MTA\) on SAP HANA Cloud.



## Prerequisites

Deploying a multitarget application \(MTA\) to SAP HANA Cloud requires **some or all** of the following components and tools; which components or tools you need depends on what you are deploying: an MTAR archive or a folder structure:

-   A file system containing the source files for the multi-target application you want to deploy

-   A deployment description for the multitarget application; the mandatory file name is `mtad.yaml`

-   An optional deployment description **extension** for the multitarget application deployment description, for example, `myMTADeploymentExtension.mtaext`

-   An application's archive manifest `MANIFEST.MF`: required only if you create the MTAR deployment archive manually, for example, with the `jar` command

-   An MTA archive, for example, `MTApp-Name.mtar` \(optional\)

-   Knowledge of the `cf deploy` command as well as its parameters and options




## Context

To deploy a multitarget application \(MTA\) to SAP HANA using the `cf` command-line tools, perform the following steps:



## Procedure

1.  Navigate to the parent folder of the file-system containing the application that you want to deploy.

2.  Create a deployment descriptor \(`mtad.yaml`\) for your multitarget application.

    > ### Note:  
    > This step is not necessary if you plan to use the Cloud MTA Build Tool \(MBT\) to create the deployment archive. The Cloud MBT generates the deployment descriptor \(`mtad.yaml`\) from the development descriptor \(`mta.yaml`\).

3.  Create an application manifest file \(`MANIFEST.MF`\) for the multitarget application.

    > ### Note:  
    > This step is not necessary if you plan to use the Cloud MTA Build Tool \(MBT\) to create the deployment archive.

4.  Create an MTA archive.

    If you want to deploy a folder structure \(including all sub-folders\), you can skip this step.

    > ### Restriction:  
    > The MTA archive **must** have the extension `.mtar`, for example, `myMTApp.mtar`.

    1.  Change directory to the parent folder containing **all** the application modules that you want to deploy.
    2.  Create an MTA archive \(MTAR\) that contains the complete MTA folder structure \(including all sub-folders\).

        To create the MTA archive, you can use the following tools:

        -   The Cloud MTA Build Tool \(MBT\); for more information, see *Related Information*
        -   Java's `jar` command, for example:

            <code>jar cvMf <i class="varname">&lt;myMTApp&gt;</i>.mtar -C <i class="varname">&lt;myMTApp&gt;</i> .</code>

        -   Any archiving tool that produces Zip output


5.  Deploy the multitarget application to SAP HANA Cloud.

    You can use either of the following deployment methods:

    -   Deploy a **file system** \(or part thereof\) that includes MTA modules and the MTA deployment descriptor \(`mtad.yaml`\):
        1.  Change directory to the folder containing the application you want to deploy.
        2.  Use the `cf deploy` command to deploy the complete MTA folder structure \(including all sub-folders\) to the default target SAP HANA container.

            <code>cf deploy <i class="varname">&lt;relative/path/to/MTA_folder&gt;</i></code>


    -   Deploy an **MTA archive**, which you create using Zip \(or Java\) tools:
        1.  Use the `cf deploy` command to deploy the MTAR archive.

            <code>cf deploy <i class="varname">&lt;myMTApp_Name&gt;</i>.mtar</code>

        2.  Check the MTA was successfully deployed.

            The information printed to the console should indicate the successful completion of the deployment process, as illustrated in the following example.

            > ### Output Code:  
            > ```
            > ...
            > Upload finished successfully
            > Starting process cf-deploy ...
            >  Processing MTA archive...
            >  MTA archive processed successfully.
            >  Building model...
            >  ...
            > Process finished successfully
            > ```



    > ### Tip:  
    > If your deployment requires system-specific information that is only available at deployment time, you can include the information in a so-called MTA deployment **extension**. The file containing the extension details can then be specified as a deployment parameter, for example, <code>cf deploy --archive <i class="varname">&lt;myMTApp_Name&gt;</i>.mtar -e myMTADeploymentExtension.mtaext</code>

6.  Check the deployment results.

    You can check that an MTA was successfully deployed by listing the corresponding services and applications and accessing the deployed application at the assigned URL.

    1.  Log on to the CF controller.

        > ### Sample Code:  
        > ```
        > cf login -a https://<hana-host>.hana.ondemand.com
        > ```

        > ### Note:  
        > You will need to provide a user name and password to log in to Cloud Foundry, as well as the name of the target organization and space you want to use.

    2.  List all running services.

        > ### Sample Code:  
        > ```
        > cf services
        > ```

        You should see the HDI service instance used by the application \(for example, ***nodejs-hdi-container***\), and also the UAA service instance \(for example, ***nodejs-uaa***

        > ### Output Code:  
        > ```
        > cf services
        > name                     service  plan         bound apps
        > -------------------------------------------------------------------------------
        > ...
        > hdi-container            hana     hdi-shared
        > ...
        > nodejs-hdi-container     hana     hdi-shared   node-hello-world-db, node-hello...
        > nodejs-uaa               xsuaa    application  node-hello-world-backend, node-hello...
        > ...
        > 
        > ```

    3.  List all applications.

        > ### Sample Code:  
        > ```
        > cf apps
        > ```

        A list of applications is displayed showing all applications that are part of the deployed MTA, for example, ***node-hello-world-db***, ***node-hello-world-backend***, and ***node-hello-world***. The status of the `db` application should be ***STOPPED***; the status of the other applications should be ***STARTED***. The `db` application is stopped by the deployment process after the HDI deployment finishes, to prevent it from wasting resources.

        > ### Output Code:  
        > ```
        > cf apps
        > name                       requested state   instances   memory   [...]
        > -----------------------------------------------------------------------
        > hdi-broker                 STARTED           1/1         256 MB   [...]
        > uaa-security-db            STARTED           1/1         256 MB   [...]
        > uaa-security               STARTED           1/1         2.00 GB  [...]
        > deploy-service             STARTED           1/1         512 MB   [...] 
        > node-hello-world-db        STOPPED           0/1         256 MB   [...]
        > node-hello-world-backend   STARTED           1/1         256 MB   [...]
        > node-hello-world           STARTED           1/1         256 MB   [...]
        > 
        > ```

    4.  List all deployed MTAs.

        > ### Sample Code:  
        > ```
        > cf mtas
        > ```

        You should see the MTA that you just deployed, for example, ***com.sap.xsa.samples.nodehelloworld***.

    5.  Display the URL assigned to application.

        > ### Sample Code:  
        > ```
        > cf app <AppName>
        > ```

        With the correct logon credentials, you should be able to access the deployed application.



**Related Information**  


[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

[The MTA Deployment Extension Descriptor](the-mta-deployment-extension-descriptor-51ac525.md "Provide system-specific details that are not known until deployment time.")

[The Cloud MTA Build Tool \(MBT\)](the-cloud-mta-build-tool-mbt-1412120.md "A new tool for building deployment archives for multitarget applications (MTA).")

