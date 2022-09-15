<!-- loio8b55a61e4ecc4a8d951d3b4f043e8349 -->

# Multitarget Applications

Multitarget applications collect multiple modules and resource references in a single, deployable archive.

A multitarget applications \(MTA\) is basically the natural evolution of the so-called "multi-part" application; an MTA, however, comprises multiple software “**modules**” that share a common life cycle for development and deployment. Although these modules can be developed using different technology and languages and then deployed to different targets, they all serve \(different aspects of\) a particular purpose for the application users.

An MTA is any unit of deployable functionality. This can be a single module or a group of modules packaged into an MTA archive along with an MTA deployment descriptor. MTAs can be distributed across multiple containers and target platforms. The MTA approach enables you to adopt a common life-cycle process \(from development to deployment\) for all application artifacts to be deployed to the target run-time platform, for example, Cloud Foundry.

> ### Tip:  
> MTAs also enable you to model and configure run-time dependencies.

You define a multi-target application in the following files:

-   MTA deployment descriptor \(`mtad.yaml`\)
-   MTA deployment **extension** descriptor \(`myMTAextension.mtaext`\)

    > ### Note:  
    > The extension descriptor is optional; it is used to provide system-, service-, or module-specific details that are not known until deployment time.


> ### Restriction:  
> For the MTA deployment operation, locally specific modifications to the deployment configuration must be defined in an MTA **deployment-extension** file.



<a name="loio8b55a61e4ecc4a8d951d3b4f043e8349__section_k5b_f3b_b1b"/>

## The MTA Model

The MTA model is a platform-independent description of the different modules that define an application, the dependencies between the modules, the configuration data the modules expose, and the resources the application modules require to run. The MTA model is specified using YAML, in descriptor files that accompany the development and deployment processes. The MTA model serves the following purposes:

1.  It defines an application composed of multiple \(heterogeneous\) subcomponents.

2.  It declares the resources that the application depends on at run time and \(or\) at deployment time.

3.  It defines configuration variables \(and their relationship\), whose values distinguish different deployment scenarios for the application.


Many people find it useful to see the MTA model as a sort of formal contract between developers \(using development tools\) and the MTA deployer. The deployer is a tool that consumes a description of the MTA model and translates it into target platform-specific “native” commands that can be used in the following scenarios:

-   The provisioning of run-time containers

-   The creation and binding of resources, for example, "service instances" on Cloud Foundry

-   The installation, running, or update of the application modules


> ### Note:  
> Although the MTA model is not target-specific, the MTA deployer is multitarget aware. Indeed, even when targeting a single platform \(for example, Cloud Foundry\), the MTA deployer is still needed to resolve the dependencies between the different application parts. Using an MTA deployer rather than the underlying “native” installation tools provides a single orchestrated application-deployment step which can span multiple run-time tiers on more than one target platform.

Since deployment \(for example, for testing\) is an integral part of the development process, development environments contain such functionality as well.



<a name="loio8b55a61e4ecc4a8d951d3b4f043e8349__section_jfj_q2b_b1b"/>

## MTA Architecture

An application that consists of UI and database modules, and even application code, is an example of an MTA. A Java EE application composed of Beans, Web and application modules, resource adapters etc., which are all subject to the same development life cycle and deployed across multiple computing tiers, is another example of a typical MTA. Both the application developer and the landscape administrator want to be able to manage the development, versioning, deployment, and operation of MTAs as one logical unit.

New distribution requirements apply for orchestrated cross-platform deployments. When acting as a Software-as-a-Service \(SaaS\) extension platform and employing Fiori as a Service \(FaaS\) concepts, application developers need to be able to distribute their applications across heterogeneous targets \(for example, Java Virtual Machines \(VM\), the front-end server, or the SaaS back end component\), each of which has its own deployment application programming interface \(API\), while providing a carefully managed, single application life cycle.

By adopting a model that does not required an application to depend on any formal target or technology, the MTA addresses the challenges of deploying applications to multiple targets by isolating the developer from target-specific native tools. Instead, developers describe the application's modules, any dependencies to other modules, MTAs and \(micro\) services, and any required or exposed interfaces. Application lifecycle-management frameworks that are MTA-aware can validate, orchestrate, and automate the MTA deployment process both on-premise and on Cloud platforms.



<a name="loio8b55a61e4ecc4a8d951d3b4f043e8349__section_tql_cgb_b1b"/>

## MTA Development Tools

*SAP Business Application Studio* provides "MTA-aware" development support both in the context of Cloud Foundry applications and Fiori-as-a-Service \(FaaS\) solutions. MTA-aware deployers for Cloud Foundry, provide deployment-related services; the services integrate with SAP product assembly and production, are integrated into traditional SAP transport tools, and support delivery via SAP Service Market Place for on-premise deployment.

> ### Restriction:  
> The MTA-aware tools used in each of these different use cases plan to implement the full MTA specification over a period of time. For this reason, at any point in time, each tool might reflect only a subset of the features described here; support for the features described will depend on priorities derived from the corresponding use case. For more information about the current feature scope, refer to the documentation for the respective tool.

**Related Information**  


[Create the MTA Description Files](create-the-mta-description-files-ebb42ef.md "Multi-target applications are defined in multiple descriptor files.")

[The MTA Development Descriptor](the-mta-development-descriptor-4486ada.md "Multi-target applications are defined in a design-time development descriptor.")

[The MTA Deployment Descriptor](the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

