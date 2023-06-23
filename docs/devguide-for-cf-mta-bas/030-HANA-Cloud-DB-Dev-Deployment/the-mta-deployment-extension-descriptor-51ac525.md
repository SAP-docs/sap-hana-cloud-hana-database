<!-- loio51ac525c78244282919029d8f5e2e35d -->

# The MTA Deployment Extension Descriptor

Provide system-specific details that are not known until deployment time.

The MTA deployment descriptor provides the input required by the MTA deployer; it contains the necessary configuration for deployment and for passing values to the applications. However, in some instances, the final values are not known to the developer of the application. This type of system-specific information is **only** known to the administrator of the system on which the application is deployed.

For the cases where system-specific information is required at deployment time, it is possible to define extensions to the deployment configuration; the modifications must be specified in an MTA **extension**. An MTA extension is a file with the suffix `.mtaext`, for example, `myMTADeploymentExtension.mtaext`. The information defined in the deployment extension is used during deployment; the file name is specified as an option in the deployment command, for example:

> ### Sample Code:  
> ```
> cf deploy target/<MTA_archive>.mtar -e myMTADeployExtension.mtaext
> ```

Extension descriptors can be applied in the following scenarios:

-   Deployment:

    In theory, the developer-created deployment descriptor can contain all the information required to deploy the corresponding MTA, but this is unlikely in reality. Usually, some deployment information will not be stored with the application code in a version-control system; it is added at deployment time. An extension descriptor provides a convenient way to declare such last-minute deployment-related information. In addition, multiple, alternative deployments can be configured by using multiple extension descriptors for the same application.


You use the MTA deployment **extension** to specify information that cannot be included in the MTA deployment descriptor, for example, because the details are not yet known, or differ from system to system.

-   Proxy information

    For example, host name and port number for connections to a service

-   Memory requirements
-   URLs

    For connections to application modules

-   User-provided service credentials


The syntax required in an MTA deployment extension is illustrated in the following example:

> ### Note:  
> The syntax used in the MTA deployment extension \(`myMTAextension.mtaext`\) is the same as the syntax required to create the MTA development descriptor \(`mta.yaml`\).

> ### Sample Code:  
> MTA Deployment Extension Description \(`MyMTADeployExtension.mtaext`\)
> 
> ```
> _schema-version: "2.0.0" 
> ID: com.sap.xs2.samples.javahelloworld.config1 
> extends: com.sap.xs2.samples.javahelloworld 
> 
> modules: 
>   - name: java-hello-world  
>     parameters: 
>       memory: 128M 
>   - name: java-hello-world-backend 
>     parameters: 
>       memory: 512M 
>       instances: 1 
> ```

You can use the MTA deployment extension descriptor to add the following information \(at deployment time\) to an MTA deployment descriptor:

-   A property element, for example, a new property or parameter.
-   A value for a property that does not already have a valued defined

> ### Note:  
> It is not possible to use the MTA deployment extension descriptor to add new `modules` or `resources`, or to add new `requires` or `provides` nodes.



<a name="loio51ac525c78244282919029d8f5e2e35d__section_lwp_dj5_hwb"/>

## The `dev.mtaext` File

If your application project includes an MTA extension file with the name `dev.mtaext` in the MTA project root, and the extension file contains properties that extend the configuration defined in the application's MTA deployment descriptor \(`mta.yaml`\), then the contents of `dev.mtaext` will be merged with the configuration defined in the `mta.yaml` file when you build or run the database module.

> ### Tip:  
> By default, the HDI deployer removes any object from the HDI container that does not exist in the the design-time database module. To prevent the HDI deployer from deleting a container artifact that is not in the developer's database module, set the `auto_undeploy` property to `false` in the `mta.yaml` file.

For development purposes, you can use the MTA extension file `dev.mtaext` to set the `auto_undeploy` property \(to `false`\), as shown in the following code sample. Since the settings in the `dev.mtaext` are automatically merged with the configuration defined in the central MTA deployment descriptor \(`mta.yaml`\) before the build of an HDB module, you avoid the need to make any changes to the `mta.yaml` file.

> ### Sample Code:  
> Editing the `dev.mtaext` file
> 
> ```
>  
> ID: anyname
> _schema-version: '2.1'
> extends: mtaname
>  
> resources:
> - name: hdi_db
>   properties:
>     hdi-container-name: ${service-name}
>     HDI_DEPLOY_OPTIONS:
>        auto_undeploy: false
>    type: com.sap.xs.hdi-container
>    parameters:
>      service-name: my-service-name 
>  
> 
> ```

For building and deploying to the target environment, set the `auto_undeploy` property to `false` in the application's MTA deployment descriptor, `mta.yaml`, as illustrated in the following example:

> ### Sample Code:  
> Editing the `mta.yaml` file
> 
> ```
> modules:
> - name: db
>    type: hdb
>    path: db
>    requires:
>     - name: hdi_db
>       properties:
>         HDI_DEPLOY_OPTIONS:
>        	 auto_undeploy: false
> ```

**Related Information**  


[MTA Deployment Descriptor Syntax](mta-deployment-descriptor-syntax-4050fee.md "Description of an MTA's deployment-related prerequisites and dependencies.")

[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

