<!-- loiod8226e641a124b629b0e8f7c111cd1ae -->

# SAP HANA Multitarget Applications

Multitarget Applications comprise several modules that contain content for a distinct run-time environment.

Business applications are typically composed of several parts that are built with different technology for different run-time environments. For example, an application could contain static Web content that runs in the browser, server-side Java code that runs in a Java Enterprise server, OData service definitions for an OData provisioning run time, and also database content such as tables, views, and procedures. Since all these parts belong to the same business application, they are developed, delivered, configured, and deployed together. Often the various different parts have dependencies and, as a result, need to be deployed to the specified target in a given order. To manage such applications, SAP has introduced the concept of a Multitarget Application \(MTA\).

Each MTA consists of one or more modules, and each MTA module is a separate “micro” application, which can be pushed to a target deployment platform, bound to any required services, and so on. MTA modules can expose certain attributes for use by other modules and they can have dependencies on other modules or resources, too. A module could, for example, depend on a REST API of some other module, or on the tables and views defined by a database module.

> ### Tip:  
> Examples of resources, on which modules can depend are: services instances such as the SAP HANA User Account and Authentication \(UAA\) instance or an SAP HANA service instance.

The MTA application model with modules and dependencies is specified in a MTA deployment descriptor file. The MTA deployment descriptor lists the different MTA modules with their technical type, their dependencies, and any required parameters. This information is used to ensure that the modules are deployed in the right order, that the required dependencies \(such as services\) exist, and for setting up the connections required between the modules. The application files and metadata such as descriptors and manifests are collected into an MTA, which can be packaged in \(and delivered as\) an archive. The MTA archive also includes information for configuring services, for example the security configuration for the UAA instance.

In the folder structure of the MTA archive, each module has its own folder. For example, an MTA could have the following base-level folders:

-   `web/`

    A folder for static Web content and the application router configuration

-   `java/`

    A folder for a Java application

-   `js/`

    A folder for a Node.js application \(including XS JavaScript in the compatibility layer\)

-   `db/`

    A folder for the SAP HANA database artifacts, for example: tables, views, stored procedures, Calculation Views, and so on...


> ### Tip:  
> The mapping of folders to modules is described in an MTA manifest file.



<a name="loiod8226e641a124b629b0e8f7c111cd1ae__section_j54_s2g_t1b"/>

## Application Pattern

SAP is promoting a pattern for building applications that can run either on-premise or in the Cloud. The logical view of this pattern shown in the diagram below represents the architecture of a business application, a term used in the context of Cloud Foundry to distinguish such applications from single applications. For an end-user's perspective, a business application is a collection of microservices, service instances, bindings, and routes which, taken as a whole, represent a usable Web-based application. These microservices, services instances, bindings, and routes are created by communicating with the Platform Controller \(for example, using a command-line interface\).

> ### Tip:  
> SAP provides a set of libraries, services, and component communication principles which are used to implement \(multi-tenant\) business applications according to the application pattern described here.

![](images/SAP_MTA_Application_Patterns_b8b8096.png)

-   Microservices

    Microservices are created by "pushing" code to the target platform resulting in the deployment of a number of microservice instances each running in a separate container

-   Services

    Services are exposed to applications by injecting access credentials into the application environment by means of service bindings. Applications are bound to a service instance which describes the configuration and credentials required to consume a service. Services instances are managed by a service broker which must be provided for each service \(or for a collection of services\).

    -   XS User Account and Authentication \(UAA\) service

        The UAA service is a multi-tenant identity management service used in Cloud Foundry. The UAA's primary role is as an OAuth2 provider, issuing tokens for client applications to use when they act on behalf of Cloud Foundry users. The UAA can also authenticate users with their Cloud Foundry credentials and can act as an SSO service using those credentials \(or others\). As well as various other management functions, the UAA provides endpoints for managing user accounts and for registering OAuth2 clients.

    -   Platform and Business Services

        Along with backing services such as SAP HANA, PostgreSQL, Redis, Audit Log, Application Log, etc., the platform also provides various business services, for example, to enable you to retrieve currency exchange rates. Applications can also make use of so-called "user-provided" services that are not managed by the platform. In all these cases, applications can bind and consume the required services in a similar way.


-   Routes

    Mapped to applications and define the URL to use to access the business application




## Application Deployment

The deploy service is, as the name suggests, used to deploy MTAs on the application run-time platform. The deployment service is an application for the deployment of MTA archives or directory structured in the same way as an MTA archive. The deploy service can be invoked from the command-line client, for example, with the `cf deploy` command.

> ### Note:  
> The Cloud Foundry plug-in multiapps must be installed to manage SAP MTAs in Cloud Foundry. For more information, see *Related Information* below.

When the deploy service receives an MTA, it first validates it for consistency. Next it ensures that the required service instances exist and creates them if necessary. It deploys the different modules in the right order, based on the dependency information in the MTA descriptor. The deploy service also sets up environment variables with the information that is needed by the different modules to connect to required modules at run time. The deploy service executes those tasks required for the successful deloyment of the MTA, for example, creating service instances or pushing applications to the desired target run-time platform.

The deploy service supports transactional execution which includes the ability to restart a multi-step deployment that was interrupted. Multiple instances of the deploy service can be started for high availability. The deploy service also supports so-called “zero-down-time” updates, for example, with the blue-green deployment update described in the Cloud Foundry documentation.

**Related Information**  


[The Cloud Foundry Programming Model](the-cloud-foundry-programming-model-df19a03.md "Writing applications for deployment to Cloud Foundry.")

[The Multiapps Plug-in for Cloud Foundry](https://plugins.cloudfoundry.org/#multiapps)

[Configuring the HDI Deployer](../040-HANA-Cloud-DB-Dev-Persistence-Model/configuring-the-hdi-deployer-d5bf65e.md "Set up and use the Node.js-based HDI Deployer in Cloud Foundry.")

