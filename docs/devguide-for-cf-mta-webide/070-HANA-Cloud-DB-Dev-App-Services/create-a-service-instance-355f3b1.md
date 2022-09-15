<!-- loio355f3b1ded1c462d932835691fe26633 -->

# Create a Service Instance

Make a service instance available to applications.



<a name="loio355f3b1ded1c462d932835691fe26633__prereq_q5r_3wv_gnb"/>

## Prerequisites

-   You have already installed the CF command-line interface \(CLI\)
-   You have `space developer` authorizations in the Cloud Foundry space where you want to create the service key.



## Context

Developers must create an instance of a service before it can be used and then bind the service to the application that needs to use it. The service instance also requires a **service broker**.

To create an instance of a service controlled by a service broker, perform the following steps:



## Procedure

1.  Create an instance of a **service broker** in the space where its managed services are required.

    > ### Tip:  
    > Standard service brokers that are available across one or more organizations can only be created by users with administrator privileges, which Cloud users do not have. Space developers, however, can create a space-specific service broker by using the `--space-scoped` option.

    The service-broker instance requires a name, for example, “myServiceBroker”:

    <code>cf create-service-broker --space-scoped <i class="varname">&lt;myServiceBroker&gt;</i> <i class="varname">&lt;USER&gt;</i> <i class="varname">&lt;PASSWORD&gt;</i> http://<i class="varname">&lt;service-broker-url&gt;</i></code>

2.  Check that the new service instance is up and running.

    Check details of the new service by displaying a list of the service instances available in the service **market place**:

    `cf marketplace`

3.  Create an instance of the **service**.

    The new service instance requires a name, for example, “myService”and is controlled by the service-broker instance you already created:

    <code>cf create-service myService default <i class="varname">&lt;myServiceInstance&gt;</i></code>

    > ### Tip:  
    > In this example of how to create a service, “`default`” refers to the service plan to use. The HDI and UAA services provide additional service plans.

4.  Bind the service instance to an application.

    <code>cf bind-service <i class="varname">&lt;myApp&gt;</i> <i class="varname">&lt;myServiceInstance&gt;</i></code>

5.  Verify that the application has been bound to the service instance.

    To confirm the application-service binding, check the environment variable *<VCAP\_SERVICES\>*.

    <code>cf env <i class="varname">&lt;myApp&gt;</i></code> 

6.  Unbind the service instance from an application.

    <code>cf unbind-service <i class="varname">&lt;myApp&gt;</i> <i class="varname">&lt;myServiceInstance&gt;</i></code>

7.  Delete the service instance.

    <code>cf delete-service <i class="varname">&lt;myServiceInstance&gt;</i></code>

8.  Remove the service broker you created.

    <code>cf delete-service-broker <i class="varname">&lt;myServiceBroker&gt;</i></code>

9.  Verify that the broker has been deleted.

    To confirm that the service broker has been removed, check the service marketplace:

    `cf marketplace`


**Related Information**  


[The Service-Broker API](the-service-broker-api-c1fb23c.md "Maintain and manage Cloud Foundry services and service brokers, for example: list, create, delete, bind, and update.")

[Maintaining Multitarget Application Services in Cloud Foundry](maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

