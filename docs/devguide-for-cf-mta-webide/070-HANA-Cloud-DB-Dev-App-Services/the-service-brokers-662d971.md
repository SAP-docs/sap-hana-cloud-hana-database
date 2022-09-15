<!-- loio662d971e420b4687b5c469779f694226 -->

# The Service Brokers

Service brokers manage instances of services used by applications running in the Cloud Foundry run time.

In Cloud Foundry, the service broker is responsible for maintaining and managing instances of service brokers and all available services. Services are bound to the application that requires the services provided by a service instance. Developers can use the service broker to bind service instances to the application that wants to make use of the advertised services.

> ### Note:  
> The SAP HANA service broker is only used for SAP HANA**database-level** services, for example: schemas, HDI containers, and secure stores. The Job Scheduler service and the User Account and Authentication \(UAA\) service each has its own service broker that is used to manage instances of the corresponding service.

A dedicated application-programing interface \(API\) is provided to enable access to the service broker and any managed services; the API enables you to create and delete service instances \(as well as instances of any service brokers that control them\) and bind the services to an application. You can also use the commands `cf marketplace` and `cf services` to display a list of the currently available services, either in the marketplace or in a target organizational space.

**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[The Service-Broker API](the-service-broker-api-c1fb23c.md "Maintain and manage Cloud Foundry services and service brokers, for example: list, create, delete, bind, and update.")

[Maintaining Multitarget Application Services in Cloud Foundry](maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

