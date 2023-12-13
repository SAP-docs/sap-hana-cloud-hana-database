<!-- loioa4bbc2dd8a20442387dc7b706e8d3070 -->

# Deployment Options in HDI

A list of options for configuring custom deployment scenarios with SAP HDI.



<a name="loioa4bbc2dd8a20442387dc7b706e8d3070__section_btj_yb5_sjb"/>

## Usage

The following example shows how to provide interactive options for the Node.js-based HDI deployer `@sap/hdi-deploy`:

> ### Output Code:  
> ```
> node deploy --<option> [<component> [<component> [...]]]
> ```

> ### Tip:  
> Interactive deployment options can also be passed to `@sap/hdi-deploy` using the environment variable `HDI_DEPLOY_OPTIONS`.

The following example shows how the environment variable `HDI_DEPLOY_OPTIONS` requires deployment options in JSON format:

```
{ "verbose" : true, "exit" : true, "include_filter" : [ "src/", "cfg/" ] }; 
```

For more information about setting HDI deployment options in an application's central MTA deployment descriptor \(`MTA.yaml`\) or MTA extension descriptor \(`myMTAextension.mtaext`\), for example, using the property `HDI_DEPLOY_OPTIONS:`, see *Related Information* below.



<a name="loioa4bbc2dd8a20442387dc7b706e8d3070__section_ctj_yb5_sjb"/>

## Deployment Options

The following table lists the options supported by the HDI deployer \(`@sap/hdi-deploy`\) for the configuration of interactive deployment scenarios, for example, for orchestration using SAP Web IDE Full-Stack or continuous integration \(CI\) scripts.

> ### Tip:  
> Options can also be passed to `@sap/hdi-deploy` by means of the `HDI_DEPLOY_OPTIONS` environment variable.


<table>
<tr>
<th valign="top">

Option

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`--version` 

</td>
<td valign="top">

Show the version of the currently installed HDI deployer and exit

</td>
</tr>
<tr>
<td valign="top">

`-t, --trace` 

</td>
<td valign="top">

Enable tracing

</td>
</tr>
<tr>
<td valign="top">

`--use-hdb` 

</td>
<td valign="top">

Enable the `hdb` client to connect to the database instead of `@sap/hana-client`; by default, the `@sap/hana-client` is used

</td>
</tr>
<tr>
<td valign="top">

`--hana-client-trace` 

</td>
<td valign="top">

Enable tracing for the SAP HANA client.

> ### Note:  
> Enabling this option means that **all** interactions with the SAP HANA server will be traced, which can lead to a large amount of trace information being written.



</td>
</tr>
<tr>
<td valign="top">

`--hana-client-packet-trace` 

</td>
<td valign="top">

Enable `PACKET` tracing for the SAP HANA client.

> ### Note:  
> This option must only be used in combination with `--hana-client-trace`.



</td>
</tr>
<tr>
<td valign="top">

`--[no-]verbose` 

</td>
<td valign="top">

\[Do not\] print detailed log messages to the console

</td>
</tr>
<tr>
<td valign="top">

<code>--structured-log <i class="varname">&lt;file&gt;</i></code> 

</td>
<td valign="top">

Write log messages as JSON objects into the given file. If the log file already exists, messages are appended.

</td>
</tr>
<tr>
<td valign="top">

`--[no-]exit` 

</td>
<td valign="top">

\[Do not\] exit after deployment of artifacts

</td>
</tr>
<tr>
<td valign="top">

`--[no-]lock-container` 

</td>
<td valign="top">

\[Do not\] acquire the container lock while working with the container

</td>
</tr>
<tr>
<td valign="top">

<code>--root <i class="varname">&lt;path&gt;</i></code> 

</td>
<td valign="top">

Use the given root path for artifacts

</td>
</tr>
<tr>
<td valign="top">

<code>--working-set [<i class="varname">&lt;path&gt;</i> ...]</code> 

</td>
<td valign="top">

Define the given paths \(directories and files\) as the working set; a non-default working set applies additional restrictions, for example, other options might be disallowed

</td>
</tr>
<tr>
<td valign="top">

<code>--include-filter [<i class="varname">&lt;path&gt;</i> ...]</code> 

</td>
<td valign="top">

Only include the given paths \(directories and files\) during delta detection

</td>
</tr>
<tr>
<td valign="top">

<code>--deploy [<i class="varname">&lt;file&gt;</i> ...]</code> 

</td>
<td valign="top">

Explicitly schedule the given files for deployment and extends the include-filter for collecting local files. Instead of a real path, a path pattern like `src/**/*.hdbtable` can be used as well.

</td>
</tr>
<tr>
<td valign="top">

`--[no-]treat-unmodified-as-modified` 

</td>
<td valign="top">

\[Do not\] treat unmodified files during delta detection as modified files

</td>
</tr>
<tr>
<td valign="top">

<code>--undeploy [<i class="varname">&lt;file&gt;</i> ...]</code> 

</td>
<td valign="top">

Explicitly schedule the given files for undeployment

</td>
</tr>
<tr>
<td valign="top">

<code>--parameter [<i class="varname">&lt;key&gt;</i>=<i class="varname">&lt;value&gt;</i>&gt; ...]</code> 

</td>
<td valign="top">

Pass the given list of key-value parameters to the deployment

</td>
</tr>
<tr>
<td valign="top">

<code>--path-parameter [<i class="varname">&lt;path&gt;</i>:<i class="varname">&lt;key&gt;</i>=<i class="varname">&lt;value&gt;</i> ...]</code> 

</td>
<td valign="top">

Pass the given list of **path** key-value parameters to the deployment

</td>
</tr>
<tr>
<td valign="top">

`--[no-]auto-undeploy` 

</td>
<td valign="top">

\[Do not\] undeploy artifacts automatically based on delta detection and ignore the `undeploy.json` file

</td>
</tr>
<tr>
<td valign="top">

`--[no-]treat-warnings-as-errors` 

</td>
<td valign="top">

\[Do not\] treat warnings as errors

</td>
</tr>
<tr>
<td valign="top">

`--[no-]simulate-make` 

</td>
<td valign="top">

\[Do not\] simulate the `make`, and skip post-`make` activities; pre-`make` activities still take effect, for example, grants

</td>
</tr>
<tr>
<td valign="top">

<code>--connection-timeout <i class="varname">&lt;ms&gt;</i></code> 

</td>
<td valign="top">

The number of milliseconds to wait for the database connection\(s\) to succeed

</td>
</tr>
<tr>
<td valign="top">

<code>--delete-timeout <i class="varname">&lt;ms&gt;</i></code> 

</td>
<td valign="top">

The number of milliseconds to wait for the `DELETE` call

</td>
</tr>
<tr>
<td valign="top">

<code>--write-timeout <i class="varname">&lt;ms&gt;</i></code> 

</td>
<td valign="top">

The number of milliseconds to wait for the `WRITE` call

</td>
</tr>
<tr>
<td valign="top">

<code>--lock-container-timeout <i class="varname">&lt;ms&gt;</i></code> 

</td>
<td valign="top">

The number of milliseconds to wait for the container lock to be released

</td>
</tr>
<tr>
<td valign="top">

<code>--exclude-filter [<i class="varname">&lt;path&gt;</i> ...]</code> 

</td>
<td valign="top">

Exclude the given paths during: file walk, delta detection and when explicitly scheduled using `--(un)deploy` 

> ### Tip:  
> The exclude filter works like \(and can be used either in place of or in combination with\) the `.hdiignore` file, whose content is similar in structure to the `.gitignore` file. Like the `undeploy.json` file, the `.hdiignore` file must be located in the root folder of the project.



</td>
</tr>
<tr>
<td valign="top">

`--[no]-optimise-file-upload` 

</td>
<td valign="top">

\[Do not\] perform delta detection by means of local SHA256 calculation instead of `DELETE` and `WRITE` calls. Will not have any positive effect when used along with `--treat-unmodified-as-modified`.

</td>
</tr>
<tr>
<td valign="top">

`--[no-]treat-wrong-ownership-as-errors` 

</td>
<td valign="top">

\[Do not\] treat wrong ownership of objects as errors

> ### Note:  
> Default: Not enabled.



</td>
</tr>
<tr>
<td valign="top">

`--[no-]migrationtable-development-mode` 

</td>
<td valign="top">

\[Do not\] pass the development mode flag for migration tables to HDI, if the parameter is supported by the server

> ### Note:  
> Default: Not enabled.



</td>
</tr>
<tr>
<td valign="top">

`--[no-]liveness-ping` 

</td>
<td valign="top">

\[Do not\] send a sign of life \(availability\) at a specified interval

> ### Note:  
> Default: Send a sign of availability



</td>
</tr>
<tr>
<td valign="top">

`--[no-]live-messages` 

</td>
<td valign="top">

\[Do not\] display the `make` messages while the `make` operation is still in progress.

> ### Note:  
> Default: Display `make` messages during the `make` operation.



</td>
</tr>
</table>



<a name="loioa4bbc2dd8a20442387dc7b706e8d3070__section_p4p_slv_zjb"/>

## Environment Variables for HDI Configuration

You can use environment variables to configure the HDI Deployer, `@sap/hdi-deploy`, for example, for use by applications or for infrastructure or development tools such as the deploy service or the internal build tools used by the SAP Web IDE Full-Stack.



### HDI Environment Variables for Applications

You can configure the Node.js module `@sap/hdi-deploy` to use the following environment variables which are exposed to applications, for example, in the the MTA development descriptor \(`mta.yaml`\) or Cloud Foundry manifest \(`manifest.yml`\):

-   `TARGET_CONTAINER`:

    \(optional\) The service name that specifies the HDI target container. This name is required if more than one HDI service is bound to the HDI deployer.

-   `SERVICE_REPLACEMENTS`:

    \(optional\) A list of service replacements structured as JSON, for example, `[ { "key": "logical-service-name-1", "service":"real-service-name-1"}, { "key": "logical-service-name-2", "service":"real-service-name-2"} ]`, where the logical service names refer to the names in the HDI content, and the real service names refer to the services which are bound to the HDI deployer in `VCAP_SERVICES`. Note that if the HDI content references a service name which is not listed in the replacements, then this name is used as a real service name.


The structure of the `SERVICE_REPLACEMENTS` environment variable is based on the MTA specification in order to enable MTA group assignments.

> ### Sample Code:  
> Example `manifest.yml` File
> 
> ```
> applications:
> - name: app-db 
>   path: db 
>   health-check-type: process 
>   services: 
>     - app-database 
>     - real-grantor-service 
>     - real-external-service 
>   env: 
>     TARGET_CONTAINER: app-database 
>     SERVICE_REPLACEMENTS: > 
>     [ 
>       { 
>         "key" : "logical-grantor-service", 
>         "service" : "real-grantor-service" 
>       }, 
>       { 
>         "key" : "logical-external-service", 
>         "service" : "real-external-service" 
>       }
>      ]
> ```



### Environment Variables for HDI Infrastructure and Development Tools

The following variables can be used to configure the HDI deployment infrastructure and development tools such as the SAP Web IDE Full-Stack


<table>
<tr>
<th valign="top">

Variable

</th>
<th valign="top">

Description

</th>
<th valign="top">

Comments

</th>
</tr>
<tr>
<td valign="top">

`EXIT` 

</td>
<td valign="top">

If set, the HDI Deployer exits when the deployment is completed.

> ### Tip:  
> Using the `EXIT` environment variable is equivalent to passing the option `--exit` on the command line.



</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`DEPLOY_ID` 

</td>
<td valign="top">

If set, the given deployment ID will be written to the final application log entry \(custom ID, to support processes in parsing log output\)

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`HDI_DEPLOY_OPTIONS` 

</td>
<td valign="top">

A JSON-structured set of options for the HDI Deployer, for example:

```
{ "auto_undeploy" : true, 
  "exit" : true, 
  "root" : "/volumes/A/workspaces/B/db/", 
  "include_filter" : [ "src/", "cfg/" ] 
};
```

Command line options can be translated to `HDI_DEPLOY_OPTIONS` options by replacing the “*\-s*” in the option names with “*\_s*”. Options which can accept multiple values require a JSON array with the required values, for example, path options such as `include-filter`.

> ### Note:  
> Options defined in `HDI_DEPLOY_OPTIONS` override any options that are passed on the command line.



</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`APPLICATION_ID` 

</td>
<td valign="top">

Used in conjunction with the `space_name` and the `organization_name` of the *<VCAP\_APPLICATION\>* to set the session variable *<APPLICATION\>* for all connections to the database.

> ### Note:  
> The `APPLICATION_ID` setting can only be used by applications from SAP.



</td>
<td valign="top">

Optional, fallback = `SAP_HDI` 

</td>
</tr>
<tr>
<td valign="top">

`APPLICATION_VERSION_INFO` 

</td>
<td valign="top">

Logged to the command line, to allow logging of some additional information about the application.

</td>
<td valign="top">

Optional

</td>
</tr>
</table>



<a name="loioa4bbc2dd8a20442387dc7b706e8d3070__section_orr_5ym_hvb"/>

## Dynamic Deployment

Based on `@sap/hdi-deploy`, the Node.js module `@sap/hdi-dynamic-deploy` provides a Node.js-based HTTP server that can be used to deploy database content to dynamically created HDI containers, for example, containers created by means of the Instance Manager. The HDI dynamic deployer is intended for use in both on-premise and Cloud scenarios.

> ### Note:  
> For more information about the HDI dynamic deployer, see *Related Information* below.

**Related Information**  


[Configuring the HDI Deployer](configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

[The SAP HDI Deployer](the-sap-hdi-deployer-1b567b0.md "SAP HDI provides dedicated tools to enable the deployment of design-time database artifacts to the SAP HANA database.")

[@sap/hdi-dynamic-deploy \(NPM Repository\)](https://www.npmjs.com/package/@sap/hdi-dynamic-deploy)

[The MTA Deployment Descriptor](../030-HANA-Cloud-DB-Dev-Deployment/the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

[The MTA Deployment Extension Descriptor](../030-HANA-Cloud-DB-Dev-Deployment/the-mta-deployment-extension-descriptor-51ac525.md "Provide system-specific details that are not known until deployment time.")

