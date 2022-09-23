<!-- loio33e3c5926feb4098a32edcaa7290c3d1 -->

# Maintaining Multitarget Application Services in Cloud Foundry

In Cloud Foundry, applications can make use of services managed by a service broker.

Developers of applications running in Cloud Foundry on SAP Business Technology Platform \(SAP BTP\) have access to a catalog of services managed by a service broker, for example, for the SAP HANA Deployment Infrastructure services or for user accounts and OAuth clients. To enable an application to use a service, it is necessary to create an instance of the service and then bind the application that requires the service to the new service instance.

In a PaaS environment, all external dependencies, such as databases, messaging systems, files systems, and so on, are provided as services. In the Cloud Foundry environment, services are offered in a market place, from which users can create service instances on-demand. A service instance is a single instantiation of a service running on SAP BTP. Service instances are created using a specific service plan, which is a configuration variant of a service.

To browse the contents of the service catalog, you can use the following tools:

-   Service Marketplace:
    -   Use the Cloud Foundry CLI

        Requires a logon to Cloud Foundry

        -   In a command shell

        -   In the console in SAP Web IDE Full-stack

    -   Use the SAP BTP cockpit GUI

        Requires a logon to SAP BTP cockpit


-   SAP Discovery Center



<a name="loio33e3c5926feb4098a32edcaa7290c3d1__section_jjq_whw_gnb"/>

## Service Discovery Center

The SAP Discovery Center provides a convenient way of browsing the SAP BTP services, tools, application-programming interfaces \(API\), and even applications that help you integrate and extend your solutions, optimize your business processes, and create an engaging digital experience. You can view all available services, and filter the results displayed according to the following criteria:

-   License model: CPEA, subscription, trial
-   Provider: Amazon Web Services \(AWS\), Microsoft Azure, Google Cloud, or SAP
-   Geographical region: Europe, US, Pacific, ...

For more information about services in the SAP Discovery Center, see *Related Information* below.



<a name="loio33e3c5926feb4098a32edcaa7290c3d1__section_tw3_nzv_gnb"/>

## Service Marketplace

Services brokers are advertised in the Cloud Foundry marketplace, whose contents you can list with the `cf marketplace` command, which is included in the CF command-line client, as illustrated in the following example:

> ### Sample Code:  
> Services in the Service Marketplace
> 
> ```
> $ cf marketplace
> Getting services from marketplace in org acme / space devel as admin...
> OK
> 
> service              plans                        description                     broker
> -------------------------------------------------------------------------------------------------------
> hana                 hdi-shared, schema           SAP HANA database               sm-hana-broker...
>                      securestore
> xsuaa                application, apiaccess       Manage app authorizations...    sm-xsuaa-...
> application-logs     lite                         Create, store, access...        sm-sleeve-broker...
> ... 
> autoscaler           standard                     Automatically increase or...    sm-autoscaler-brok...
> auditlog-api         default                      Audit log API...                sm-auditlog-api-...
> auditlog-management  default                      Retrieve logs and change...     sm-auditlog-manage...
> ...
> metering-service     default                      Record usage data for...        sm-metering-broker...
> ...
> hana-cloud           hana                         Leverage in-memory data...      sm-hana-cloud-...
> service-manager      subaccount-admin,            Central registry for services,  sm-service-manager...
>                      subaccount-audit, container  service brokers, and platforms
> ...
> ```

To make a service available to your multitarget application, you must create an instance of the chosen service, for example, with the `cf create-service` command. The service instance can then be bound to any application that requires the service, for example, using the `cf bind-service` command.

> ### Tip:  
> The SAP BTP cockpit also provides access to the Service Marketplace with a graphical user interface.

To view services in the SAP BTP cockpit, navigate to the Cloud Foundry space where you want to use the service and choose *Services* \> *Service Marketplace*. Here you can find a detailed overview of each service along with information about any service plans, how you can subscribe, along with the tools needed to create a service instance and bind it to an application. You can also display a list of the current bindings between applications and service instances.



<a name="loio33e3c5926feb4098a32edcaa7290c3d1__section_xr1_jzv_gnb"/>

## Service Plans

For more details of an individual service, including a description of any service plans, use the `cf marketplace` command with the option <code>-s <i class="varname">&lt;service name&gt;</i></code>. The following examples display details of the `hana` service:

> ### Sample Code:  
> Services in the Service Marketplace
> 
> ```
> $ cf marketplace -s hana
> Getting service plan information for service hana as admin...
> OK
> 
> service plan   description                                 free or paid
> 
> hdi-shared     HDI container on a HANA database            free
> schema         Schema on a HANA database                   free
> securestore    User with permissions to use secure store   free
> ```

> ### Tip:  
> The service plan is mapped to a corresponding application “resource type” that is typically specified in the `resources` section of the multitarget application's deployment descriptor \(`mtad.yaml`\).

For example, the “`hana`” service plan “`hdi-shared`” is mapped to the resource type “`com.sap.xs.hdi-container`”; the “`xsuaa`” service plan “`application`” is mapped to the resource type “`com.sap.xs.uaa-application`”.



<a name="loio33e3c5926feb4098a32edcaa7290c3d1__section_szh_2zv_gnb"/>

## Service Keys

To integrate services with applications, the service credentials must be delivered to the application, for example, by creating a service instance and binding the service instance to your application. Alternatively, you can use service keys to generate credentials that enable direct communication with a service instance. For more information about service instances and service keys, see *Related Information* below.



<a name="loio33e3c5926feb4098a32edcaa7290c3d1__section_esc_1zv_gnb"/>

## User-Provided Services

The Cloud Foundry environment also allows you to work with user-provided service instances. User-provided service instances enable developers to provide services that are not available in the marketplace with their applications running in the Cloud Foundry environment. You can use the Cloud Foundry CLI to create a user-provided service, for example, with the `cf create-user-provided-service` command. After creation, an instance of a user-provided service behaves in exactly the same way as a service instance that is created through the market place. For more information about creating user-defined services including how to ensure the correct forwarding of requests to any routes that are bound to the service, see the help provided by the Cloud Foundry CLI, for example, using the command `cf help create-user-provided-service`.

**Related Information**  


[Browse Services in the SAP Discovery Center](https://discovery-center.cloud.sap/viewServices)

[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Service Plans and Resources](service-plans-and-resources-0393ce3.md "A service plan is a particular type of service (for example, a database configuration) that is available for use.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Create a Service Key](create-a-service-key-26c3446.md "A service key generates credentials to that enable direct communication with a service instance.")

