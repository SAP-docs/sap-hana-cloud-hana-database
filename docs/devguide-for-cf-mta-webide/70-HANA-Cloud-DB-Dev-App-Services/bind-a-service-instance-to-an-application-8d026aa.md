<!-- loio8d026aab67124191b694d430ba03bc0d -->

# Bind a Service Instance to an Application

Bind a Cloud service instance to your multitarget application.



<a name="loio8d026aab67124191b694d430ba03bc0d__prereq_q5r_3wv_gnb"/>

## Prerequisites

-   You have already installed the CF command-line interface \(CLI\).
-   You have created the service instance that you want to bind to an application.
-   You have deployed the application to the same space where you created the service instance.



<a name="loio8d026aab67124191b694d430ba03bc0d__context_vmv_q1w_gnb"/>

## Context

In Cloud Foundry on SAP Business Technology Platform \(SAP BTP\), application developers can make use of a catalog of services managed by a service broker, for example, for the SAP HANA Deployment Infrastructure services, for job schedules, or for user accounts and OAuth clients. To make use of a service, an instance of the service must be created and an the application must be bound to the specified service instance.

> ### Note:  
> You can also use the SAP BTP cockpit to bind applications to service instances. Navigate to the *Service Instances* pane, select a service instance, and choose *...* \> *Bind Application*.

To use the Cloud Foundry command-line client to bind an deployed application to a service instance, perform the following steps:



<a name="loio8d026aab67124191b694d430ba03bc0d__steps_wmv_q1w_gnb"/>

## Procedure

1.  Open a command shell.

2.  Bind the application to a named service instance.

    Use the CF command `bind-service` to bind your application to a service instance, as shown in the following example:

    ```
    cf bind-service <APP_NAME> <SERVICE_INSTANCE>  {-c PARAMETERS_AS_JSON}
    ```

    You will need to specify the following parameters:

    -   *<APP\_NAME\>*

        The name of the application that you want to bind to a service instance

    -   *<SERVICE\_INSTANCE\>* 

        The name of the service instance to which you want to bind your application

    -   \{-c PARAMETERS\_AS\_JSON\}

        \(Optional\) Provide service-specific configuration parameters in a valid JSON object.



