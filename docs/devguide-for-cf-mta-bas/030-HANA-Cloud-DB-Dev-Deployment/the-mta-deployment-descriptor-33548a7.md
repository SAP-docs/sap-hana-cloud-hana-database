<!-- loio33548a721e6548688605049792d55295 -->

# The MTA Deployment Descriptor

Description of the deployment options for a multitarget application.

The MTA **deployment** descriptor defines the prerequisites and dependencies for the deployment of a multitarget application \(MTA\). The deployment description of an MTA is specified in an `mtad.yaml` file.

> ### Note:  
> If you use command-line tools to deploy an MTA, you must create the MTA deployment descriptor manually.

> ### Sample Code:  
> Simple MTA Deployment Description \(If you use command-line tools to deploy an MTA, you must create the MTA deployment descriptor manually.`mtad.yaml`\)
> 
> ```
> ID: com.acme.mta.sample
> version: 1.0.1
> modules:
>    - name: pricing-ui
>      type: javascript.nodejs
>      requires:
>        - name: thedatabase
> 
>    - name: pricing-backend
>      type: java.tomcat
>      provides:
>        - name: price_opt
>          properties:
>            protocol: http
>            uri: myhost.mydomain
> resources:
>    - name: thedatabase
>      type: com.sap.xs.hdi-container
> 
> ```

The deployment descriptor \(`mtad.yaml` for a multi-target application comprises the following high-level components:

-   Global elements

    An identifier and version that uniquely identify the MTA, plus additional **optional** information such as: a description, the providing organization, and a copyright notice for the author.

-   [Modules](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_wjj_3pn_pt)

    The application modules contained in the MTA deployment archive

-   [Resources](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_sjf_x4n_pt)

    The external resource that the application modules \(defined in the “modules” section\) depend on

-   [Properties](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_zgc_m4n_pt)

    Key-value pairs that must be made available to the respective module at run time

-   [Parameters](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_s3d_j4n_pt)

    Reserved variables that affect the behavior of the MTA-aware tools, such as the deploy service.

-   [Metadata](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_i43_223_nx)

    Provide additional information about the declared parameters and properties.

-   [Cross-MTA Dependencies](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_gfg_1tx_nv)

    Modules can have dependencies on modules in other MTAs and subscribe to MTA configuration details \(and changes\) stored in the configuration registry managed by the deploy service.

-   [Plug-ins](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_sxt_kbd_4v)

    MTAa can consume multiple configuration entries per requires dependency; the configuration is provided in a list property.

-   [Service Creation and Binding](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_yvh_bgd_4v)

    Some services support additional configuration parameters in the create-service request; these parameters are passed in a valid JSON object containing the service-specific configuration parameters. You can also find information about [service keys](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_rsh_cyd_4v) and [service tags](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_fkh_2yd_4v).

-   [Sizing Restrictions](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__section_tnc_1hv_ccb)

    The restrictions for the MTA artifacts handled by the deploy service both on-premise and SAP Business Technology Platform \(Cloud Foundry\).




<a name="loio33548a721e6548688605049792d55295__section_wjj_3pn_pt"/>

## Modules

The `modules` section of the deployment descriptor lists the names of the application modules contained in the MTA deployment archive; the following elements are mandatory:

-   `name`

    Must be unique within the MTA it identifies


Optional module attributes include: `path`, `type`, `description`, `properties`, and `parameters`, plus `requires` and `provides` lists.



### Order of Deployment

Modules and therefore applications are deployed in an order that is based on the dependencies they have on each other. This is done in order to ensure that an application that depend on other applications is deployed only after any dependent applications are already up and running.

In some cases, it is crucial that modules and therefore applications are deployed in a predictable and consistent order. To ensure this, the module-level attribute deployed-after has been introduced. It contains a list of module names. If a module has this attribute, it will be deployed only after the modules specified in the attribute have already been deployed. The relations described through this attribute are transitive, so if module A should be deployed after module B, and module B should be deployed after module C, then it means that module A should be deployed after module C.

In the following example, the `deployed-after` attributes guarantee that the `ui` module is deployed after the `backend` and `metrics` modules, and they in turn are deployed after the `hdi-content` module. Note that the deployment order of the `backend` and the `metrics` modules is not specified in the attributes. This means that they can be deployed in any order.

> ### Sample Code:  
> MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> ID: com.sap.sample 
> version: 0.1.0 
> _schema-version: "3.2.0" 
> parameters: 
>   enable-parallel-deployments: true 
> 
> modules:
>   - name: ui 
>     type: javascript  
>     deployed-after: [ backend, metrics ]  
>   - name: backend  
>     type: java  
>     deployed-after: [ hdi-content ]  
>     requires:  
>       - name: metrics  
>         properties: METRICS_URL: ~{url}  
>   - name: metrics  
>     type: javascript  
>     deployed-after: [ hdi-content ]  
>     provides: 
>       - name: metrics  
>         properties: url: ${default-url} 
>   - name: hdi-content  
>     type: hdi
> ```



### Parallel Deployment

In the order-of-deployment example above, the global MTA parameter `enable-parallel-deployments` is set to `true`. This setting activates the parallel deployment of MTA modules that do not have any dependencies regarding the deployment order. If the parameter is missing or its value is `false`, the modules are deployed sequentially.



### Circular dependencies

If two modules have a circular dependency \(for example `m1` depends on `m2`, but `m2` also depends on `m1`, the parameter “`dependency-type`” can be specified to control the order in which the modules are deployed. Modules with parameter `dependency-type: hard` \(`m1` in the following example\) are always deployed first.

> ### Note:  
> The default setting for the dependency type `dependency-type: soft` for all modules. The obvious consequence of this default dependency setting is that the deployment order of modules with circular dependencies is arbitrary and cannot be relied upon.

> ### Sample Code:  
> MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> ID: com.sap.xs2.sample
> 
> version: 0.1.0
> 
> modules:
>   - name: m1
>     type: java.tomcat
>     requires:
>       - name: m2
>     parameters:
>       dependency-type: hard
>   - name: m2
>     type: java.tomcat
>     requires:
>       - name: m1
> ```



### Shared Module Entries

It is possible for multiple MTA modules to reference a single deployable application, for example, a code bundle in the MTA archive. This means that, during the deployment operation, the same piece of code can be executed separately in multiple application \(or application instances\) but with different parameters and properties. This results in multiple, deployed run-time modules based on the same source module, which are usually started with different configuration parameters. A development project can have one source folder which is referenced by multiple module entries in the MTA deployment descriptor `mtad.yaml`, as illustrated in the following example:

> ### Code Syntax:  
> Multiple MTA Module Entries in the Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> ... 
> modules: 
> - name: fileloader-master 
>   type: nodejs 
>   path: js 
>   properties: 
>     FL_ROLE: master 
> - name: fileloader-worker 
>   type: nodejs 
>   path: js 
>   parameters: 
>     instances: 3 
>   properties: 
>    FL_ROLE: worker 
> ... 
> ```

If deployment is based on an MTA archive, it is not necessary to duplicate the code to have two different deployable modules; the specification for the MTA-module entry in `MANIFEST.MF` is extended, instead. The following \(incomplete\) example of a `MANIFEST.MF` show how to use a comma-separated list of module names to associate one set of deployment artifacts with all listed modules:

> ### Code Syntax:  
> Multiple MTA Modules Listed in the `MANIFEST.MF` Deployment Manifest
> 
> ```
> 
> ```



<a name="loio33548a721e6548688605049792d55295__section_sjf_x4n_pt"/>

## Resources

The application modules defined in the “modules” section of the deployment descriptor depend on Manifest-Version: 1.0 ... Name: js/ MTA-Module: fileloader-master, fileloader-worker ... **resources**. In the `resources` section, the following elements are mandatory:

-   `name`

    Must be unique within the MTA it identifies


The MTA deployment descriptor also supports the use of the following **optional** resource attributes:

-   `type`

    The resource **type** is one of a reserved list of resource types supported by the MTA-aware deployment tools, for example: `com.sap.xs.uaa`, `com.sap.xs.hdi-container`; the **type** indicates to the deployer how to discover, allocate, or provision the resource, for example, a managed service such as a database, or a user-provided service. A resource type is associated with a particular backing service \(for example, "`hana`" or "`xsuaa`"\) and a corresponding service plan \(for example, "`hdi-shared`" or "`default`"\).

    > ### Tip:  
    > For the complete list of resource **types** and the associated services and service plans, see *MTA Deployment Descriptor Syntax* in *Related Information* below.

-   `description`
-   `properties`
-   `parameters`
-   `active`

    The resource type `active: [true | false]` determines whether the resource should be considered \(or ignored\) for provisioning or for service binding. Resources that are not active \(`"false"`\) are not processed and are ignored even if the "inactive" resource is defined in an application's `requires` list.


> ### Restriction:  
> System-specific parameters for the deployment descriptor must be included in a so-called MTA deployment extension descriptor.



<a name="loio33548a721e6548688605049792d55295__section_zgc_m4n_pt"/>

## Properties

The MTA deployment descriptor can contain two types of properties, which are very similar, and are intended for use in the **modules** or **resources** configuration, respectively. Properties can be declared in the deployment description both in the `modules:` configuration \(for example, to define `provides:` or `requires:` dependencies\), or in the `resources` configuration to specify `requires:` dependencies. Both kinds of properties \(`modules:` and `requires:`\) are injected into the module’s environment. In the `requires:` configuration, properties can reference other properties that are declared in the corresponding `provides:` configuration, for example, using the `~{}` syntax.

The values of properties can be specified at design time, in the deployment description \(`mtad.yaml`\). More often, however, a property value is determined during deployment, where the value is either explicitly set by the administrator, for example, in an deployment-extension descriptor file \(`myDeployExtension.mtaext`\), or inferred by the MTA deployer from a target-platform configuration. When set, the deployer injects the property values into the module's environment. The deployment operation reports an error, if it is not possible to determine a value for a property.

> ### Tip:  
> It is possible to declare metadata for properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a property is **required** \(`optional; false`\) or can be modified `overwritable: true`.



### Cross-References to Properties

To enable resource properties to resolve values from a property in another resource or module, a resource must declare a dependency. However, these “requires” declarations do not affect the order of the application deployment.

> ### Restriction:  
> It is not possible to reference **list** configuration entries either from resources or “subscription” functionalities \(deployment features that are available to subscriber applications\).

> ### Code Syntax:  
> Cross-References between Properties in the MTA Deployment Descriptor
> 
> ```
> 
> modules: 
>   - name: java 
>     ... 
>     provides:  
>       - name: backend  
>         properties:  
>           url: ${default-url}/foo 
> resources:  
>   - name: example  
>     type: example-type   
>     properties:   
>       example-prop: my-example-prop   
>     - name: uaa
>       type: uaa-type 
>       requires: 
>         - name: example 
>         - name: backend 
>             properties: 
>               prop: ~{url} 
>             parameters: 
>               param: ~{url} 
>       properties: 
>         pro1: ~{example/example-prop} 
>       parameters: 
>         config: 
>           app-router-url: ~{backend/url} # reference via a module's provides section 
>           example-prop: ~{example/example-prop} # reference a resource's property 
> ```



<a name="loio33548a721e6548688605049792d55295__section_s3d_j4n_pt"/>

## Parameters and Placeholders

Parameters are reserved variables that affect the behavior of the MTA-aware tools, such as the deployer. Parameters can be “system”, “write-only”, or “read-write” \(default value can be overwritten\). Each tool publishes a list of system parameters and their \(default\) values for its supported target environments. All parameter values can be referenced as part of other property or parameter value strings. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>. The value of a system parameter cannot be changed in descriptors. Only its value can be referenced using the placeholder notation.

Examples of common read-only parameters are `user`, `app-name`, `default-host`, `default-uri`. The value of a writable parameter can be specified within a descriptor. For example, a module might need to specify a non-default value for a target-specific parameter that configures the amount of memory for the module’s runtime.

> ### Tip:  
> It is also possible to declare metadata for parameters and properties defined in the MTA deployment description; the mapping is based on the parameter or property keys. For example, you can specify if a parameter is **required** \(`optional; false`\) or can be modified `overwritable: true`.

> ### Sample Code:  
> Parameters and Placeholders
> 
> ```
> modules:
>   - name: node-hello-world
>     type: javascript.nodejs
>     path: web/
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
> ```

Descriptors can contain so-called placeholders \(also known as substitution variables\), which can be used as sub-strings within property and parameter values. Placeholder names are enclosed by the dollar sign \($\) and curly brackets \(\{\}\). For example: `${host}` and `${domain}`. For each parameter “`P`”, there is a corresponding placeholder `${P}`. The value of *<P\>* can be defined either by a descriptor used for deployment, or by the deploy service itself.

> ### Tip:  
> Placeholders can also be used without any corresponding parameters; in this scenario, their value cannot be overridden in a descriptor. Such placeholders are Read only.

Placeholders can be used to read the value of parameters. For example, the following placeholder can be used in a descriptor to get the CF / XS API URL: $\{xs-api-url\}. Placeholders can also be used in map and list values in properties and parameters sections of modules and resources, as illustrated in the following example:

> ### Sample Code:  
> ```
> 
> resources: 
>   - name: uaa
>     type: com.sap.xs.uaa 
>     parameters: 
>       config: 
>         users: [ "${generated-user}", "XSMASTER" ]
> ```



<a name="loio33548a721e6548688605049792d55295__section_i43_223_nx"/>

## Metadata for Properties and Parameters

It is possible to declare metadata for parameters and properties defined in the MTA deployment description, for example, using the “`parameters-metadata:`” or “`properties-metadata:`” keys, respectively; the mapping is based on the keys defined for a parameter or property. You can specify if a property is required \(`optional; false`\) or can be modified \(`overwritable: true`\), as illustrated in the following \(incomplete\) example:

The `overwritable:` and `optional` keywords are intended for use in extension scenarios, for example, where a value for a parameter or property is supplied at deployment time and declared in a deployment-extension descriptor file \(`myMTADeploymentExtension.mtaext`\).

You can declare metadata for the parameters and properties that are already defined in the MTA deployment description. However, any parameters or properties defined in the `mtad.yaml` deployment descriptor with the metadata value `overwritable: false` cannot be overwritten by a value supplied from the extension descriptor. In this case, an error would occur in the deployment.

> ### Code Syntax:  
> Metadata for MTA Deployment Parameters and Properties
> 
> ```
> 
> modules:
>  - name: frontend
>    type: javascript.nodejs
>    parameters: 
>      memory: 128M  
>      domain: ${default-domain} 
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
> ```

> ### Note:  
> Parameters or properties can be declared as sensitive. Information about properties or parameters flagged as “sensitive” is not written as plain text in log files; it is masked, for example, using a string of asterisks \(`********`\).



<a name="loio33548a721e6548688605049792d55295__section_rhr_j4n_pt"/>

## Example Deployment Description File

In many cases, an MTA will consist of multiple modules, which have interdependencies. The following, slightly more complex example shows an MTA deployment description including three modules:

-   A database model

-   An SAP UI5 application \(hello world\)

-   An application written in node.js


In this example, the UI5 application, “hello-world”, will use the environment-variable *<ui5\_library\>* as a logical reference to some version of UI5 on a public Website.

> ### Sample Code:  
> Complex MTA Deployment Description \(`mtad.yaml`\)
> 
> ```
> ID: com.acme.xs2.samples.javahelloworld 
> version: 0.1.0 
> 
> modules:
>   - name: hello-world
>     type: javascript.nodejs
>     requires:
>       - name: uaa
>       - name: java_details
>         properties:
>           backend_url: ~{url3}/
> 
>     properties:
>       ui5_library: "https://sapui5.hana.acme.com/"
>     
>   - name: java-hello-world-backend
>     type: java.tomee
>     requires: 
>       - name: uaa
>       - name: java-hello-world-db        # deploy ordering
>       - name: java-hdi-container
>     provides: 
>       - name: java_details
>         properties:
>           url3: ${url}                   # the value of the place-holder ${url} 
>                                          # will be made known to the deployer
>   - name: java-hello-world-db
>     type: com.sap.xs.hdi
>     requires: 
>       - name: java-hdi-container
> 
> resources:
>   - name: java-hdi-container
>     type: com.sap.xs.hdi-container
>     
>   - name: java-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       name: java-uaa                          # the name of the actual service
> 
> ```

The example describes three modules, which define a specific deployment order: `hello-world` requires `java-details`, which is provided by `java-hello-world-backend`, which in turn requires `java-hello-world-db`. These modules depend on a several resources, which are provisioned by the deployer as service instances, for example a database service instance `java-hdi-container` and a user authentication and authorization \(UAA\) service instance`java-uaa`. `uaa` is an existing service that provides the `hello_world` application with an OAuth user and password in order to enable the run-time to support authentication and authorization for this application. If your application does not require authentication services, you do not need to include this type of dependency.

The `hello_world` UI application will need to know the “access-point” for the `java-hello-world-backend` module. However, since this type of URL is often platform-specific, the UI application uses a property value \(`backend_url` in this example\) which is evaluated by the deployer as a value-substitution of the variable *<~\{url3\}\>*; the variable *<~\{url3\}\>* is provided as a property of the backend module `java-hello-world-backend`.

> ### Note:  
> The value of `url3` is specified via the system parameter `default-url`, whose value is known to the deployer at deployment time.



<a name="loio33548a721e6548688605049792d55295__section_gfg_1tx_nv"/>

## Cross-MTA Dependencies

In addition to having dependencies on modules in the same MTA, modules can have dependencies on modules from **other** MTAs, too. For these so-called cross-MTA dependencies to work, the MTA that **provides** the dependencies must declare them as “public” \(this is true by default\). By default configuration parameters are visible only in the organization in which their providing MTA resides, but this can be changed by using the `visibility` parameter described later in this section.

There are two methods that you can use to declare that one module has a dependency on a module in a different MTA:

-   [`mta-provided`](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__subsection_ncc_5vx_nv) 

-   [`configuration`](the-mta-deployment-descriptor-33548a7.md#loio33548a721e6548688605049792d55295__subsection_m5p_ywx_nv)


> ### Note:  
> Both declaration methods require the addition of a resource in the deployment descriptor; the additional resource defines the provided dependency from the other MTA.



### Cross MTA Dependency Method 1: Resource Type “mta-provided”

The resource defined in this method contains the special parameters `mta-id` \(the ID of the provider MTA\), `mta-version` \(the version of the provider MTA\) and `mta-provides-dependency` \(the name of the provides dependency in the provider MTA\). In addition, the `mta-version` parameter can contain version ranges as described in the Semver specification.

You can declare metadata for the parameters and properties defined in the MTA deploymentBear in mind that this method can only be used for cross-MTA dependency resolution, and does not allow the specification of the organization and space in which the “providing” MTA resides. As a result, a provided dependency will be “found” by this syntax, only if it is published by an MTA that is deployed in the same space as the consuming MTA.

> ### Caution:  
> Because of the limitations listed above, it is not recommended to use the “`mta-provided`” dependency-declaration method; whenever possible, use the alternative declaration method \(“`configuration`”\) instead.

The following example shows the dependency declaration in the deployment descriptor of the “consumer” MTA :

> ### Sample Code:  
> Consumer MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "2.0.0" 
> ID: com.sap.sample.mta.consumer 
> version: 0.1.0 
> 
> modules: 
>   - name: consumer
>     type: java.tomee 
>     requires: 
>       - name: message-provider 
>         properties: 
>           message: ~{message} 
> 
> resources: 
>   - name: message-provider 
>     type: mta-provided 
>     parameters: 
>       mta-id: com.sap.sample.mta.provider 
>       mta-version: ">=1.0.0" 
>       mta-provides-dependency: message-provider
> ```

The following example shows the dependency declaration in the deployment descriptor of the “provider” MTA :

> ### Sample Code:  
> Provider MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "2.0.0" 
> ID: com.sap.sample.mta.provider 
> version: 2.3.0
> 
> modules: 
>   - name: provider 
>     type: javascript.nodejs 
>     provides: 
>       - name: message-provider 
>         public: true 
>         properties: 
>           message: "Hello! This is a message provided by application \"${app-name}\", deployed in org \"${org}\" and space \"${space}\"!" 
> ```



### Cross-MTA Dependency Method 2: Resource Type “configuration”

This method can be used to access any entry that is present in the configuration registry. The parameters used in this cross-MTA declaration method are `provider-nid`, `provider-id`, `version`, and `target`. The parameters are all optional and are used to filter the entries in the configuration registry based on their respective fields. If any of these parameters is not present, the entries will not be filtered based on their value for that field. The `version` parameter can accept any valid Semver ranges.

When used for cross-MTA dependency resolution the `provider-nid` is always “`mta`”, the`provider-id` follows the format <code><i class="varname">&lt;mta-id&gt;</i>:<i class="varname">&lt;mta-provides-dependency-name&gt;</i></code> and the `version` parameter is the version of the provider MTA. In addition, as illustrated in the following example, the `target` parameter is structured and contains the name of the organization and space in which the provider MTA is deployed. In the following example, the placeholders `${org}` and `${space}` are used, which are resolved to the name of the organization and space of the consumer MTA. In this way, the provider MTA is deployed in the same space as the consumer MTA.

> ### Note:  
> By default, all provided dependencies are public.

The following example shows the dependency declaration in the deployment descriptor of the “consumer” MTA :

> ### Sample Code:  
> Consumer MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "2.0.0" 
> ID: com.sap.sample.mta.consumer 
> version: 0.1.0 
> modules:
>   - name: consumer
>     type: java.tomee 
>     requires: 
>       - name: message-provider 
>         properties: 
>           message: ~{message} 
> 
> resources: 
>   - name: message-provider 
>     type: configuration 
>     parameters:
>       provider-nid: mta 
>       provider-id: com.sap.sample.mta.provider:message-provider 
>       version: ">=1.0.0" 
>       target: 
>         org: ${org}     # Specifies the org of the provider MTA
>         space: ${space} 
> ```

> ### Tip:  
> If no target organization or space is specified by the consumer, then the current organization and space are used to deploy the provider MTA. If no match is found for the provider MTA in the specified target organization or space, then <code>org: <i class="varname">&lt;current-org&gt;</i></code> and `space: SAP` is searched.

The following example shows the dependency declaration in the deployment descriptor of the “provider” MTA :

> ### Sample Code:  
> Provider MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "2.0.0" 
> ID: com.sap.sample.mta.provider 
> version: 2.3.0
> 
> modules: 
>   - name: provider 
>     type: javascript.nodejs 
>     provides: 
>       - name: message-provider 
>         public: true 
>         properties: 
>           message: "Hello! This is a message provided by application \"${app-name}\", deployed in org \"${org}\" and space \"${space}\"!" 
> ```



### Cross-MTA Configuration Visibility

A “consumer” module must explicitly declare the organizations and spaces in which a “provider” is expected to be deployed, except if it is the same space as the consumer. The “provider” can define an allow list that specifies the organizations and spaces from which the consumption of configuration data is permitted. It is not required to include in the allow list all the provider's spaces in its own organization.

> ### Note:  
> Previously, registry entries were visible from all organizations by default. Now, the default visibility setting is "visible within the current organization and all the organization's spaces".

Allow lists can be defined on various levels. For example, a visibility allow list could be used to ensure that a provider's configuration data is visible in the local space only, in **all** organizations and spaces, in a defined list of organizations, or in a specific list of organization and space combinations.

The options for allow lists and the visibility of configuration data are similar to the options available for managed services. However, for visibility allow lists, space developers are authorized to extend the visibility of configuration data beyond the space in which they work, without the involvement of an administrator. An administrator is required to release service plans to certain organizations.

Visibility is declared on the provider side by setting the parameter `visibility:` \(of type 'sequence'\), containing entries for the specified organization \(`org:`\) and space \(`space:`\). If no `visibility:` parameter is set, the default visibility value `org: ${org}, space: '*'` is used, which restricts visibility to consumers deployed into all spaces of the provider's organization. Alternatively, the value `org: '*'` can be set, which allows to bindings from all organizations and spaces. The allow list can contain entries at the organization level only. This, however, releases configuration data for consumption from all spaces within the specified organizations, as illustrated in the following \(annotated\) example.

> ### Tip:  
> Since applications deployed in the same space are always considered " friends", visibility of configuration data in the local space is always preserved, no matter which visibility conditions are set.

> ### Sample Code:  
> ```
> provides:
>   - name: backend
>     public: true
>     parameters:
>       visibility:          # a list of possible settings:
>        - org: ${org}       # for local org 
>          space: ${space}   # and local space
>        - org: org1         # for all spaces in org1
>        - org: org2         # for the specified combination (org2,space2)
>          space: space2
>        - org: ${org}       # default: all spaces in local org
>        - org: '*'          # all orgs and spaces
>        - org: '*'          
>          space: space3     # every space3 in every org
> ```

The authorization model ensures the following rules apply:

-   Only those users in the allowed spaces can read or consume the provided configuration data.

-   Only users with the role “SpaceDeveloper” in the configuration-data provider's space can modify \(edit or delete\) configuration data.




<a name="loio33548a721e6548688605049792d55295__section_sxt_kbd_4v"/>

## Plug-ins

The deployment service also supports a method that allows an MTA to consume **multiple** configuration entries per `requires` dependency; the configuration is provided in a `list` property, as illustrated in the following example:

> ### Posting Instructions:  

> ### Sample Code:  
> Multiple “requires” Dependencies in the MTA Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> _schema-version: "2.1" 
> ID: com.acme.framework 
> version: "1.0" 
> modules:
>   - name: framework 
>     type: javascript.nodejs 
>     requires: 
>       - name: plugins
>         list: plugin_configs 
>         properties: 
>           plugin_name: ~{name} 
>           plugin_url: ~{url}/sources 
>         parameters: 
>           managed: true # true | false. Default is false 
> 
> resources: 
>   - name: plugins 
>     type: configuration 
>     parameters: 
>       target: 
>         org: ${org} 
>         space: ${space} 
>       filter: 
>         type: com.acme.plugin 
> ```

The MTA deployment descriptor shown in the example above contains a module that specifies a “`requires`” dependency to a configuration resource. Since the `requires` dependency has a `list` property, the deploy service will attempt to find multiple configuration entries that match the criteria specified in the configuration resource.

> ### Tip:  
> It is possible to create a subscription for a **single** configuration entry, for example, where no “`list:`” element is defined in the required dependency.

The resource itself contains a `filter` parameter that is used to filter entries from the configuration registry based on their content. In the example shown above, the filter only matches entries that are provided by an MTA deployed in the current space, which have a `type` property in their content with a value of `com.acme.plugin`.

> ### Note:  
> The filter parameter can be used in combination with other configuration resource specific parameters, for example: `provider-nid`, `provider-id`, `target`, and `version`.

If the “`list`” element is missing, the values matched by the resources filter are **single** configuration entries – not the usual list of multiple configuration entries. In addition, if either no value or multiple values are found during the deployment of the consuming \(subscribing\) MTA, the deployment operation fails. If a provider \(plug-in\) contributes additional configuration details after subscriber applications have been deployed, the subscriber applications will not receive the new information immediately; they will be made aware of the new configuration details only when they are updated. Note, however, that the update operation will fail because multiple configuration entries will be available at that point.

The XML document in the following example shows some sample configuration entries, which would be matched by the filter if they were present in the registry.

> ### Sample Code:  
> MTA Configuration Entries Matched in the Registry
> 
> ```
> <configuration-entry>
>   <id>8</id> 
>   <provider-nid>mta</provider-nid> 
>   <provider-id>com.sap.sample.mta.plugin-1:plugin-1</provider-id> 
>   <provider-version>0.1.0</provider-version> 
>   <target-space>2172121c-1d32-441b-b7e2-53ae30947ad5</target-space> 
>   <content>{"name":"plugin-1","type":"com.acme.plugin","url":"https://xxx.mo.sap.corp:51008"}</content> 
> </configuration-entry> 
> <configuration-entry> 
>   <id>10</id> 
>   <provider-nid>mta</provider-nid> 
>   <provider-id>com.sap.sample.mta.plugin-2:plugin-2</provider-id> 
>   <provider-version>0.1.0</provider-version> 
>   <target-space>2172121c-1d32-441b-b7e2-53ae30947ad5</target-space> 
>   <content>{"name":"plugin-2","type":"com.acme.plugin"}</content> 
> </configuration-entry> 
> ```

The JSON document in the following example shows the environment variable that will be created from the `requires` dependency defined in the example deployment descriptor above, assuming that the two configuration entries shown in the XML document were matched by the filter specified in the configuration resource.

> ### Note:  
> References to non-existing configuration entry content properties are resolved to “`null`”. In the example above, the configuration entry published for `plugin-2` does not contain a `url` property in its content. As a result, the environment variable created from that entry is set to “`null`” for `plugin_url`.

> ### Sample Code:  
> Application Environment Variable
> 
> ```
> plugin_configs: [ 
>   { 
>     "plugin_name": "plugin-1",  
>     "plugin_url": "https://xxx.mo.sap.corp:51008/sources"  
>   },  
>   {  
>     "plugin_name": "plugin-2",  
>     "plugin_url": null  
>   } 
> ] 
> ```

Requires dependencies support a special parameter named “`managed`”, which registers as a “subscriber” the application created from the module containing the `requires` dependency. One consequence of this registration is that if any new configuration entries are published in the configuration registry during the deployment of another MTA, and those new entries match the filter specified in the subscription of an application, then that application's environment would be updated, and the application itself would be restarted in order for it to see its new environment's state.

> ### Tip:  
> When starting the deployment of an MTA \(with the `xs deploy` command\), you can use the special option *\--no-restart-subscribed-apps* to specify that, if the publishing of configuration entries created for that MTA result in the update of a subscribing application's environment, then that application should **not** be restarted.



<a name="loio33548a721e6548688605049792d55295__section_yvh_bgd_4v"/>

## Service-Creation Parameters

Some services support additional configuration parameters in the `create-service` request; these parameters are passed in a valid JSON object containing the service-specific configuration parameters. The deploy service supports the following methods for the specification of service creation parameters:

-   Method 1

    An entry in the MTA deployment descriptor \(or the extension\)

-   Method 2

    A JSON file with the required service-configuration parameters

    > ### Note:  
    > If service-creation information is supplied both in the deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.




### Service-Creation Parameters in the MTA Deployment Descriptor

The following example shows how to define the service-configuration parameters in the MTA deployment descriptor \(`mtad.yaml`\). If you use this method, all parameters under the special `config` parameter are used for the service-creation request.

> ### Sample Code:  
> Service-Configuration Parameters in the MTA Deployment Descriptor
> 
> ```
> resources: 
>   - name: java-uaa 
>     type: com.sap.xs.uaa 
>     parameters: 
>       config: 
>         xsappname: java-hello-world 
> ```



### Service-Creation Parameters in a JSON File

The following example shows how to define the service-configuration parameters for a service-creation request in a JSON file; with this method, there are dependencies on further configuration entries in other configuration files. For example, if you use this JSON method, an additional entry must be included in the `MANIFEST.MF` file which defines the path to the JSON file containing the parameters as well as the name of the resource for which the parameters should be used.

> ### Sample Code:  
> Service-Configuration Parameters in a JSON File
> 
> ```
> resources: 
>   - name: java-uaa 
>     type: com.sap.xs.uaa 
>     parameters: 
>       config: 
>         xsappname: java-hello-world 
> ```

The MTA's security descriptor \(`xs-security.json`\) should contain the following:

> ### Sample Code:  
> `xs-security.json` File
> 
> ```
> { 
>   "xsappname": "java-hello-world" 
> } 
> ```

The application manifest \(`MANIFEST.MF`\) should contain the following:

> ### Sample Code:  
> Service-Configuration Parameters in the MANIFEST.MF
> 
> ```
> Name: xs-security.json 
> MTA-Resource: java-uaa 
> Content-Type: application/json 
> ```

The following example of an MTA deployment descriptor shows how to combine both methods to achieve the desired application-service creation on deployment:

> ### Sample Code:  
> Combined Service-Configuration Parameters in the MTA Deployment Descriptor
> 
> ```
> resources: 
>   - name: java-uaa 
>     type: com.sap.xs.uaa 
>     parameters: 
>       config: 
>         xsappname: java-hello-world 
> ```



<a name="loio33548a721e6548688605049792d55295__section_lhr_hrd_4v"/>

## Service-Binding Parameters

Some services support additional configuration parameters in the `create-bind` request; these parameters are passed in a valid JSON object containing the service-specific configuration parameters. The deployment service supports the following methods for the specification of service-binding parameters:

-   Method 1

    An entry in the MTA deployment descriptor \(or the extension\)

-   Method 2

    A JSON file with the required service-configuration parameters


> ### Note:  
> If service-binding information is supplied both in the MTA's deployment \(or extension\) descriptor **and** in a supporting JSON file, the parameters specified directly in the deployment \(or extension\) descriptor override the parameters specified in the JSON file.

In the MTA deployment descriptor, the `requires` dependency between a module and a resource represents the binding between the corresponding application and the service created from them \(if the service has a `type`\). For this reason, the `config` parameter is nested in the `requires` dependency parameters, and a distinction must be made between the `config` parameter in the `modules` section and the `config` parameter used in the `resources` section \(for example, when used for service-creation parameters\).



### Service-Binding Parameters in the MTA Deployment Descriptor

The following example shows how to define the service-binding parameters in the MTA deployment descriptor \(`mtad.yaml`\). If you use this method, all parameters under the special `config` parameter are used for the service-bind request.

> ### Sample Code:  
> Service-Binding Parameters in the MTA Deployment Descriptor
> 
> ```
> modules: 
>   - name: node-hello-world-backend 
>     type: javascript.nodejs 
>     requires: 
>       - name: node-hdi-container 
>         parameters: 
>           config: 
>             permissions: debugging 
> ```



### Service-Binding Parameters in a JSON File

The following example shows how to define the service-binding parameters for a service-bind request in a JSON file; with this method, there are dependencies on entries in other configuration files. For example, if you use this JSON method, an additional entry must be included in the `MANIFEST.MF` file which defines the path to the JSON file containing the parameters as well as the name of the resource for which the parameters should be used.

> ### Sample Code:  
> Service-Binding Parameters in a JSON File
> 
> ```
> modules: 
>   - name: node-hello-world-backend 
>     type: javascript.nodejs 
>     requires: 
>       - name: node-hdi-container 
>         parameters: 
>           config-path: xs-hdi.json 
> ```

The MTA's `xs-hdi.json` file should contain the following:

> ### Sample Code:  
> `xs-hdi.json` File
> 
> ```
> { 
>   "permissions": "debugging" 
> } 
> ```

The application manifest \(`MANIFEST.MF`\) should contain the following:

> ### Note:  
> To avoid ambiguities, the name of the module is added as a prefix to the name of the `requires` dependency; the name of the manifest attribute uses the following format: <code><i class="varname">&lt;module-name&gt;</i>#<i class="varname">&lt;requires-dependency-name&gt;</i></code>.

> ### Sample Code:  
> Service-Binding Parameters in the MANIFEST.MF
> 
> ```
> Name: xs-hdi.json 
> MTA-Requires: node-hello-world-backend#node-hdi-container 
> Content-Type: application/json
> ```

The following example of an MTA deployment descriptor shows how to combine both methods to achieve the desired application-service binding on deployment:

> ### Sample Code:  
> Combined Service-Binding Parameters in the MTA Deployment Descriptor
> 
> ```
> modules: 
>   - name: node-hello-world-backend 
>     type: javascript.nodejs 
>     requires: 
>       - name: node-hdi-container 
>         parameters: 
>           config: 
>             permissions: debugging 
> ```



<a name="loio33548a721e6548688605049792d55295__section_rsh_cyd_4v"/>

## Service Keys

You can use the `service-keys` parameter in the MTA deployment descriptor to configure the deployment service to create and update the corresponding service keys during the creation or update of a service instance. The special `service-keys` parameter must be added to the `resources` in the MTA deployment descriptor which represent services that support service keys.

The following example shows how to set up the configuration of the service keys in the applications deployment descriptor \(`mtad.yaml`\) file. Each entry for the `service-keys` parameter can include optional configuration parameters, which must be placed under the `config` parameter.

> ### Sample Code:  
> Service-Key Configuration in the MTA Deployment Descriptor
> 
> ```
> resources: 
>   - name: my-service-instance 
>     type: org.cloudfoundry.managed-service
>     parameters:  
>       service-keys:  
>       - name: tool-access-key  
>         config:  
>           permissions: read-write  
>       - name: reader-endpoint  
>         config:  
>           permissions: read-only
> ```



### Consuming Existing Service Keys

You can configure an application to use an existing service key as an alternative to a service binding. In this way, it is possible to enable an application to use service key's credentials and consume the corresponding service. The existing service keys are modeled as a resource of type `org.cloudfoundry.existing-service-key`. An MTA module can depend on the defined service resource which results in the injection of the reused service-key credentials into the consuming application's environment.

In the following example, the Node.js application `myApp` has the environment variable `keycredentials` whose details are specified in the existing service key `test-key-1` which belongs to the existing service `service-a`. In this reuse-service-key configuration, the only parameter that is mandatory is `service-name` in the `resources` section.

> ### Sample Code:  
> Consuming an Existing Service-Key in the MTA Deployment Descriptor
> 
> ```
> modules:
>   - name: myApp 
>     type: javascript.nodejs 
>     requires: 
>       - name: service-key-1 
>         parameters: 
>           env-var-name: keycredentials # Default value is service-key name
> ... 
> resources: 
>   - name: service-key-1 
>     type: org.cloudfoundry.existing-service-key
>     parameters: 
>       service-name: service-a # service the key belongs to 
>       service-key-name: test-key-1 # Default value is the resource name 
> ```



<a name="loio33548a721e6548688605049792d55295__section_fkh_2yd_4v"/>

## Service Tags

Some services provide a list of tags that are later added to the *<VCAP\_SERVICES\>* environment variable. These tags provide a more generic way for applications to parse *<VCAP\_SERVICES\>* for credentials. You can provide custom tags when creating a service instance, too. To inform the deployment service about custom tags, you can use the special `service-tags` parameter, which must be located in the `resources` definition that represent the managed services, as illustrated in the following example:

> ### Sample Code:  
> Defining Service Tags in the MTA Deployment Descriptor
> 
> ```
> resources: 
>   - name: nodejs-uaa 
>     type: com.sap.xs.uaa 
>     parameters: 
>       service-tags: ["custom-tag-A", "custom-tag-B"] 
> ```

> ### Note:  
> Some service tags are inserted by default, for example, `xsuaa`, for the XS User Account and Authentication \(UAA\) service.



<a name="loio33548a721e6548688605049792d55295__section_ujf_nb2_4v"/>

## Namespaces

To prevent name clashes for applications and services contained in different MTAs, but deployed in the same space, the deployment service provides an option that enables you to add the MTA IDs in front of the names of the applications and services contained in those MTAs. For example, an application named “`com.sap.xs2.sample.app`” and a service named “`com.sap.xs2.sample.service`” are created when the *\--use-namespaces* option is specified during the deployment of an MTA with the following deployment descriptor:

> ### Sample Code:  
> MTA Deployment Descriptor
> 
> ```
> ID: com.sap.xs2.sample 
> version: 0.1.0 
> 
> modules: 
>   - name: app 
>     type: java.tomcat 
> 
> resources: 
>   - name: service 
>     type: com.sap.xs.uaa 
> ```

By default the “use namespaces” feature is disabled. However, specifying the *\--use-namespaces* option as part of the `xs deploy` command allows you to enable it. If you want namespaces to be used for applications, but not for services, you can use the *\--no-namespaces-for-services* option in combination with the *\--use-namespaces*. For example, if you use the *\--use-namespaces* and *\--no-namespaces-for-services* options when deploying an MTA with the deployment descriptor shown in the sample code above, the deployment operation creates an application named “`com.sap.xs2.sample.app`” and a service named “`service`”.



<a name="loio33548a721e6548688605049792d55295__section_hkb_xg2_4v"/>

## Application Versions and Deployment Consistency

The deployment service follows the rules specified in the Semantic Versioning Specification \(Semver\) when comparing the versions of a deployed MTA with the version that is to be deployed. If an MTA submitted for deployment has a version that is lower than or equal to an already deployed version of the same MTA, the deployment might fail if their is a conflict with the version rule specified in the deployment operation. The version rule is a parameter of the deployment process, which specifies which relationships to consider between the existing and the new version of an MTA before proceeding with the deployment operation. The version rules supported by the deploy service are as follows:

-   *HIGHER*

    Only MTAs with versions that are bigger than the version of the currently deployed MTA, are accepted for deployment.

-   *SAME\_HIGHER*

    Only MTAs with versions that are higher than \(or the same as\) the version of the currently deployed MTA are accepted for deployment. This is the **default** setting for the version rule.

-   *ALL*

    All versions are accepted for deployment.




<a name="loio33548a721e6548688605049792d55295__section_xfy_yg2_4v"/>

## Registration of Service URLs

An application can declare a service URL for automatic registration with the run-time platform controller; the URL is made available so that other applications can find out where \(which URL\) the application can be accessed. The following example shows the parameters to use in the MTA's deployment \(or extension\) descriptor to ensure that the corresponding application specifies that a service URL should be registered as part of its deployment process:

> ### Tip:  
> You can use placeholders `${}` in the service-URL declaration.

> ### Sample Code:  
> ```
> modules: 
>   - name: jobscheduler-dashboard 
>     type: javascript.nodejs 
>     parameters: 
>       register-service-url: true 
>       service-name: job-scheduler-service-dashboard 
>       service-url: ${default-url}
> ```



<a name="loio33548a721e6548688605049792d55295__section_z5h_332_4v"/>

## Service-Broker Creation

Service brokers are applications that advertise a catalog of service offerings and service plans, as well as interpreting calls for creation, binding, unbinding, and deletion. The deploy service supports automatic creation \(and update\) of service brokers as part of an application deployment process. For example, an application can declare that a service broker should be created as part of its deployment process, by using the following parameters in its corresponding module in the MTA deployment \(or extension\) descriptor:

> ### Tip:  
> You can use placeholders `${}` in the service-URL declaration.

> ### Sample Code:  
> ```
> 
> - name: jobscheduler-broker
>   properties: 
>     user: ${generated-user}
>     password: ${generated-password}  
>   parameters:
>     create-service-broker: true 
>     service-broker-name: jobscheduler 
>     service-broker-user: ${generated-user} 
>     service-broker-password: ${generated-password} 
>     service-broker-url: ${default-url} 
> ```

The value of the “`${generated-user}`” and “`${generated-password}`” placeholders in the `properties` section is the same as in the `parameters` section. The service-broker application uses this mechanism to inject the user-password credentials.

The `create-service-broker` parameter should be set to true if a service broker must be created for the specified application module. You can specify the name of the service broker with the `service-broker-name` parameter; the default value is `${app-name}`The `service-broker-user` and `service-broker-password` are the credentials that will be used by the controller to authenticate itself to the service broker in order to make requests for creation, binding, unbinding and deletion of services. The `service-broker-url` parameter specifies the URL on which the controller will send these requests.

> ### Note:  
> During the creation of the service broker, the run-time platform controller makes a call to the service-broker API to inquire about the services and plans the service broker provides. For this reason, an application that declares itself as a service broker must implement the service-broker application-programming interface \(API\). Failure to do so might cause the deployment process to fail.



<a name="loio33548a721e6548688605049792d55295__section_ddn_hz2_4v"/>

## Module-Based User-Provided Service Creation

The Cloud Foundry run-time allows you to expose an application as a user provided service which other applications can bind to. The following example of the application's the MTA deployment \(or extension\) descriptor shows the syntax required:

> ### Sample Code:  
> ```
> 
> modules:
>   - name: provider 
>     properties: 
>       userID: ${generated-user} 
>       password: ${generated-password} 
>     parameters: 
>       create-user-provided-service: true
>       user-provided-service-name: techical-user-provider
>       user-provided-service-config: 
>         userID: ${generated-user} 
>         password: ${generated-password} 
>         url: ${default-url} 
> ```

The `create-user-provided-service` parameter must be set to “`true`” if you want a user-provided service to be created for the specified module. In addition, you can specify custom parameters for the application \(for example, `userID`, `password`, or `url`\); these custom parameters are used for the creation of the user-provided service. The custom parameters are exposed to any other applications that bind to the user-provided service that is created during the application-deployment process.

> ### Restriction:  
> The names of environment variables already defined at the platform level \(for example, *<XS\_\*\>*\) cannot be used to define the name of a custom parameter, too. In addition, since “`user`” is the \(protected\) name of a platform environment variable, it cannot be used as the name of a custom parameter. To specify the name of a user in a custom parameter, use “`userID`”, “`username`”, or something similar instead.



<a name="loio33548a721e6548688605049792d55295__section_yds_bs2_qv"/>

## Alternative Grouping of MTA Properties

The deploy service supports the extension of the standard syntax for references in module properties; this extension enables you to specify the name of the `requires` section inside the property reference. You can use this syntax extension to declare implicit groups, as illustrated in the following example:

> ### Sample Code:  
> Syntax Extension: Alternative Grouping of MTA Properties
> 
> ```
> modules:
>   - name: pricing-ui
>     type: javascript.nodejs 
>     properties: 
>       API: # equivalent to group, but defined in the module properties
>        - key: internal1
>          protocol: ~{price_opt/protocol} #reference to value of protocol defined in price_opt of module pricing-backend
>        - key: external 
>          url: ~{competitor_data/url} # reference to string value of property 'url' in required resource 'competitor_data' 
>          api_keys: ~{competitor_data/creds} # reference to list value of property 'creds' in 'competitor_data' 
>     requires: 
>      - name: competitor_data 
>      - name: price_opt 
>   - name: pricing-backend
>     type: java.tomcat 
>     provides: 
>      - name: price_opt 
>        properties: 
>           protocol: http ... 
>   resources: 
>     - name: competitor_data 
>       properties: 
>         url: "https://marketwatch.acme.com/" 
>         creds: 
>           app_key: 25892e17-80f6 
>           secret_key: cd171f7c-560d 
> ```



## MTA Deployment from a Directory

It is possible to deploy an MTA directly from directory, provided that directory structure is suitably defined. When deploying an MTA from a directory structure, the deploy service's command-line client \(`xs deploy`\) builds an MTA archive \(`myMTA.mtar`\) as a first step and then uses the prepared archive to complete the deployment operation. To ensure a successful deployment of an MTA from a directory structure, the following prerequisites apply:

-   `mtad.yaml`

    The `mtad.yaml` file should be located in the root of the MTA directory one would like to deploy.

-   `MANIFEST.MF`

    To enable the deploy service to create a valid `MANIFEST.MF` entry for each MTA element with the associated content, you must ensure that the conditions listed in the following table are met:


**Required Entries in the MANIFEST.MF File for Directory Deployment**


<table>
<tr>
<th valign="top">

Element with Associated Content

</th>
<th valign="top">

Element/Parameter

</th>
<th valign="top">

Example mtad.yaml

</th>
<th valign="top">

Manifest Entry

</th>
</tr>
<tr>
<td valign="top">

MTA module

</td>
<td valign="top">

Element: `path` 

</td>
<td valign="top">

```
modules: 
- name: jobscheduler-backend 
    type: javascript.nodejs 
    path: backend/ 
```



</td>
<td valign="top">

```
Name: 
  backend/
MTA-Module: 
  jobscheduler-backend

```



</td>
</tr>
<tr>
<td valign="top">

MTA resource that requires creation configuration specified in an external file

</td>
<td valign="top">

Parameter: `config-path` 

</td>
<td valign="top">

```
- name: jobscheduler-uaa
  type: com.sap.xs.uaa
  parameters:
    config-path: security/xs-security.json

```



</td>
<td valign="top">

```
Name: 
  security/xs-security.json
MTA-Resource: 
  jobscheduler-uaa
Content-Type: 
  application/json 

```



</td>
</tr>
<tr>
<td valign="top">

Module required dependency, pointing to the resource that needs binding configuration specified in an external file

</td>
<td valign="top">

Parameter: `config-path` 

</td>
<td valign="top">

```

modules: 
- name: backend
  requires: db
  parameters:
    config-path: cfg/backend-db-params.json

```



</td>
<td valign="top">

```
Name:
  cfg/backend-db-params.json 
MTA-Requires: 
  backend/db 
Content-Type: 
  application/json 

```



</td>
</tr>
</table>

> ### Note:  
> The values specified for `path` and `config-path` values should be the **relative** path from the root directory of the MTA to be deployed to the file or directory containing the specified content.



<a name="loio33548a721e6548688605049792d55295__section_tnc_1hv_ccb"/>

## Sizing Restrictions

The following table lists the restrictions that apply to the size of MTA **deployment** components that are handled by the SAP HANA deploy service during application deployment to Cloud Foundry:

**MTA Descriptor File Size Restrictions**


<table>
<tr>
<th valign="top">

MTA Component

</th>
<th valign="top">

Maximum Size

</th>
</tr>
<tr>
<td valign="top">

MTA archive

</td>
<td valign="top">

4 GB

</td>
</tr>
<tr>
<td valign="top">

MTA modules/resources content

</td>
<td valign="top">

2 GB

</td>
</tr>
<tr>
<td valign="top">

MTA deployment descriptor \(`mtad.yaml`\)

</td>
<td valign="top">

1 MB

</td>
</tr>
<tr>
<td valign="top">

MTA manifest \(`MANIFEST.MF`\)

</td>
<td valign="top">

1 MB

</td>
</tr>
</table>

**Related Information**  


[MTA Deployment Descriptor Syntax](mta-deployment-descriptor-syntax-4050fee.md "Description of an MTA's deployment-related prerequisites and dependencies.")

[Multitarget Applications](multitarget-applications-8b55a61.md "Multitarget applications collect multiple modules and resource references in a single, deployable archive.")

[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

