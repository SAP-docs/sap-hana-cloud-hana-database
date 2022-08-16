<!-- loio4486ada1af824aadaf56baebc93d0256 -->

# The MTA Development Descriptor

Multi-target applications are defined in a design-time **development** descriptor.

The **development** descriptor \(`mta.yaml`\) is used to define the elements and dependencies of a multitarget application \(MTA\), as illustrated in the following example:

> ### Sample Code:  
> MTA Development Descriptor \(`mta.yaml`\)
> 
> ```
> ID: com.acme.mta.sample
> version: 1.0.1
> modules:
>    - name: pricing-ui
>      type: nodejs
>      path: ./ui
>      requires:
>        - name: thedatabase
> 
>    - name: pricing-backend
>      type: java
>      path: ./backend
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

> ### Note:  
> The MTA development descriptor \(`mta.yaml`\) is used by *SAP Business Application Studio* and the SAP Cloud MTA Build Tool \(MBT\) to generate the **deployment** descriptor \(`mtad.yaml`\) that is required to deploy an MTA to the run-time platform. If you use command-line tools to deploy an MTA, you do not need an MTA **development** description \(`mta.yaml`\). However, you must create the MTA deployment descriptor \(`mtad.yaml`\) manually.

The MTA development descriptor \(`mta.yaml`\) includes the following main components:

-   Global elements

    An identifier and version that uniquely identify the MTA, plus additional **optional** information such as: a description, the providing organization, and a copyright notice for the author.

-   [Modules](the-mta-development-descriptor-4486ada.md#loio4486ada1af824aadaf56baebc93d0256__section_vcx_rqn_pt)

    A set of code or content which needs to be deployed to a specified location.

-   [Resources](the-mta-development-descriptor-4486ada.md#loio4486ada1af824aadaf56baebc93d0256__section_sxd_sqn_pt)

    Something required by the MTA at run time but not provided by the MTA, for example, a managed service or an instance of a user-provided service.

-   [Properties](the-mta-development-descriptor-4486ada.md#loio4486ada1af824aadaf56baebc93d0256__section_c45_sqn_pt)

    Key-value pairs that must be made available to the respective module at run time

-   [Parameters](the-mta-development-descriptor-4486ada.md#loio4486ada1af824aadaf56baebc93d0256__section_hqz_fqn_pt)

    Parameters are reserved variables that affect the implementation of the MTA-aware tools, such as the deployer.




<a name="loio4486ada1af824aadaf56baebc93d0256__section_vcx_rqn_pt"/>

## Modules

A **module** is a set of code or content which needs to be deployed to a specified location. The `modules` section of the MTA development descriptor enables you to define a set of source artifacts of a certain type which resides in a file system and which can be addressed by a file path. The following elements are mandatory:

-   `name`

    Must be unique within the MTA it identifies


Optional module attributes include: `type`, `properties`, and `parameters`, plus `requires` and `provides`.



### Order of deployment

Modules and therefore applications are deployed in an order that is based on the dependencies they have on each other. This is done in order to ensure that an application that depend on other applications is deployed only after any dependent applications are already up and running. To determine the order of application deployment and start up, the modules defined in the application development \(and deployment\) descriptor are sorted in such a way that the first module has the least number of \(and preferably no\) dependencies on other modules in the MTA, while the last one has the most dependencies. For example, the modules in the following deployment descriptor will be deployed in the order m3, m2, and finally m1:

> ### Note:  
> The number of dependencies between the modules and resources has no influence the on the deployment order; during deployment, the creation of services always takes place before any of the modules are deployed.

> ### Sample Code:  
> MTA Development Descriptor \(`mta.yaml`\)
> 
> ```
> ID: com.sap.xs2.sample
> version: 0.1.0
> 
> modules:
>   - name: m1
>     type: java.tomcat
>     requires:
>       - name: m2
>       - name: m3
>   - name: m2
>     type: java.tomcat
>     requires:
>       - name: m3
>   - name: m3
>     type: java.tomcat
>     requires:
>       - name: r1
>       - name: r2
>  
> resources:
>   - name: r1
>     type: com.sap.xs.uaa
>   - name: r2
>     type: com.sap.xs.hdi-container
> ```



### Circular dependencies

If two modules have a circular dependency \(for example `m1` depends on `m2`, but `m2` also depends on `m1`, the parameter “`dependency-type`” can be specified to control the order in which the modules are deployed. Modules with parameter `dependency-type: hard` \(`m1`, in the following example\) are always deployed first.

> ### Note:  
> The default setting for the dependency type `dependency-type: soft` for all modules. The obvious consequence of this default dependency setting is that the deployment order of modules with circular dependencies is arbitrary and cannot relied upon.

> ### Sample Code:  
> MTA Development Descriptor \(`mta.yaml`\)
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



<a name="loio4486ada1af824aadaf56baebc93d0256__section_sxd_sqn_pt"/>

## Resources

A **resource** is something which is required by the MTA at run time but not provided by the MTA, for example, a managed service or an instance of a user-provided service. In the development description's `resources` section, the following elements are mandatory:

-   `name`

    Must be unique within the MTA it identifies


Optional resource attributes include: `type`, `description`, `properties`, and `parameters`. The resource `type` is one of a reserved list of resource types supported by the MTA-aware deployment tools, for example: `com.sap.xs.uaa`, `com.sap.xs.hdi-container`, `com.sap.xs.job-scheduler`; the **type** indicates to the deployer how to discover, allocate, or provision the real resource, for example, a managed service such as a database, or a user-provided service.

> ### Restriction:  
> System-specific parameters for the deployment descriptor must be included in a so-called MTA deployment **extension** descriptor.



### Referencing Resource-Configuration Parameters Defined in a Separate File

When you deploy an application, some of the application's resources may require additional configuration,which you can provide in the form of parameters. For example, for a resource of type `com.sap.xs.uaa`, it might be necessary to provide details of the authentication methods and authorization types to use for access to your application. Typically, this information is provided using parameters declared in the development descriptor \(`mta.yaml`\) file, as illustrated in the following example:

> ### Sample Code:  
> Configuration Parameters in the Development Descriptor
> 
> ```
> ...
> resources:
>   - name: node-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       config: 
>         xsappname: myApp
>         scopes:
>          - name: $XSAPPNAME.Display
>            Description: Display
>          - name: $XSAPPNAME.Edit
>            Description: Edit
>          - name: $XSAPPNAME.Delete
>            Description: Delete
> ... 
> ```

Alternatively, you can define the configuration parameters in a separate file stored within the same project. In this example, security-related configuration parameters are declared in the security descriptor `xs-security.json`, and the file's location is specified as a value of the application resource’s `path` parameter, as illustrated in the following code snippet:

> ### Note:  
> The values specified for `path` should be the **relative** path from the root directory of the MTA to be deployed to the file or directory containing the specified content, as illustrated in the following example:

> ### Sample Code:  
> Configuration Path in the Development Descriptor
> 
> ```
> ...
> resources:
>   - name: nodejs-uaa
>     type: com.sap.xs.uaa
>     parameters:
>       path: security/xs-security.json
> ...
> ```

In the example above, it is assumed that the referenced resource-configuration file `xs-security.json` contains the information illustrated in the following \(incomplete\) code snippet:

> ### Sample Code:  
> Excerpt from the Security Descriptor \(`xs-security.json`\)
> 
> ```
> {
>   "xsappname" : "myApp", 
>   "scopes"     : [ { 
>                     "name" : "$XSAPPNAME.Display", 
>                     "description" : "display" }, 
>                    { 
>                     "name" : "$XSAPPNAME.Edit", 
>                     "description" : "edit" },
>                    { 
>                     "name" : "$XSAPPNAME.Delete", 
>                     "description" : "delete"  } 
>                  ], 
> ...
> }
> ```

During the application build process, the information included in the file referenced in the `path` parameter \(for example, referencing `xs-security.json`\) is converted from JSON to YAML and inserted into the **deployment** descriptor \(`mtad.yaml`\) generated by the build, as illustrated in the following \(incomplete\) example of the deployment descriptor:

> ### Sample Code:  
> Excerpt from the generated Deployment Descriptor \(`mtad.yaml`\)
> 
> ```
> ...
> resources:
>   - name: node-uaa
>     type: com.sap.xs.uaa 
>     parameters: 
>       config: 
>         xsappname: myApp  
>         scopes: 
>          - name: $XSAPPNAME.Display  
>            description: display 
>          - name: $XSAPPNAME.Edit 
>            description: edit 
>          - name: $XSAPPNAME.Delete 
>            description: delete
> ...
> ```



<a name="loio4486ada1af824aadaf56baebc93d0256__section_c45_sqn_pt"/>

## Properties

The MTA development descriptor \(`mta.yaml`\) contains two types of properties: **modules** and **requires**, which are basically very similar.

The values of properties can be specified at design time, in the deployment description \(`mta.yaml`\). More often, though a property value is determined during deployment, where the value is either explicitly set by the administrator \(for example, in an extension descriptor file\) or inferred by the MTA deployer from a target platform configuration. When set, the deployer injects the property values into the module's environment. The deployment operation reports an error, if it is not possible to determine a value for a property.

Both kinds of properties \(“module” and “required”\) are injected into the module’s environment. In the “requires” section, properties can reference other properties declared in the corresponding “provides” section, for example, using the `~{}` syntax.



<a name="loio4486ada1af824aadaf56baebc93d0256__section_hqz_fqn_pt"/>

## Parameters

Parameters are reserved variables that affect the behavior of the MTA-aware tools, such as the deployer. Parameters can be “system” \(read-only\) values, “write-only”, or “read-write” \(default value can be overwritten\). Each tool publishes a list of reserved parameters and their \(default\) values for its supported target environments. All parameter values can be referenced as part of other property or parameter value strings. To reference a parameter value, use the placeholder notation <code>${<i class="varname">&lt;parameter&gt;</i>}</code>. The value of a parameter which is “read-only” cannot be changed in descriptors; only its value can be referenced using the placeholder notation.

Examples of common read-only parameters are `user`, `app-name`, `default-host`, `default-uri`. The value of a writable parameter can be specified within a descriptor. For example, a module might need to specify a non-default value for a target-specific parameter that configures the amount of memory for the module’s target run-time environment.

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

**Related Information**  


[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

