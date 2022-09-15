<!-- loio424a70b12c3d42809e777591813e3703 -->

# Set up a Multitarget Application Project

An overview of the steps required to set up and deploy a multitarget application project for Cloud Foundry on SAP Business Technology Platform \(BTP\).



## Prerequisites

-   Development tools

    You can choose between graphical and command-line tools:

    -   SAP Web IDE Full-Stack

        *SAP Web IDE Full-Stack* is available as a service to users logged on to SAP BTP cockpit. To work with SAP Web IDE Full-Stack, the user must also be assigned the role `DiDeveloper`. For more information, see *Related Information* below.

    -   You have installed the Cloud Foundry \(CF\) command-line client on your development machine.

        The CF CLI client tools must be installed locally, if you want to connect to SAP HANA Cloud from your local machine. You will also need the MultiApps plug-ins package for multitarget applications. For more information about where to find the CF CLI client tools, see *Related Information* below.

    -   SAP Node.js packages

        You need to configure NPM to resolve SAP-scoped NPM dependencies \(`@sap/package`\), for example, using the public NPM registry at `https://registry.npmjs.org`. For more information, see *Related Information* below.


-   You have access to a running SAP BTP system where the CF run time is installed and configured.


> ### Caution:  
> The code examples included in this document for CF are often syntactically incomplete; they are intended for illustration purposes only.



## Context

The end-to-end process of developing an application that you want to deploy on SAP HANA Cloud is illustrated in the steps described in this high-level overview.

<a name="loio424a70b12c3d42809e777591813e3703__table_y4c_kk2_vt"/>Application Development Overview


<table>
<tr>
<th valign="top">

Step



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

 [Create the design-time folder infrastructure for your application source files](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_e45_fk2_vt) 



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

 [Create the deployment descriptor files for your application](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_zsx_zk2_vt) 



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

 [Add database artifacts and content](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_t1k_1l2_vt) 



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

 [Add application business logic to work with the database artifacts](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_b4p_1l2_vt) 



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

 [Create any required OData service definitions](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_ljz_1l2_vt) 



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

 [Create the user interface in which to display the database content](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_fbf_bl2_vt) 



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

 [Add security to protect what you have built](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_anm_bl2_vt) 



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

 [Define application routes \(and destinations\)](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_szx_bl2_vt) 



</td>
</tr>
<tr>
<td valign="top">

9



</td>
<td valign="top">

 [Create any service instances needed by your application](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_tvj_qwn_wt) 



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

 [Deploy your project](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_wss_cl2_vt) 



</td>
</tr>
<tr>
<td valign="top">

11



</td>
<td valign="top">

 [Test your project in the user interface](set-up-a-multitarget-application-project-424a70b.md#loio424a70b12c3d42809e777591813e3703__step_kvg_dl2_vt) 



</td>
</tr>
</table>

> ### Note:  
> Some configuration artifacts are subject to restrictions regarding their location; deployment tools **expect** to find particular artifacts in a particular location.



<a name="loio424a70b12c3d42809e777591813e3703__steps_s15_2k2_vt"/>

## Procedure

1.  Create the design-time folder infrastructure for your application source files.

    To make the maintenance of source files easier and facilitate the task of deploying the application, it is also essential to create a clear and consistent structure for the design-time artifacts that you develop for your application. The folders typically include modules for the following areas: database, Web, application code, OData \(optional\). The security description \(OAuth2 client configuration\) can be placed either in its own root-level module or in the application code structure, for example, `js/security/` or `java/security/`.

    > ### Tip:  
    > SAP Web IDE Full-Stack provides Wizards and templates to assist with the creation of application modules and the related resources for your MTA. If you are using the CF command-line tools to develop an MTA, you must create all modules and resources yourself.

    > ### Sample Code:  
    > ```
    > <myAppName>
    > |- db/                             # Database module
    > |  |- package.json                 # Database details/dependencies
    > |  \- src/                         # Database artifacts: tables, views,
    > |     |- .hdiconfig                # HDI plug-in configuration
    > |     |- .hdinamespace             # HDI plug-in namespace configuration (optional)
    > |     |- mytable.hdbtable          # Database design-time definition
    > |     \- myview.hdbtable           # Database design-time view
    > |- js/                             # JavaScript app module 
    > |  |- start.js                     # JavaScript app entry point
    > |  |- package.json                 # JavaScript app details/dependencies
    > |  \- src/                         # JavaScript source code
    > |     \- odata/                    # OData module
    > |        |- resources/             # OData service resources
    > |        \- services/              # OData service definitions
    > |           | - srv1.xsodata       # OData service definition
    > |           \ - srvN.xsodata       # OData service definition
    > |- ui/                             # Application UI module
    > |  |- xs-app.json                  # Application routes configuration
    > |  |- package.json                 # Application details/dependencies
    > |  \- resources/                   # Static UI resources
    > |     \- index.html                # Client UI start page
    > |- xs-security.json                # Application security description
    > |- manifest.yml                    # Manifest description incl. destinations
    > |- mta.yaml                        # Central development manifest (Graphical IDE tools only)
    > \- mtad.yaml                       # Central deployment manifest
    > 
    > ```

2.  Create the development and deployment descriptor files for your application.

    The development and deployment descriptors specify what application components to build \(and how\), the dependencies between the application components, and where \(and how\) to deploy the components. The development and deployment manifest files for the multi-target application must be located in the application's root folder.

    -   `mta.yaml`

        Development manifest for a multi-target application \(MTA\)

        > ### Tip:  
        > The `mta.yaml` is only required if you are working with SAP Web IDE Full-Stack, which creates \(and maintains\) the file automatically when you create a new application project and maintain the project's components.

    -   `mtad.yaml`

        Deployment manifest for a multi-target application \(MTA\)

        > ### Tip:  
        > If you are working with the CF command-line client, you must create \(and maintain\) the `mtad.yaml` file manually. If you are using SAP Web IDE Full-Stack, no action is required; SAP Web IDE Full-Stack creates the deployment manifest `mtad.yaml` transparently at deployment time using the information specified in the corresponding development descriptor \(`mta.yaml`\).


3.  Add database artifacts and content.

    Create database artifacts such as tables and views, for example using native SAP HANA Cloud DDL or SAP CAP Core Data and Services \(CD+S\). You can also create procedures and sequences, for example, using SQLScript.

    > ### Note:  
    > The database content must include a `package.json` file containing details of dependencies and, in addition, the container configuration \(`.hdiconfig`\) and run-time name space configuration \(`.hdinamespace`\) files.

4.  Add application business logic to work with the database artifacts.

    The business logic is used to help retrieve data from the database, for example, using OData services. The data is requested from and displayed in the client user interface.

    For applications written in JavaScript \(Node.js or XS JavaScript\), you need to perform the following high-level steps:

    1.  Add a package description file \(`package.json`\) to your JavaScript resource-files folder with details of your application's contents and dependencies.

    2.  Add a startup file for your JavaScript application, for example, `main.js`.

    3.  Create any additional JavaScript \(`.js` or `.xsjs`\) files and libraries.


    For applications written in Java, you need to perform the following high-level steps:

    1.  Write Java application's code.

    2.  Look up the required data source.

    3.  Build the WAR file based on the project object model file \(`pom.xml`\), for example, with Maven.


5.  Create any required OData service definitions.

    An OData service definition is described in an `xsodata` artifact, for example, `myOdataService.xsodata`; the service definition should be placed in the `resources/` folder of your OData project structure.

6.  Create the user interface \(GUI\) to display the database content \(HTML pages\).

7.  Add security to protect what you have built \(`xs-security.json`\).

    Creates the security descriptor \(`xs-security.json`\) for the application; maintains role templates and authorization scopes \(in the `xs-security.json`\) to define who has access to the application; binds the application to a service instance; deploys the application to the target run-time environment.

8.  Define application routes \(and destinations\).

    The application router is used to serve static content, propagate user information, and act as a proxy to forward requests to other micro services. Application routes are defined in the application-router descriptor `xs-app.json`, a JSON-formatted file that should be located in the application's Web resources module.

    Destinations are defined in an environment variable for the `@sap/approuter` application. The destinations are typically specified in the application manifest \(`manifest.yml`\) file. The router information is added to the `env: destinations` section of the `manifest.yml`, as illustrated in the following example.

9.  Create any service instances needed by your application.

    > ### Note:  
    > SAP Web IDE Full-Stack creates any required services based on the information in the “`resources`” section of the application's development/deployment descriptor \(`mta.yaml`\) and binds the application to the service instance created.
    > 
    > If you are using the Cloud Foundry CLI, you must create any services and manually bind the application to the service instance, for example, using the `cf create-service` and `cf bind-service` commands.

    <code>cf create-service <i class="varname">&lt;SERVICE&gt;</i> <i class="varname">&lt;PLAN&gt;</i> <i class="varname">&lt;SERVICE_INSTANCE&gt;</i></code>

    -   HDI container service instance

        `cf create-service hana hdi-shared my-hdi-container`

    -   User Account and Authentication \(UAA\) service

        Using information specified in the application’s security descriptor \(`xs-security.json`\)

        <code>cf create-service xsuaa default -c <i class="varname">&lt;/path/to/&gt;</i>xs-security.json</code>


10. Deploy your application project.

    1.  Deploy an application to the target run-time environment.

        -   CF CLI client
            -   Push an individual application component/module:

                <code>cf push <i class="varname">&lt;myAppName&gt;</i></code>

            -   Deploy a complete MTA archive:

                <code>cf deploy <i class="varname">&lt;myMTAName&gt;</i>.[mtar | zip]</code>

            -   Install a Software Component Version \(SCV\):

                <code>cf install <i class="varname">&lt;myAppArchive&gt;</i>.zip</code>




11. Test your application project in the user interface.

    On build or deployment, an application is assigned a URL with a specific port. You can paste the assigned URL into a Web browser to test it. This information is displayed differently depending on the tools you are using:

    -   SAP Web IDE Full-Stack

        In the UI, select the application's UI module and, in the context menu, choose *Run* \> *Run as* \> *Web Application*. When the application is up and running, SAP Web IDE Full-Stack displays the URL required to access the application as well as the application's current status at the bottom of the run console in the details pane:

        > ### Tip:  
        > If the application is already running, you do not need to restart it; selecting an application module in the SAP Web IDE project pane displays the URL and status of the application in the run console:

    -   CF CLI

        Displays the ports allocated to applications running in a given run-time space, for example, using the `cf apps` command, as illustrated in the following example:

        > ### Output Code:  
        > ```
        > $>cf apps
        > 
        > Getting apps in org "myorg" / space "DEV" as USER...
        > Found apps:
        > 
        > name                    req. state  instances  memory   disk   urls
        > -----------------------------------------------------------------------------------
        > hdispacedeploy...       STARTED     1/1        1G      1G      hdispacedeploy...
        > app1                    STARTED     1/1        1G      1G      ...hana.ondemand.com
        > app2                    STOPPED     0/1        <none>  <none>  ...hand.ondemand.com
        > ...
        > ```



**Related Information**  


[Open SAP Web IDE Full-Stack](https://help.sap.com/viewer/825270ffffe74d9f988a0f0066ad59f0/CF/en-US/51321a804b1a4935b0ab7255447f5f84.html)

[Install the MultiApps Plug-in in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/27f3af39c2584d4ea8c15ba8c282fd75.html)

[The NPM Registry](../060-HANA-Cloud-DB-Dev-App-Code/the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[Download and Install the Cloud Foundry CLI client](download-and-install-the-cloud-foundry-cli-client-c9f777d.md "Set up the Cloud Foundry Command Line Interface (CLI)")

