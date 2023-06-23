<!-- loio4050fee4c469498ebc31b10f2ae15ff2 -->

# MTA Deployment Descriptor Syntax

Description of an MTA's deployment-related prerequisites and dependencies.



> ### Note:  
> The following syntax example contains links to more detailed information. Hover the mouse cursor over the property you want to find out about and click the link, if available, to display details of the required syntax.

> ### Sample Code:  
> MTA Deployment Description \(`mtad.yaml`\)
> 
> ```
> ID: com.sap.xs2.samples.nodehelloworld
> version: 0.1.0
> parameters:
>   enable-parallel-deployments: true
> 
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/   # Only for use in mta.yml
>     deployed-after: [ node-hello-world-backend, node-hello-world-db]
>     requires:
>       - name: nodejs-uaa
>       - name: nodejs
>         group: destinations
>         properties:
>           name: backend
>           url: ~{url}
>           forwardAuthToken: true
>         properties-metadata:  
>           name:  
>            optional: false  
>            overwritable: false
>           url:  
>            overwritable: false  
>     parameters:
>       host: !sensitive ${user}-node-hello-world
>       memory: 128MB
>     parameters-metadata:  
>       memory:  
>         optional: true  
>         overwritable: true 
>   - name: node-hello-world-backend
>     type: javascript.nodejs
>     path: js/   # Only for use in mta.yml
>     provides:
>       - name: nodejs
>         properties:
>           url: "${default-url}"
>     requires:
>       - name: nodejs-uaa
>       - name: nodejs-hdi-container
>       - name: node-hello-world-db
>     parameters:
>       host: ${user}-node-hello-world-backend
> 
>   - name: node-hello-world-db
>     type: com.sap.xs.hdi
>     path: db/   # Only for use in mta.yml
>     requires:
>       - name: nodejs-hdi-container
>     parameters:
>         tasks:
>           - name: task-1
>             command: node deploy.js 
>             env: 
>               env1: value1
> 
> resources:
>   - name: nodejs-hdi-container
>     type: com.sap.xs.hdi-container
>     parameters:
>       config:         # Only for use in mtad.yaml
>         schema: ${default-container-name}
>         xsappname: MyAppName01
>     
>   - name: nodejs-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config-path: xs-security.json         # Not for use in mtad.yaml; only in mta.yaml
>   - name: log
>     type: application-logs
>     optional: true
> 
> ```



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_vs1_bhy_xs"/>

## ID

Use the `ID` property to specify a unique identifier for the MTA. For example, the ID could be a reverse-URL dot-notation string that uniquely identifies the run-time namespace of the multi-target application to be deployed.

> ### Code Syntax:  
> ```
> ID: com.acme.mta.samples.javahelloworld
> ```



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_q2l_1hy_xs"/>

## version

Use the `version` property to specify a version of the MTA defined in the `mtad.yaml` deployment descriptor.

The version value must follow the standard format for semantic versioning, for example, 2.0.0 \(<code><i class="varname">&lt;major&gt;</i>.<i class="varname">&lt;minor&gt;</i>.<i class="varname">&lt;patch&gt;</i></code>\). The restriction ensures a reliable contract between a development environment and the deployed system components.

> ### Sample Code:  
> ```
>  
> "version": "<Major_Version>.<Minor_Version>.<Patch_Version>" 
> 
> ```

> ### Note:  
> It is also possible to declare a “partial” or incomplete version, for example, “`1`” or “`1.3`”.

You can specify all the information used to define the MTA version, for example: “*<Major\_Version\>*.*<Minor\_Version\>*.*<Patch\_Version\>*”, or any combination of the information, for example, *<Major\_Version\>*.*<Minor\_Version\>*, or simply *<Major\_Version\>*. If the version declaration does not specify a value for the *<Minor\_Version\>* or the *<Patch\_Version\>*, the deployer assumes the most recent known minor or patch version.



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_gfd_vjx_xs"/>

## modules

`modules` section of the MTA deployment descriptor, you can define a set of modules of a certain type, the contents of which reside in the MTA archive or in a file system.

> ### Sample Code:  
> Module Definition in the MTA Deployment Description
> 
> ```
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/   # Only for use in mta.yml
>     requires:
>       - name: nodejs-uaa
>       - name: nodejs
>         group: destinations
>         properties:
>           name: backend
>           url: ~{url}
>           forwardAuthToken: true
>     parameters:
>       host: ${user}-node-hello-world
>       tasks:
>         - name: task-1
>           command: node deploy.js 
>           env: 
>             env1: <value1>
>             env1: <value2>
>         - name: task-2
> 
> ```

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

Use the following attributes to define each new dependent module:

**MTA Deployment Descriptor Modules Keys**


<table>
<tr>
<th valign="top">

Attribute



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example Value



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

Name of the module to be deployed



</td>
<td valign="top">

java-hello-world-backend



</td>
</tr>
<tr>
<td valign="top">

 <code><a href="mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__table_sj5_vdb_kv">type</a></code> 



</td>
<td valign="top">

Determines the run-time to which the specified module is deployed.



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `path` 



</td>
<td valign="top">

The file-system path relative to the root of the MTA directory tree. The content of the file is used for the creation \(or update\) of the Cloud Foundry multitarget application.

> ### Restriction:  
> The specified `path` is used only during the MTA build; it is used to create an entry in the `MANIFEST.MF` file. In existing \(already built\) MTA archives \(MTAR\), `path` is ignored, and the corresponding entry for the module in the `MANIFEST.MF` file is used.

For the deployment descriptor, `mtad.yaml`, see `config` and `config-path` in [parameters](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__table_h3d_jp5_pt).



</td>
<td valign="top">

 `web/` 



</td>
</tr>
<tr>
<td valign="top">

 `group` 



</td>
<td valign="top">

Combine properties from multiple providers into one look-up object \(for example, an environment variable\). This reduces the number of look ups performed by the code of the requiring module.



</td>
<td valign="top">

`DESTINATIONS`

`API`



</td>
</tr>
<tr>
<td valign="top">

 `provides` 



</td>
<td valign="top">

Used to specify the names of `provides` sections, each containing configuration data; the data **provided** can be **required** by other modules in the same MTA.



</td>
<td valign="top">

 *<provides\_section\_name\>* 



</td>
</tr>
<tr>
<td valign="top">

 `requires` 



</td>
<td valign="top">

Used to specify the names of “`requires`” sections that are provided“resource” that has been declared for the same MTA. Tools check if all required names are provided within the MTA. The deployment mechanism for the requiring module will access properties of the matching `provides`Metadata for MTA Deployment Parameters and section and provide them to the module runtime, for example, in environment variables.

The `requires` section can declare a **group** assignment. Groups are used to combine properties from multiple providers into one lookup object \(for example, an environment variable\). This reduces the number of lookups performed by the code of the requiring module.



</td>
<td valign="top">

 *<requires\_section\_name\>* 



</td>
</tr>
<tr>
<td valign="top">

 `properties` 



</td>
<td valign="top">

A structured set of name-value pairs, which contain values that are injected into the environment of requiring modules at run time.

A `properties` property section has a map structure at its first level; any deeper levels can be structured in any way, as long as they can be transformed into a valid JSON object or array.

Keys defined at the first level map are used as lookup names. If environment variables are used, one variable is created per map key, and the name of the variable equals the key value.

> ### Tip:  
> It is possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.



</td>
<td valign="top">

```
properties:
  name: backend
  url: ${default-url}
  forwardAuthToken: true
```



</td>
</tr>
<tr>
<td valign="top">

[`parameters`](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__section_pp5_mg5_pt)



</td>
<td valign="top">

Reserved variables that affect the behavior of the MTA-aware tools, such as the deployer. Parameters can be “read-only” values, “write-only”, or “read-write” \(current/defined value can be overwritten\). Modules and resources can read parameters by referencing them with place-holder notation, for example, enclosed by `${}`.



</td>
<td valign="top">

 `host: ${user}-node-hello-world` 



</td>
</tr>
</table>

> ### Note:  
> In the context of the module `type`, the “deployment environment” is any required set of configuration tools, deployment orchestration tools, and target-platform-specific services used to deploy an MTA.

The following table shows how the modules `type` defined in the MTA deployment descriptor is mapped, where appropriate, to a corresponding build pack and which, if any parameters and properties can be used.

> ### Restriction:  
> In the following table, “platform” is either XS \(XS advanced on-premise\) or CF \(Cloud Foundry\). For details of individual parameters, see [MTA Development and Deployment Parameters](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__table_h3d_jp5_pt) below.

**MTA Default Modules Types \(XS Advanced/Cloud Foundry\)**


<table>
<tr>
<th valign="top">

Module Type



</th>
<th valign="top">

Platform



</th>
<th valign="top">

Module Parameters \(default\)



</th>
<th valign="top">

Module Properties



</th>
<th valign="top">

Result



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

 `javascript.nodejs` 



</td>
<td valign="top">

XS



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top">

Node.js run time



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

Automatic build-pack detection



</td>
</tr>
<tr>
<td valign="top">

 `nodejs` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(nodejs_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Node.js run time



</td>
</tr>
<tr>
<td valign="top">

 `native` 



</td>
<td valign="top">

XS



</td>
<td valign="top">

None



</td>
<td valign="top">

None



</td>
<td valign="top">

Native C++ run time



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

 `custom` 



</td>
<td valign="top">

XS



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top">

Custom run time



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

Automatic build-pack detection



</td>
</tr>
<tr>
<td valign="top">

 `application` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

CF



</td>
<td valign="top">

None



</td>
<td valign="top">

Automatic build-pack detection



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

 `java` 



</td>
<td valign="top">

XS



</td>
<td valign="top">

None



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top" rowspan="2">

Java run time

> ### Note:  
> Default is Tomcat



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(sap_java_buildpack)` 



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

 `java.tomcat` 



</td>
<td valign="top">

XS



</td>
<td valign="top">

None



</td>
<td valign="top" rowspan="2">

 `TARGET_RUNTIME` \(tomcat\)



</td>
<td valign="top" rowspan="2">

Tomcat run time of `sap_java_buildpack` 



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(sap_java_buildpack)` 



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

 `java.tomee` 



</td>
<td valign="top">

XS



</td>
<td valign="top">

None



</td>
<td valign="top" rowspan="2">

 `TARGET_RUNTIME` \(tomee7\)



</td>
<td valign="top" rowspan="2">

TomEE 7 run time in the `sap_java_buildpack`.

> ### Note:  
> The outdated TomEE 1.7 version is no longer included in the SAP Java Buildpack. Although TomEE 1.7 will continue to be supported until the end of the deprecation period, it is recommended to migrate to TomEE 7 as soon as possible, as described in the *TomEE Migration Guide* listed in *Related Information* below.



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(sap_java_buildpack)` 



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

 `python` 



</td>
<td valign="top">

XS



</td>
<td valign="top">

None



</td>
<td valign="top" rowspan="2">

None



</td>
<td valign="top" rowspan="2">

Python run time



</td>
</tr>
<tr>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(python_buildpack)` 



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.xs.hdi` 



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

-   `no-route: true`
-   `no-start: true`
-   `memory: 256MB`
-   `tasks: true` 

    In this case, the one-off task executed on the application \(after it has been deployed\) deploys the entire HDI content.

    ```
    [{
      "name": "deploy", 
      "command": "npm start", 
      "env": { "EXIT": 1 } 
    }] 
    ```

-   `dependency-type: hard`



</td>
<td valign="top">

None



</td>
<td valign="top">

HDI content activation



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.xs.hdi-dynamic` 



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

 `buildpack(nodejs_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Node.js run time



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.xs.hdi-zdm` 



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

-   `zdm-mode: true`
-   `no-route: true`
-   `memory: 256MB`
-   `execute-app: true`
-   `success-marker: STDOUT:.*ZDM deployment done.*`
-   `failure-marker: STDERR:.*ZDM deployment failed.*`
-   `stop-app: true`
-   `check-deploy-id: true`
-   `dependency-type: hard`
-   `health-check-type: none`



</td>
<td valign="top">

 `"HDI_DEPLOY_MODE": "ZDM"` 



</td>
<td valign="top">

HDI content activation



</td>
</tr>
<tr>
<td valign="top">

`com.sap.xs.sds`



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

-   `no-route: true`
-   `dependency-type: hard`



</td>
<td valign="top">

None



</td>
<td valign="top">

Streaming Analytics



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.xs.dwf` 



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

-   `no-route: true`
-   `memory: 256M`
-   `execute-app: true`
-   `success-marker: STDOUT:The deployment of DWF content to .* container container finished successfully .*`
-   `failure-marker: STDERR:The deployment of DWF content to .* container failed .*`
-   `stop-app: true`
-   `check-deploy-id: true`
-   `dependency-type: hard`



</td>
<td valign="top">

None



</td>
<td valign="top">

Data Warehousing Foundation



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.portal.site-content` 



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

-   `no-route: true`
-   `memory: 256M`
-   `execute-app: true`
-   `success-marker: "STDOUT:The deployment of html5 application content done.*"`
-   `failure-marker: "STDERR:The deployment of html5 application content failed.*"`
-   `check-deploy-id: true`
-   `dependency-type: hard`
-   `health-check-type: none`



</td>
<td valign="top">

None



</td>
<td valign="top">

Portal content activation



</td>
</tr>
<tr>
<td valign="top">

 `com.sap.html5.application-content` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

-   `no-route: true`
-   `memory: 256M`
-   `execute-app: true`
-   `success-marker: "STDOUT:The deployment of html5 application content done.*"`
-   `failure-marker: "STDERR:The deployment of html5 application content failed.*"`
-   `stop-app: true`
-   `check-deploy-id: true`
-   `dependency-type: hard`
-   `health-check-type: none`



</td>
<td valign="top">

None



</td>
<td valign="top">

HTML5 application content activation

> ### Restriction:  
> For use only in Cloud Foundry scenarios, to make the Node.js Application Router available as a service, for example, to applications that have no graphical front end.



</td>
</tr>
<tr>
<td valign="top">

 `business-logging` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

-   `no-route: true`
-   `memory: 256M`
-   `execute-app: true`
-   `success-marker: "STDOUT:Deployment of content deployer done."`
-   `failure-marker: "STDERR:The deployment of content deployer failed."`
-   `stop-app: true`
-   `health-check-type: none`



</td>
<td valign="top">

None



</td>
<td valign="top">

Deploys the Business Logging for configuring text resources



</td>
</tr>
<tr>
<td valign="top">

 `staticfile` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(staticfile_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Static file run time



</td>
</tr>
<tr>
<td valign="top">

 `ruby` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(ruby_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Ruby run time



</td>
</tr>
<tr>
<td valign="top">

 `go` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(go_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Go run time



</td>
</tr>
<tr>
<td valign="top">

 `php` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(php_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

PHP run time



</td>
</tr>
<tr>
<td valign="top">

 `binary` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(binary_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Binary run time



</td>
</tr>
<tr>
<td valign="top">

 `dotnet_core` 



</td>
<td valign="top">

CF



</td>
<td valign="top">

 `buildpack(dotnet_core_buildpack)` 



</td>
<td valign="top">

None



</td>
<td valign="top">

Dotnet run time



</td>
</tr>
</table>

You can use the `buildpack` parameter to specify a particular build pack to use for the application build and deployment, as illustrated in the following example:

> ### Sample Code:  
> ```
> modules: 
>   - name: my-binary-app
>     type: custom
>     parameters:
>       buildpack: binary_buildpack
> ```



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_umn_vjx_xs"/>

## resources

A resource is something which is required by the MTA at run time but not provided by the MTA, for example, a managed service instance, an instance of a user-provided service, or an external Web resource.

> ### Sample Code:  
> Resource Definition in the MTA Deployment Description
> 
> ```
> resources:
>   - name: nodejs-hdi-container
>     type: com.sap.xs.hdi-container
>     parameters:
>       config:             # Only for use in mtad.yaml
>         schema: ${default-container-name}
>         xsappname: MyAppName01
>   - name: nodejs-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config-path: security/xs-security.json      # Not for use mtad.yaml; only in mta.yaml
>   - name: log
>     type: application-logs
>     optional: true
> 
> ```

In the `resources` section of the MTA deployment descriptor, the following attributes are used to define each resource:

**MTA Deployment Descriptor Resources Keys**


<table>
<tr>
<th valign="top">

Attributes



</th>
<th valign="top">

Description



</th>
<th valign="top">

Example Value



</th>
</tr>
<tr>
<td valign="top">

 `name` 



</td>
<td valign="top">

The name of the required resource



</td>
<td valign="top">

 *<Module\_Name\>* 



</td>
</tr>
<tr>
<td valign="top">

 [`type`](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__table_t1k_bdb_kv) 



</td>
<td valign="top">

Determines the way in which the resource is provisioned by the deploy service. Typed resources are provisioned as service instances.

> ### Note:  
> The resource type is mapped to a service and a corresponding service plan. For more information, see “parameters” below and [service mappings](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__table_t1k_bdb_kv).



</td>
<td valign="top">

com.sap.xs.hdi-container

com.sap.xs.uaa

org.cloudfoundry.managed-service \*



</td>
</tr>
<tr>
<td valign="top">

 `description` 



</td>
<td valign="top">

Non-translatable, free-text string; the string is not meant to be presented on application user interfaces \(UI\)



</td>
<td valign="top">

Resource provides features that ...



</td>
</tr>
<tr>
<td valign="top">

 [`parameters`](mta-deployment-descriptor-syntax-4050fee.md#loio4050fee4c469498ebc31b10f2ae15ff2__section_pp5_mg5_pt) 



</td>
<td valign="top">

Reserved variables that affect the behavior of the MTA-aware tools, such as the deployer. Parameters can be “read-only” values, “write-only”, or “read-write” \(current/defined value can be overwritten\). Modules and resources can read parameters by referencing them with place-holder notation, that is; enclosed by `${}`.



</td>
<td valign="top">

 `service-plan: hdi-shared` 



</td>
</tr>
<tr>
<td valign="top">

 `properties` 



</td>
<td valign="top">

A structured set of name-value pairs, which contain values that are injected into the environment of requiring modules at run time.



</td>
<td valign="top">

```
properties:
  name: backend
  url: ~{url}
  forwardAuthToken: true
```



</td>
</tr>
<tr>
<td valign="top">

 `optional` 



</td>
<td valign="top">

An application can declare required resources to be `optional`, if it can compensate for their non-existence. If a required resource is declared as `optional: true` and the deployer cannot allocate the required resource, the deployer issues a warning and continues processing. If a required resource is **not** optional \(`optional: false`\), the deployer indicates an error and stops processing.



</td>
<td valign="top">

 `optional: true` \(default = `false`\)



</td>
</tr>
<tr>
<td valign="top">

 `active` 



</td>
<td valign="top">

Determines whether the resource should be considered \(`true`\) or ignored \(`false`\) for provisioning or for service binding. Resources that are not active \(`"false"`\) are not processed and are ignored even if the "inactive" resource is present in another application's `requires` list.

If you previously deployed the same application with the resource type attribute `active` set to `true`, the binding to the resource will be removed if `active` is reset to `false`.

> ### Restriction:  
> For information about which limitations and restrictions apply when using the `active` attribute, see below.



</td>
<td valign="top">

 `active: false` \(default = `true`\)



</td>
</tr>
</table>

When using the `active` resource attribute, bear in mind the following restrictions and limitations:

-   For deployments with the resource type `existing-service`, or `user-provided-service`, no binding is created; for `managed-service` no binding or service is created.

-   For deployments with the resource type `org.cloudfoundry.existing-service-key`, no binding to an application environment is made in the following cases:

    -   If the `org.cloudfoundry.existing-service-key` resource itself is set to `active: false` 

    -   If the `org.cloudfoundry.existing-service-key` resource is set to `active: true`, but refers to a resource that is set to `active: false`


-   For deployments with configuration resources that are dependent on other Multi-Target Applications and the configuration resource is set to `active:false`:

    -   If the `requires` section of the module **type** expects a list, then the environment variable assigned for this list is empty and no subscriptions are created between the modules.

    -   If the `requires` section does **not** expect a list, then there will be no environment variable.



> ### Note:  
> The resource type is mapped to a service and a corresponding service plan.

For example, the resource type “`com.sap.xs.hdi-container`” is mapped to the “`hana`” service plan “`hdi-shared`”; the resource type “`com.sap.xs.uaa-application`” is mapped to the “`xsuaa`” service plan “`application`”. The command `cf marketplace` displays a list of all currently available services and service plans.

The following table shows how the **resource type** defined in the MTA deployment descriptor is mapped to a corresponding service and service plan.

> ### Restriction:  
> In the following table, “platform” is either XS \(XS advanced on-premise\) or CF \(Cloud Foundry\).

**MTA Default Resource Types and Mapped Services**


<table>
<tr>
<th valign="top">

Resource Type



</th>
<th valign="top">

Service



</th>
<th valign="top">

Platform



</th>
<th valign="top">

Service Plan



</th>
<th valign="top">

Created Service



</th>
</tr>
<tr>
<td valign="top">

com.sap.xs.hana-schema



</td>
<td valign="top">

hana



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

schema



</td>
<td valign="top">

Plain schema



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.hana-securestore



</td>
<td valign="top">

hana



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

securestore



</td>
<td valign="top">

SAP HANA secure store



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.hdi-container



</td>
<td valign="top">

hana



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

hdi-shared



</td>
<td valign="top">

HDI container



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.uaa



</td>
<td valign="top">

xsuaa



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

default



</td>
<td valign="top">

Global UAA \*



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.uaa-application



</td>
<td valign="top">

xsuaa



</td>
<td valign="top">

CF



</td>
<td valign="top">

application



</td>
<td valign="top">

PaaS-enabled application UAA service plan for CF scenarios



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.uaa-apiaccess



</td>
<td valign="top">

xsuaa



</td>
<td valign="top">

CF



</td>
<td valign="top">

apiaccess



</td>
<td valign="top">

Access Plan for Authorization, Users and IDPS API endpoints in CF



</td>
</tr>
<tr>
<td valign="top">

com.sap.xs.sds



</td>
<td valign="top">

sds



</td>
<td valign="top">

XS/CF



</td>
<td valign="top">

default



</td>
<td valign="top">

Streaming Analytics



</td>
</tr>
<tr>
<td valign="top">

auditlog-api



</td>
<td valign="top">

auditlog-api



</td>
<td valign="top">

CF



</td>
<td valign="top">

default



</td>
<td valign="top" rowspan="2">

Audit-log service



</td>
</tr>
<tr>
<td valign="top">

auditlog-management



</td>
<td valign="top">

auditlog-management



</td>
<td valign="top">

CF



</td>
<td valign="top">

default



</td>
</tr>
<tr>
<td valign="top">

application-logs

> ### Note:  
> Replaces deprecated `com.sap.xs.application-logs`



</td>
<td valign="top">

application-logs



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Streams logs of bound applications to a central application logging stack



</td>
</tr>
<tr>
<td valign="top">

autoscaler



</td>
<td valign="top">

autoscaler



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Automatically increase or decrease the number of application instances based on a policy you define.



</td>
</tr>
<tr>
<td valign="top">

connectivity



</td>
<td valign="top">

connectivity



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Establishes secure, reliable connectivity between Cloud applications and on-premise systems



</td>
</tr>
<tr>
<td valign="top">

destination



</td>
<td valign="top">

destination



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Provides a secure and a reliable access to destination configurations



</td>
</tr>
<tr>
<td valign="top">

feature-flags



</td>
<td valign="top">

feature-flags



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Feature Flags service for the control of feature rollout



</td>
</tr>
<tr>
<td valign="top">

ml-foundation-services



</td>
<td valign="top">

ml-foundation-services



</td>
<td valign="top">

CF



</td>
<td valign="top">

lite



</td>
<td valign="top">

Provides access to foundation services by provisioning and deprovisioning“ ml foundation” services



</td>
</tr>
<tr>
<td valign="top">

objectstore



</td>
<td valign="top">

objectstore



</td>
<td valign="top">

CF



</td>
<td valign="top">

s3-standard



</td>
<td valign="top">

Provides a highly available, distributed, consistent object store for Amazon Web Services \(AWS\), Microsoft Azure, Google Cloud, SAP

> ### Note:  
> The service plan depends on the underlying Cloud infrastructure.



</td>
</tr>
<tr>
<td valign="top">

postgresql

> ### Note:  
> Replaces deprecated `org.postgresql`



</td>
<td valign="top">

postgresql



</td>
<td valign="top">

CF



</td>
<td valign="top">

v9.4-container



</td>
<td valign="top">

Provides a postgreSQL object-relational database system



</td>
</tr>
</table>

You can use the `service-plan` parameter to specify a custom service plan in place of the predefined plan. The following example shows how to replace the default service plan `v9.4-container` for the `postgresql` resource with the custom service plan `v9.4-container-xsmall`:

> ### Sample Code:  
> Specifying a Custom Service Plan
> 
> ```
> 
> resources: 
>   - name: my-postgre-service 
>     type: postgresql 
>     parameters: 
>       service-plan: v9.6-dev
> ```

To use a managed service \(or service plan\) in a Cloud Foundry scenario which is not listed in the resource-types tables above \(and the special resource-types table below\), you can define the new managed service with the resource type `org.cloudfoundry.managed-service`, as illustrated in the following example:

> ### Sample Code:  
> ```
> resources: 
>   - name: my-postgre-service 
>     type: org.cloudfoundry.managed-service 
>     parameters: 
>       service: spark 
>       service-plan: shared
> ```

The `shared` parameter can only be used with resource types that are interpreted as services, for example, all `org.cloudfoundry.[managed|user-provided]-service` resource types as well as all default resource types such as `com.sap.xs.hdi-container`.

The deployment service also supports a number of “special” resource types, as illustrated in the following table:

**Additional Special MTA Resource Types: Service Mapping**


<table>
<tr>
<th valign="top">

Resource Type



</th>
<th valign="top">

Resource Parameter ID



</th>
<th valign="top">

Created Service



</th>
</tr>
<tr>
<td valign="top">

org.cloudfoundry.user-provided-service



</td>
<td valign="top">

-   `service-name`

    **Optional**. Name of the service to create. Default value: the resource name.

-   `config`

    **Required**. Map value, containing the service creation configuration, for example, `url` and user credentials \(`user` and `password`\)

-   `shared`

    **Optional** \(true | false \(default\)\). Share service between multiple MTAs.




</td>
<td valign="top">

Create or update a user-provided service configured with the specified resource parameters



</td>
</tr>
<tr>
<td valign="top">

org.cloudfoundry.managed-service



</td>
<td valign="top">

-   `service`

    **Required**. Name of the service to create.

-   `service-plan`

    **Required**. Name of the service plan to use; this can be any service plan available in the service market place \(`cf marketplace`\).

-   `shared`

    **Optional** \(true | false \(default\)\). Share service between multiple MTAs.




</td>
<td valign="top">

Create a managed service



</td>
</tr>
<tr>
<td valign="top">

org.cloudfoundry.existing-service



</td>
<td valign="top">

-   `service-name`

    **Optional**. Name of the service to ignore. Default value: the resource name.




</td>
<td valign="top">

Assume that the named service exists and do not try to manage its life-cycle



</td>
</tr>
<tr>
<td valign="top">

org.cloudfoundry.existing-service-key



</td>
<td valign="top">

-   `service-name`

    **Required**. Name of the existing service instance whose key is to be used.

-   `service-key-name`

    **Optional**. Name of the service key. Default value is the resource `name`.




</td>
<td valign="top">

Check and use credentials for an existing service key.



</td>
</tr>
<tr>
<td valign="top">

mta-provided



</td>
<td valign="top">

-   `mta-id`

    **Required**. The ID of the provider MTA. Can also contain version ranges as described in the Semantic Version \(Semver\) specification.

-   `mta-version`

    **Required**. The version of the provider MTA.

-   `mta-provides-dependency`

    **Required**. The name of the `provides` dependency in the provider MTA.




</td>
<td valign="top">

Define dependencies between different MTAs



</td>
</tr>
<tr>
<td valign="top">

configuration



</td>
<td valign="top">

-   `provider-nid`

    **Optional**. Name space ID of the provider MTA. For cross-MTA dependency resolution this value is always “`mta`”

-   `provider-id`

    **Optional**. The ID of the provider MTA. Requires the format <code><i class="varname">&lt;mta-id&gt;</i>:<i class="varname">&lt;mta-provides-dependency-name&gt;</i></code>.

-   `version`

    **Optional**. Version number of the provider MTA; required format is defined in the Semver specification.

-   `target`

    **Optional**. Name of the provider MTA's target “space”; a structured parameter that must contain the “`org`” and “`space`” of the provider MTA.

    > ### Tip:  
    > If you specify a wild-card value \(\*\) for organization or space of the provider MTA, the provider would be searched in all organization or spaces for which the wild-card value is provided. If no match is found for the provider MTA in the specified target organization or space, then <code>org: <i class="varname">&lt;current-org&gt;</i></code> and `space: SAP` is searched.

-   `filter`

    **Optional**. Map value, containing the content entries used to match configuration entries, for example:

    ```
    filter:
      type: com.acme.plugin 
      name: some-cool-plugin
    ```




</td>
<td valign="top">

Define the mechanism for filtering configuration entries based on their configuration content



</td>
</tr>
</table>



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_pp5_mg5_pt"/>

## Parameters

Module, resource, and dependency parameters have special, platform-specific semantics. In general, many of these parameters are the same and have the same syntax and semantics as those that can be specified in manifest files for application-deployment, for example, with the `cf push` command. All parameter values can be referenced as part of other property or parameter value strings. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>, for example, `${default-host}`.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

The following parameters are supported:

**MTA Development and Deployment Parameters**


<table>
<tr>
<th valign="top">

Parameter



</th>
<th valign="top">

Scope



</th>
<th valign="top">

Read-Only \(System\)



</th>
<th valign="top">

Default Value



</th>
<th valign="top">

Example



</th>
</tr>
<tr>
<td valign="top">

 `app-name` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The name of the application to be deployed for this module, based on the module name \(with or without a name-space prefix\)



</td>
<td valign="top">

`node-hello-world`

`com.sap.xs2.samples.xsjshelloworld.node-hello-world`



</td>
</tr>
<tr>
<td valign="top">

 `authorization-url` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The authorization end point for the application run-time environment, for example, Cloud Foundry.

Default: N/A

> ### Tip:  
> Use in place of the deprecated `xs-auth-url`.



</td>
<td valign="top">

 `https://localhost:9999/uaa-security` 



</td>
</tr>
<tr>
<td valign="top">

 `buildpack` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Empty, or as specified in the deploy service configuration



</td>
<td valign="top">

 `buildpack: git://github.acme.com/xs2-java/xs2javabuildpack` 



</td>
</tr>
<tr>
<td valign="top">

 `command` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Empty, or as specified in the deploy service configuration



</td>
<td valign="top">

 `command: node index.js` 



</td>
</tr>
<tr>
<td valign="top">

 `check-deploy-id` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Check the deployment \(process\) id when checking the application execution status



</td>
<td valign="top">

 `check-deploy-id: true` 



</td>
</tr>
<tr>
<td valign="top">

 `config` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

Define service creation parameters in the MTA deployment descriptor **inline**. If the option is present in both the `MANIFEST.MF` \(`"xsappname": "default-xsappname"`\) and the `config` parameter \(`xsappname: MyAppName01`\), the MTA deployment service merges both definitions and gives precedence to the `config` parameter \(`MyAppName01`\).

> ### Restriction:  
> For use only in the **deployment** descriptor \(`mtad.yaml`\)!



</td>
<td valign="top">

```
resources:
  - name: nodejs-hdi-container
    type: com.sap.xs.hdi-container
    parameters:
      config:       # Only for use in mtad.yaml
        xsappname: MyAppName01

```



</td>
</tr>
<tr>
<td valign="top">

 `config-path` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

The relative path from the MTA root directory to a file in the same application project, which contains information used to create or update parameters of a Cloud Foundry service represented by the MTA resource.

> ### Restriction:  
> The specified `config-path` is used only during the MTA build, and a corresponding entry is created in the `MANIFEST.MF` file. In existing \(already built\) MTA archives \(MTAR\), the path is ignored, and the entry for the module in the `MANIFEST.MF` file is used instead.



</td>
<td valign="top">

```
resources:
  - name: nodejs-uaa
    type: com.sap.xs.uaa
    parameters:
      config-path: ./xs-security.json    # Only for use in mta.yaml

```



</td>
</tr>
<tr>
<td valign="top">

 `controller-url` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The URL for the application programming interface \(API\) in the application run-time environment, for example, Clound Foundry.

Default: N/A

> ### Tip:  
> Use in place of the deprecated `xs-api-url`.



</td>
<td valign="top">

```
https://api.cf.acme.ondemand.com
```



</td>
</tr>
<tr>
<td valign="top">

`database_id`



</td>
<td valign="top">

resources



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The unique ID of a database instance \(other than the default\) that hosts the run-time to which you want to deploy an application.

> ### Tip:  
> Also useful in Cloud scenarios where multiple tenant databases are mapped to the same Cloud Foundry organization or space and you need to specify the target tenant DB explicitly.



</td>
<td valign="top">

```
resources:
  - name: hdi_db
    parameters:
      config:
        database_id: 007c3a2f-5f4a-42e2-bd18-c00d7ec007f

```



</td>
</tr>
<tr>
<td valign="top">

 `default-container-name` 



</td>
<td valign="top">

resources



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Default value for the container-name parameter that is used during HDI creation. It is based on the organization, space and service name, which are combined in a way that conforms to the container-name restrictions for length and legal characters.

Default: N/A



</td>
<td valign="top">

 `INITIAL_INITIAL_SERVICE_NAME` 



</td>
</tr>
<tr>
<td valign="top">

 `default-domain` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The default domain \(configured in the Cloud Foundry environment\)



</td>
<td valign="top">

`accra6024`

`cfapps.acme.com`



</td>
</tr>
<tr>
<td valign="top">

 `default-host` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The default host name, composed based on the target platform name and the module name, which ensures uniqueness. Used with host-based routing to compose the default URI, see below.



</td>
<td valign="top">

 `trial-a007007-node-hello-world` 



</td>
</tr>
<tr>
<td valign="top">

 `default-port` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

The default, automatically allocated port value. Used with port-based routing to compose the default URI \(explained below\).

If a previous version of the application is already deployed, the default port is the same as the port in the first URL used by that application. If a previous version has not been deployed, a new port is reserved that is not in use by any other application



</td>
<td valign="top">

52001



</td>
</tr>
<tr>
<td valign="top">

 `default-uri` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The default URI, composed either as `${domain}:${port}` with port-based routing or as `${host}.${domain}` with host-based routing. Note that `${host}` will be the same as `${default-host}`, unless specified explicitly as a parameter. Similarly, `${domain}` will be the same as `${default-domain}`, and `${port}` will be the same as `${default-port}`, unless specified explicitly.



</td>
<td valign="top">

On premise: `accra6024:52001`

Cloud Foundry: `trial-a007007-node-hello-world.cfapps.acme.ondemand.com`



</td>
</tr>
<tr>
<td valign="top">

 `default-url` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The default URL, composed as `${protocol}://${default-uri}` 



</td>
<td valign="top">

 `${protocol}://${default-uri}` 



</td>
</tr>
<tr>
<td valign="top">

 `default-xsappname` 



</td>
<td valign="top">

resources



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Default value for the `xsappname` parameter that is used during UAA creation. It is based on the service name, which is modified in a way that conforms to the `xsappname` restrictions for length and legal characters.

Default: N/A



</td>
<td valign="top">

 `xs_-deploy-service-database` \(if the service name is “`xs@-deploy-service-database`” 



</td>
</tr>
<tr>
<td valign="top">

 `dependency-type` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Deployment order of modules with circular dependencies.

Default: “`soft`”



</td>
<td valign="top">

`dependency-type: hard`

`dependency-type: soft`



</td>
</tr>
<tr>
<td valign="top">

 `deployed-after` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Indicates the point in the deployment sequence when the specified modules must be deployed



</td>
<td valign="top">

 `deployed-after: [ backend, metrics ]` 



</td>
</tr>
<tr>
<td valign="top">

 `deploy-url` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The URL of the deploy service for the application run-time environment, for example, Cloud Foundry.



</td>
<td valign="top">

 `https://mo-de0825faa.mo.sap.corp:51002` 



</td>
</tr>
<tr>
<td valign="top">

 `disk-quota` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

The disk space that will be available to the application.

> ### Note:  
> Requires a unit of measurement \(M, MB, G, or GB\) in upper or lower case.

On-premise: -1 \(unlimited\), or as specified in module-type.

Cloud Foundry: 1GB, or as specified in module-type.



</td>
<td valign="top">

 `disk-quota: 1G` 



</td>
</tr>
<tr>
<td valign="top">

 `domain` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

`${default-domain}`

> ### Tip:  
> It is recommended to use `routes` to define application routes.



</td>
<td valign="top">

 `domain: ${default-domain}.acme.com` 



</td>
</tr>
<tr>
<td valign="top">

 `domains` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

 `domains: - ${default}` 



</td>
<td valign="top">

 `domains: - ${default-domain}.acme.com - test-${default-domain}.acme.com` 



</td>
</tr>
<tr>
<td valign="top">

 `enable-ssh` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Enables \(`true`\) the use of SSH within an application.

> ### Restriction:  
> For the Diego container run-time environment only.



</td>
<td valign="top">

 `enable-ssh: true` 



</td>
</tr>
<tr>
<td valign="top">

 `enable-parallel-deployments` 



</td>
<td valign="top">

All



</td>
<td valign="top">



</td>
<td valign="top">

Activates `true`\) the parallel deployment of MTA modules that do not have any dependencies regarding the deployment order. If the parameter is missing or its value is `false`, the modules are deployed sequentially.



</td>
<td valign="top">

 `enable-parallel-deployments: true` 



</td>
</tr>
<tr>
<td valign="top">

 `execute-app` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

After start and upon completion, application sets \[success | failure\]-marker in a log message



</td>
<td valign="top">

 `execute-app: true` 



</td>
</tr>
<tr>
<td valign="top">

 `env-var-name` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Specified in required dependencies and defines the name of the environment variable that will contain the service key credentials. The parameter itself is optional

Default: the name of the service key.



</td>
<td valign="top">

```
modules: 
  - name: foo 
    type: javascript.nodejs 
    requires: 
      - name: service-key-1 
        parameters: 
          env-var-name: SERVICE_KEY_CREDENTIALS
```



</td>
</tr>
<tr>
<td valign="top">

 `failure-marker` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

The failure marker in the log files for application execution, for example:

***\(STDERR\): The deployment of *<DWF\>* content to .\* container failed.\****

Default: `"STDOUT:FAILURE"`



</td>
<td valign="top">

 `failure-marker: "STDERR:Failure!"` 



</td>
</tr>
<tr>
<td valign="top">

 `generated-password` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A generated user id that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).

Default: N/A



</td>
<td valign="top">

 `IG@zGg#2g-cvMvsW` 



</td>
</tr>
<tr>
<td valign="top">

 `generated-user` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

A generated user id that is composed of 16 characters that may contain upper and lower case letters, digits and special characters \(\_, -, @, $, &, \#, \*\).

Default: N/A



</td>
<td valign="top">

 `uYi$d41TzM1-Dm6f` 



</td>
</tr>
<tr>
<td valign="top">

 `health-check-http-endpoint` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Application is considered healthy if the response to `GET` request is “200 OK”.

Default:

-   `health-check-type: http`: “/”
-   Otherwise: N/A



</td>
<td valign="top">

`health-check-type: http`

`health-check-http-endpoint: /health`



</td>
</tr>
<tr>
<td valign="top">

 `health-check-timeout` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Health-check timeout in seconds



</td>
<td valign="top">

 `health-check-timeout: 120` 



</td>
</tr>
<tr>
<td valign="top">

 `health-check-type` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

.`http` 



</td>
<td valign="top">

`health-check-type: port`

`health-check-type: http`

`health-check-type: process`



</td>
</tr>
<tr>
<td valign="top">

 `host` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

`${default-host}`

> ### Tip:  
> It is recommended to use `routes` to define application routes.



</td>
<td valign="top">

 `host: ${space}-node-hello-world` 



</td>
</tr>
<tr>
<td valign="top">

 `hosts` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

 `hosts: - ${host}` 



</td>
<td valign="top">

 `hosts: - ${space}-node-hello-world - test-${space}-node-hello-world` 



</td>
</tr>
<tr>
<td valign="top">

 `instances` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

1, or as specified in module-type



</td>
<td valign="top">

 `instances: 2` 



</td>
</tr>
<tr>
<td valign="top">

 `keep-existing-routes` 



</td>
<td valign="top">

Global, modules



</td>
<td valign="top">

 



</td>
<td valign="top">

At the **global** level, it ensures that the existing routes of **all** applications within an MTA are retained. At the **modules** level, it ensures the existing routes of the module's corresponding application are retained, even if the routes are not defined within the deployment and/or extension descriptors.

> ### Note:  
> The module-level variant of the parameter takes priority over the global parameter. Default is `false`.

`keep-existing-routes` is typically used to retain manually mapped routes \(for example, with the "`cf map-route`" command\). However, manually mapped routes can lead to inconsistent deployment results or errors that are hard to trace. The recommended approach is to define all routes in the deployment and/or extension descriptors and let the deployer create and manage them.



</td>
<td valign="top">

```
parameters:
  keep-existing-routes: true
modules:
  - name: foo
    type: nodejs
    parameters:
      keep-existing-routes: false
  - name: bar
    type: nodejs
  - name: baz
    type: javascript.nodejs
```



</td>
</tr>
<tr>
<td valign="top">

`makeUniqueName`



</td>
<td valign="top">

resources



</td>
<td valign="top">

 



</td>
<td valign="top">

Generate a unique schema name by appending a numeric identifier to the schema name, for example: MY\_SCHEMA\_1, MY\_SCHEMA\_2, etc. In SAP Business Application Studio, this parameter is set to "true" by default.



</td>
<td valign="top">

```
resources:
  - name: hdi_db
    parameters:
      config:
        makeUniqueName: true

```



</td>
</tr>
<tr>
<td valign="top">

 `memory` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

256M, or as specified in module-type



</td>
<td valign="top">

 `memory: 128M` 



</td>
</tr>
<tr>
<td valign="top">

 `no-route` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Do not assign a route to the application



</td>
<td valign="top">

 `no-route: true` 



</td>
</tr>
<tr>
<td valign="top">

 `no-start` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Start/do not start the application during deployment. Default: `false`.

> ### Tip:  
> This parameter setting overrides the command-line option *\--no-start*.

If you explicitly set the `no-start` to `false` for the module `foo` in the example provided, then the module `foo` **is** started on deployment, even if you also specify the command-line option `--no-start` with the `cf deploy` command.



</td>
<td valign="top">

```
modules: 
  - name: foo
    type: foo 
    parameters: 
      memory: 1G 
      no-start: true 
  - name: bar 
    type: bar 
    parameters: 
      memory: 2G
```



</td>
</tr>
<tr>
<td valign="top">

 `org` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Name of the target organization



</td>
<td valign="top">

 `initial, trial` 



</td>
</tr>
<tr>
<td valign="top">

 `port` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

 `${default-port}` 



</td>
<td valign="top">

 `port: 52001` 



</td>
</tr>
<tr>
<td valign="top">

 `ports` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

 `ports: - ${port}` 



</td>
<td valign="top">

 `ports: - 52001 - 52002` 



</td>
</tr>
<tr>
<td valign="top">

 `protocol` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The protocol used by the application run-time \(Cloud Foundry\) environment, for example: “http” or “https” 



</td>
<td valign="top">

 `https` 



</td>
</tr>
<tr>
<td valign="top">

 `restart-on-env-change` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Restart application on update if `env` has changed in one of the environment variables: `vcap-application`, `vcap-services` and `user-provided`.

> ### Note:  
> Default is `true`. `false` means that running applications cannot consume any environment changes.



</td>
<td valign="top">

```
restart-on-env-change:
  vcap-application: false
  vcap-services: true
  user-provided: true
```



</td>
</tr>
<tr>
<td valign="top">

 `route-path` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The context “route-path” which is part of the application default URI. Context path routing is based not only on domain names \(host header\) but also the path specified in the URL

> ### Tip:  
> It is recommended to use `routes` to define application routes.



</td>
<td valign="top">

Host-based routing:

<code>${host}.${domain}:<i class="varname">&lt;router-port&gt;</i>${route-path}</code>

Port-based routing:

`${domain}:${port}${route-path}`



</td>
</tr>
<tr>
<td valign="top">

 `routes` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

An aggregation of the parameters `host(s)`, `domain(s)`, and `no-hostname`, which encompasses the full addresses to which to bind a module.

> ### Tip:  
> If both the `routes` parameter and the other \(host, domain\) parameters are defined, the `routes` value is used and the values specified for the other parameters are ignored.



</td>
<td valign="top">

```
modules:
- name: my-app
  type: application
  parameters:
    routes:
    - route: host.my.domain/eg
    - route: host.his.domain/eg2
    - route: host.her.domain2/eg3
```



</td>
</tr>
<tr>
<td valign="top">

`schema`



</td>
<td valign="top">

resources



</td>
<td valign="top">

 



</td>
<td valign="top">

The schema name or HDI container name. If no schema name is set, the schema name will be a generated GUID.



</td>
<td valign="top">

```
resources:
  - name: hdi_db
    parameters:
      config:
        schema: MY_SCHEMA

```



</td>
</tr>
<tr>
<td valign="top">

 `service` 



</td>
<td valign="top">

resources



</td>
<td valign="top">

 



</td>
<td valign="top">

Empty, or as specified in resource-type



</td>
<td valign="top">

 `service: hana` 



</td>
</tr>
<tr>
<td valign="top">

 `service-alternatives` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

Empty, or as specified in the deploy service configuration \(`resource-type`\)

List of alternatives for a **default** service offering defined in the deploy service configuration. If a default service offering does not exist for the current org/space or creating a service fails \(with a specific error\), service alternatives are used. The order of service alternatives is considered.



</td>
<td valign="top">

```
parameters:
  service: managed-hana
  service-plan: hdi-shared
  service-alternatives: ["hana"]

```



</td>
</tr>
<tr>
<td valign="top">

 `create-service-broker` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies whether \[true|false\] a service broker should be registered for the application module.

Default: false



</td>
<td valign="top">

 `create-service-broker: true` 



</td>
</tr>
<tr>
<td valign="top">

 `service-broker-name` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The name of the service broker in the Cloud Foundry environment to be created and registered for the specified application module.

Default: `${app-name}`



</td>
<td valign="top">

`service-broker-name: jobscheduler`

`service-broker-name: ${app-name}`



</td>
</tr>
<tr>
<td valign="top">

 `service-broker-password` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The password used for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.



</td>
<td valign="top">

 `service-broker-password: ${generated-password}` 



</td>
</tr>
<tr>
<td valign="top">

 `service-broker-url` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specifies the value of the service broker universal resource locator \(URL\) to register; service requests are sent to this URL. The parameter is mandatory if `create-service-broker: true`.



</td>
<td valign="top">

 `service-broker-url: ${default-url}` 



</td>
</tr>
<tr>
<td valign="top">

 `service-broker-user` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The name of the user required for authentication by the XS controller at the service broker when performing service-related requests. The parameter is mandatory if `create-service-broker: true`.



</td>
<td valign="top">

 `service-broker-user: ${generated-user}` 



</td>
</tr>
<tr>
<td valign="top">

 `service-key-name` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

For resource type `org.cloudfoundry.existing-service-key`. Resource parameter `service-name` is mandatory, if no `service-key-name` is defined, the deploy service uses the name of the resource.



</td>
<td valign="top">

```
parameters: 
  service-name: myservice-a
  service-key-name: myservice-key  
```



</td>
</tr>
<tr>
<td valign="top">

 `service-keys` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

The name of the service key to be created or updated.



</td>
<td valign="top">

```
parameters: 
  service-keys:
  - name: tool-access-key
    config: 
      permissions: read-write
  - name: reader-endpoint
    config: 
      permissions: read-only
```



</td>
</tr>
<tr>
<td valign="top">

 `service-name` 



</td>
<td valign="top">

resources



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The name of the service to be created for this resource in the Cloud Foundry environment, based on the resource name \(with or without a name-space prefix\)



</td>
<td valign="top">

`nodejs-hdi-container`

`com.sap.xs2.samples.xsjshelloworld.nodejs-hdi-container`



</td>
</tr>
<tr>
<td valign="top">

 `service-plan` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

Empty, or as specified in resource-type



</td>
<td valign="top">

 `service-plan: hdi-shared` 



</td>
</tr>
<tr>
<td valign="top">

 `service-tags` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

A list of custom service tags that are added to the *<VCAP\_SERVICES\>* environment variable and assigned to the specified service instance



</td>
<td valign="top">

```
parameters: 
  service-tags: ["custom-tag-A", "custom-tag-B"]
```



</td>
</tr>
<tr>
<td valign="top">

 `siteId` 



</td>
<td valign="top">

resources



</td>
<td valign="top">



</td>
<td valign="top">

A globally unique ID \(GUID\) for your Fiori LaunchPad site



</td>
<td valign="top">

 `siteId=4c736e0c-a096-45f1-9ae5-a613eb24b2b9` 



</td>
</tr>
<tr>
<td valign="top">

 `space` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Name of the target organizational space



</td>
<td valign="top">

 `initial, a007007` 



</td>
</tr>
<tr>
<td valign="top">

 `stop-app` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

Stop the application after execution.



</td>
<td valign="top">

 `stop-app: true` 



</td>
</tr>
<tr>
<td valign="top">

 `success-marker` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

 



</td>
<td valign="top">

The success marker in logfiles for application execution, for example:

***\(STDOUT\): The deployment of *<appname\>* content done***

Default: `"STDOUT:SUCCESS"`



</td>
<td valign="top">

 `success-marker: "STDOUT:Success!"` 



</td>
</tr>
<tr>
<td valign="top">

 `tasks` 



</td>
<td valign="top">

modules



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Specify tasks which are available for execution \(by `command:`\) in the current droplet of the application. The tasks are executed after the deployment of the application in which they are specified.

> ### Tip:  
> Use `env:` to define environment variables which will be available during the task execution.



</td>
<td valign="top">

```
tasks: 
 - name: task-1 
   command: some-script.sh 
   env: 
     env1: value1 
     env2: value2 
```



</td>
</tr>
<tr>
<td valign="top">

 `tcp` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Use TCP type routes for all application routes if there is `domains` parameters with multiple values.

Default: `false`



</td>
<td valign="top">

 `tcp:true` 



</td>
</tr>
<tr>
<td valign="top">

 `tcps` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Create a TCPS route \(and use TLS with SSL termination at the platform router\) for all app routes where there are '`hosts`' and `domains` parameters with multiple values.

> ### Note:  
> Only relevant if SSL is enabled globally in the run-time platform, for example, with “SSL mode”\).

Default: `false`



</td>
<td valign="top">

 `tcps:true` 



</td>
</tr>
<tr>
<td valign="top">

 `user` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

Name of the current user



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

 `visibility` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Specify in an “allow list” the organizations and spaces from which configuration data can be consumed. An allow list is not required for all the provider's spaces in its own organization. A consumer must explicitly declare in which organization or space a “provider” is expected to be deployed \(if it is not in the consumer's space\).



</td>
<td valign="top">

```
provides:
  - name: backend
    parameters:
      visibility:
       - org: ${org}
         space: ${space}
       - org: '*'
       - org: '*'
         space: space3
```



</td>
</tr>
<tr>
<td valign="top">

 `xs-api-url` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The URL for the application programming interface \(API\) in the Cloud Foundry environment

Default: N/A

> ### Tip:  
> Deprecated: use `controller-url` instead.



</td>
<td valign="top">

```
https://api.cf.acme.ondemand.com
```



</td>
</tr>
<tr>
<td valign="top">

 `xs-auth-url` 



</td>
<td valign="top">

All



</td>
<td valign="top">

Yes



</td>
<td valign="top">

The authorization end point for the Cloud Foundry environment

Default: N/A

> ### Tip:  
> Deprecated: use `authorization-url` instead.



</td>
<td valign="top">

 `https://localhost:9999/uaa-security` 



</td>
</tr>
<tr>
<td valign="top">

 `zdm-mode` 



</td>
<td valign="top">

modules



</td>
<td valign="top">



</td>
<td valign="top">

Run blue-green deployment in zero-downtime-maintenance mode



</td>
<td valign="top">

 `zdm-mode: true` 



</td>
</tr>
</table>



<a name="loio4050fee4c469498ebc31b10f2ae15ff2__section_cxs_dk3_nx"/>

## Metadata for Properties and Parameters

It is possible to declare metadata for parameters and properties defined in the MTA deployment description, for example, using the “`parameters-metadata:`” or “`properties-metadata:`” keys, respectively; the mapping is based on the keys defined for a parameter or property. You can specify if a property is required \(`optional; false`\) or can be modified \(`overwritten: true`\), as illustrated in the following \(incomplete\) example:

> ### Code Syntax:  
> ```
> 
> modules:
>  - name: frontend
>    type: javascript.nodejs
>    parameters: 
>      memory: 128M  
>      domain: !sensitive ${default-domain} 
>    parameters-metadata:  
>      memory:  
>        optional: true
>        overwritable: true  
>      domain:  
>        overwritable: false 
>    properties:  
>      backend_types:  
>        order_management: sap-erp  
>        data_warehouse: sap-bw  
>    properties-metadata:  
>      backend_types:  
>        overwritable: false  
>        optional: false
>        sensitive: false
> 
> ```

The `overwritable:` and `optional` keywords for defining metadata are intended for use in extension scenarios, for example, where a value for a parameter or property is supplied at deployment time and declared in a deployment-extension descriptor file \(`myDeploymentExtension.mtaext`\). Parameters or properties defined in the `mtad.yaml` deployment descriptor with the metadata value `overwritable: false` cannot be overwritten by a value supplied from the extension descriptor. In this case, an error would occur in the deployment.

> ### Tip:  
> Parameters or properties can also be declared as sensitive.



### overwritable:

The effect of the metadata key `overwritable: [true | false]` differs depending on the value type of the property or parameter it modifies. For example, if a value is declared in a deployment-**extension** descriptor for a value that in the original deployment descriptor is declared with the metadata parameter `overwritable: false`, then the value in the extension descriptor is ignored. The following rules apply for the modification of the

-   For parameters and properties of value type scalar \(or an array\), the overwritable operation replaces the value declared

-   If a parameter \(or property\) value type is structured \(for example, as a map or object\), then “overwritable” means “extendable” or “merged” 

-   A parameter \(or property\) value type with no declared value can be overwritten by a either a scalar value or a structured value

-   If there is mismatch in the value type declared for the original parameter \(or property\) in the MTA deployment descriptor and a corresponding value for the same parameter \(or property\) in an MTA deployment-**extension** descriptor, an error occurs with notification that the overwrite operation was not successful




### sensitive:

The `sensitive` keyword enables you to hide sensitive information from public view, for example, if it is written to log or audit files. If a property or parameter is flagged as “sensitive”, any related information is not written as plain text in log files; it is masked, for example, using a string of asterisks \(`********`\). You can declare a parameter or property as “sensitive” in either of the following ways:

-   `!sensitive`

    Add the string `!sensitive` before the parameter value, for example: `domain: !sensitive ${default-domain}` 

-   `sensitive: true`

    Add the `sensitive: true` key to the list of `parameter-metadata`


**Related Information**  


[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

[Maintaining Multitarget Application Services in Cloud Foundry](../070-HANA-Cloud-DB-Dev-App-Services/maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

[TomEE Migration Guide \(Apache\)](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Ftomee.apache.org%2Fdeveloper%2Fmigration%2Ftomee-1-to-7.html)

