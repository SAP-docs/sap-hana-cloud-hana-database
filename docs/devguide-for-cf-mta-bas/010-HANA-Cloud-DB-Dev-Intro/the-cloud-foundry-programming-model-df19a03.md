<!-- loiodf19a03dc07e4ba19db4e0006c1da429 -->

# The Cloud Foundry Programming Model

Writing applications for deployment to Cloud Foundry.

In this section, you can find information about the following topics:

-   [Cloud Foundry Concepts](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_py4_wfm_rv)

-   [System Architecture](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_i2t_45k_qv)

-   [Authentication and Authorization](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_tm3_lxk_qv)

-   [Component Model](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_chp_lxk_qv)

-   [Client User Interface](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_myy_lxk_qv)

-   [SAP HANA Database](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__section_ggf_nxk_qv)

    Includes information about the Service Broker, HDI containers, the HDI deployer, the SAP HANA Instance Broker, and database synonyms




<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_py4_wfm_rv"/>

## Cloud Foundry Concepts

The Cloud Foundry platform runs applications; these applications belong to “spaces”, which belong in turn to “organizations”.

In the context of an organization, the platform users can be assigned special permissions in the different spaces. For example, administrators and developers need permissions to deploy and start applications. Spaces can be used to provide a secure and isolated environment for the development teams working on different projects. Applications can use various runtime “services”, for example: database services, the User Account and Authentication service \(UAA\), or a scheduler service. Each service can be offered in different configurations called “service plans”, which have different features and characteristics.

Before a service can be used by an application, it is necessary to create a service “instance” to which the application must be bound. For each type of service there is a “service broker”; the service broker executes the actions required to create and delete service instances and bind application to services. The UAA service broker, for example, implements the API for managing UAA service instances. What a service instance means technically may differ between services and service plans. A service instance can be just a configuration for a shared implementation and a separate login and data area on a shared server. In certain other cases, each service instance can have its own server.

   
  
**Basic Cloud Foundry Concepts**

 ![](images/Application_and_Services_in_Cloud_Foundry_f4e7909.png "Basic Cloud Foundry Concepts") 

Applications are deployed to the target platform by using the `push` operation of the platform API. For this reason, in Cloud Foundry parlance, applications are “pushed” to the platform. Pushing an application works as follows:

1.  First the application files are uploaded to the platform.

2.  Next, programs called “buildpacks” are executed to create archives that create the self-contained and ready-to-run executable applications.

    Some of the most typical activities executed by buildpacks are: downloading any required libraries and other dependencies, and configuring the application. Different buildpacks exist for the different target run-time environments such as Java or JavaScript/Node.js.


Applications are started as separate processes. At run time, the applications need the connection information for the services instances to which they are bound. The applications obtain this information from process-specific environment variables, which are resolved by the platform in a process known as “service wiring”. Bindings can only be created between applications and service instances in the same “space”. For scale-out scenarios, the platform can be instructed to start multiple instances of an application \(several processes\). Cloud Foundry applications are units that can be pushed, started, stopped, and bound to services. You can display a list of all the applications running in the current space with the `cf apps` command.

> ### Note:  
> Each deployed application runs in a specific run-time container.



<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_i2t_45k_qv"/>

## System Architecture

Cloud Foundry is optimized for 12-Factor applications: the new methodology for building scalable, easy-to-maintain, software-as-a-service applications. The code base for Cloud Foundry or multitarget application can be stored in an external Git repository. Applications are deployed \(pushed\) from the Git repository to the target platform and run in separate processes that can be scaled independently. The applications expose services by means of port bindings, store their configuration in the environment, and build upon backing services that are consumed over the network. Multitarget applications build upon the microservices paradigm and leverage Cloud Foundry tools and services to create, bind, and dispose of services.

Typically, the following service layers are available:

-   Backing Services

    Provide the technology on which multitarget application are built, for example:

    -   Persistence services \(databases, key-value stores, …\)

    -   Communication services \( message queues, email gateways, …\)

    -   Authentication services \(User Account and Authentication service \(UAA\)\)


-   Application Services

    Implement business logic and build upon backing services. Application services are implemented in different languages \(for example, Java or JavaScript\) for which the platform provides appropriate run-time environment \(for example, Tomcat or Node.js\). Communication between application services is always remote since the application services run in isolated containers that are managed by the platform.

-   Mashup Services

    Combining application services, mashup services expose central end points to the user interface that runs as a rich client in a Web browser. In their simplest form, mashup services perform simple URL-based routing, for example, provided by the Application Router \(`approuter`\) or the Fiori Launchpad. However, mashup services can also implement more complex scenarios, for example, the service calls seen in next-generation micro-service based platforms such as “hybris-as-a-service” \(YaaS\).




<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_tm3_lxk_qv"/>

## Authentication and Authorization

When a user sends an unauthenticated request to the central entry point of a multitarget application such as the Application Router \(or any other mashup service\), the user is redirected to the User Account and Authentication \(UAA\) service. The UAA can handle different types of authentication methods, for example: basic \(user name and password\) and SAML assertions. The UAA does not store user credentials itself; relies on an external user store, for example: SAP Cloud Identity or also the SAP HANA database. Upon successful login, the UAA issues an OAuth token that can then be forwarded in all calls to further application services to authenticate that user. This way, application services only need to support one single authentication method: OAuth tokens. By contrast, authentication at backing services like databases is based on technical users that are authenticated with user credentials \(name and password\) provided to the application in its environment. The user’s OAuth token can also be forwarded to a backing service such as the SAP HANA database for user-based authorizations.

OAuth tokens not only provide a unified authentication method, they also contain the user’s authorization in the form of a set of permissions, called “scopes”. Authorization scopes are managed in the UAA and can be derived for example from SAML roles or attributes. Based on these scopes, applications perform functional authorization checks on all service layers, either modeled or implemented in code. Instance-based authorization is based on attributes that can be included in the OAuth token but, more often, are managed by the application itself.



<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_chp_lxk_qv"/>

## Component Model

In a microservice architecture such as the one provided with Cloud Foundry, the following rules apply:

-   Service life cycle

    Each service has its own independent life cycle and must provide stable service interfaces for robust integration with other services that may be upgraded or even completely replaced at different times.

-   Service isolation and independence

    Services are isolated from each other and share nothing. If common frameworks or libraries need to be shared, they are embedded redundantly \(and possible in different versions\) in each service.

-   Service language and run time

    Services can be implemented in any available language and run in any available run time environment, independently of the languages and run-time environments used to implement other services.

-   Service extensions

    Services can provide extensions to other services, either by wrapping or replacing existing services with extended implementations or implementing predefined extension point service interfaces. Additionally, new applications can be aggregated from existing and new services by combining them in a “mashup” service.


To facilitate the deployment of groups of services which in their specific combination constitute a business application that is managed as a whole, Multi-Target-Applications \(MTAs\) that can be deployed in one step and share the same life cycle but otherwise retain their independence. This approach brings an important operations benefit that is supported in the Cloud.



<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_myy_lxk_qv"/>

## Client User Interface

The UI model assumes a rich client that communicates via HTTP with application services in the Cloud \(for example using the OData protocol for UI5 based user interfaces\). The SAP standard UI technologies, Fiori and UI5, follow this model. To overcome the same-origin policy restriction implemented in Web browsers, the UI client connects to a central entry point such as the Application Router or a mashup service that acts as reverse proxy and routes inbound requests to the appropriate application service. Native clients that are not subject to the restrictions of a Web browser should follow this model to simplify configuration, hide internal implementation details, and provide central login \(and logout\) services.

The same reasons \(of simplicity, implementation details, and central login services\) also apply when deciding whether to use Cross-Origin Resource Sharing \(CORS\) in the browser as an alternative solution to the same-origin policy restriction. Fiori applications can be served by a central Application Router that reads UI content and routing configuration from the layered repository \(LRep\) backing service. As a result, Fiori applications do not need to deploy a dedicated Application Router; they just have to deploy their Fiori content to the shared LRep. By contrast, plain \(non-Fiori\) UI5 applications embed their UI content in their own Application Router which also acts as a Web server for content packaged with its own container; these UI5 applications do not rely on a backing service as an external content repository.



<a name="loiodf19a03dc07e4ba19db4e0006c1da429__section_ggf_nxk_qv"/>

## SAP HANA Database

SAP provides support for SAP HANA as the database backing service.

-   [SAP HANA Service Broker](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__subsection_sxv_bgv_pv)

-   [HDI Container](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__subsection_xbw_bgv_pv)

-   [HDI Deployer](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__subsection_dgw_bgv_pv)

-   [Synonyms](the-cloud-foundry-programming-model-df19a03.md#loiodf19a03dc07e4ba19db4e0006c1da429__subsection_hbf_gjv_pv)




### SAP HANA Service Broker

Service Brokers are the components that manage backing services. An application that requires a particular instance of a backing service defines this dependency, and the platform interacts with the service-specific Service Broker to create a dedicated instance for the application and binds the application to it.

The SAP HANA Service Broker provides various types of service instances according to the service plan the application requires. First and foremost, these are HDI containers; however, plain schemata are also possible. Both types of service plan provide isolation in a shared database so that applications do not get exclusive access to a complete SAP HANA system; the applications have access to a container which allows multiple applications \(or different versions of one application\) to share an SAP HANA system.

When an application is started, the platform passes the connection parameters and credentials of the container to the application in its environment. For this reason, applications do not need to hard-code the names of any schema or provide access to global tables; applications are isolated within their assigned container.

Multiple applications within one MTA may share a container if they share the same life cycle. However, different MTAs that have different life cycles are assigned different containers.



### HDI Container

HDI Containers are a special type of database schemata that manage their contained database objects. These objects are described in design-time artifacts that are deployed by the HDI Deployer application. HDI takes care of dependency management and determines the order of activation; HDI also provides support for upgrading existing run-time artifacts when their corresponding design-time artifacts are modified.

Applications that use other persistency frameworks are obliged to fall back on the use of plain schemata. These frameworks can then directly execute DDL statements, something that is not allowed in HDI Containers, where the management of database objects is performed exclusively by HDI.



### HDI Deployer

The HDI Deployer is an application that is included in an MTA and is used to deploy HDI design-time artifacts to the respective HDI containers. When an MTA is deployed, the HDI Deployer application is pushed first so that it can “prepare” the SAP HANA persistence; by the time defined services are started, the HDI container is ready for use.

The same pattern used for the HDI Deployer is also applied with other backing services. For example, the SDS Deployer deploys Streaming Analytics artifacts, and the LRep Deployer deploys FLP content to the Layered Repository. The common approach is that dedicated applications initialize backing service instances for MTAs and are coordinated by the deployment process as defined in the MTA deployment descriptor.

In addition to the stand-alone deployer application, HDI also offers an API that enables applications to create database objects at run time by generating design-time artifacts within the application and deploying them into their container with the HDI. In this way, it is possible to extend the persistence in run-time authoring scenarios, for example, field extensibility or dynamic rule generation.



### Synonyms

In Cloud Foundry, SAP HANA multitarget applications only connect to their own database container \(or in the case of multi-tenancy: their containers\); a multitarget application cannot connect directly to containers bound to other applications. Explicit schema references are not allowed or even possible because they are dynamically created and managed by the SAP HANA Service Broker. This is in line with the decentralized data management concept in a micro-services architecture.

However, from a performance perspective and also from a data-consistency perspective, replication is not always the best answer. So, the SAP HANA database provides synonyms that enable an application to perform a controlled “break out” from its own container to related containers. A database synonym is similar to a symbolic link; from an application's perspective, the access always happens within its own container, but the synonym may link to an object in another container. A container that exposes objects to other containers must explicitly grant access to consuming containers in order to create synonyms. The container exposing objects with synonyms has control over the set of objects which can be accessed. As a result, the exposing container has the means to define an application programming interface \(API\) at the database level, for example, by creating an allow-list for only public objects in a database role that is granted to the consuming container.

> ### Note:  
> The complete setup and deployment of synonyms is done by the HDI Deployer; it is not necessary for application developers to configure this manually.

**Related Information**  


[The Cloud Foundry Programming Model](the-cloud-foundry-programming-model-df19a03.md "Writing applications for deployment to Cloud Foundry.")

