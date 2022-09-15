<!-- loio26c3446247864a8a89d0d2eb6aff6351 -->

# Create a Service Key

A service key generates credentials to that enable direct communication with a service instance.



<a name="loio26c3446247864a8a89d0d2eb6aff6351__prereq_q5r_3wv_gnb"/>

## Prerequisites

-   You have already installed the CF command-line interface \(CLI\)
-   You know the name of the service instance for which you want to create a service key.
-   You have `space developer` authorizations in the Cloud Foundry space where you want to create the service key.



## Context

You can use service keys to generate the credentials required to communicate directly with a service instance you have instantiated. If you have configured a service key for your service, then local clients, applications in other spaces, or entities outside your deployment can use this service key to access your service instance.

To use the Cloud Foundry command-line client to create a service key for a service instance, perform the following steps:



## Procedure

1.  Open a command shell.

    > ### Tip:  
    > You can use the console in *SAP Business Application Studio*, too.

2.  Log in to the Cloud Foundry space where you want to create the service key.

    Use the command `cf login -a` to log in to Cloud Foundry, as illustrated in the following example:

    ```
    cf login -a https://api.[…].ondemand.com
    ```

    You will need to specify the following parameters when prompted:

    -   User credentials: name and password
    -   Target space: Cloud Foundry organization and space

3.  Create the service key.

    Use the command `cf create-service-key` to generate a key for your service instance, as illustrated in the following example:

    ```
    cf create-service-key <SERVICE_INSTANCE> <SERVICE_KEY> {-c PARAMETERS_AS_JSON}
    ```

    You will need to specify the following parameters:

    -   *<SERVICE\_INSTANCE\>* 

        The name of the service instance for which you want to generate a service key

    -   *<SERVICE\_KEY\>*

        The name of the new service key you want to create

    -   \{-c PARAMETERS\_AS\_JSON\}

        \(Optional\) Provide service-specific configuration parameters in a valid JSON object.

        > ### Tip:  
        > These parameters can also be defined in the deployment descriptor \(`mtad.yaml`\) of a multitarget application, as described below.


    Alternatively, you can create a service key in either of the following ways:

    -   SAP BTP cockpit

        You can use the SAP BTP cockpit to manage service keys, for example: display a list of existing service keys, or create a new service key. Navigate to the *Service Instances* pane, select a service instance, and choose *Service keys* \> *Create Service Key*.

    -   The HDI deploy service

        You can use the `service-keys` parameter in a multitarget application's \(MTA\) deployment descriptor \(`mtad.yaml`\) to configure the deployment service to create and update the corresponding service keys during the creation or update of a service instance. The special `service-keys` parameter must be added to the service instance to which it corresponds in the `resources` section of the multitarget application's deployment descriptor, as illustrated in the following example. For more information about the deployment descriptor, see *Related Information* below.

        > ### Sample Code:  
        > Service-Key Configuration in the MTA Deployment Descriptor \(`mtad.yaml`\)
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


4.  Consume an existing service key.

    You can configure a multitarget application to use an existing service key as an alternative to a service binding. In this way, it is possible to enable an application to use a service key's credentials and consume the corresponding service. The existing service keys are modeled as a resource of type `org.cloudfoundry.existing-service-key`. An MTA module can depend on the defined service resource which results in the injection of the reused service-key credentials into the consuming application's environment.

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
    >       service-name: service-a # the service that the key belongs to 
    >       service-key-name: test-key-1 # Default value is the resource name 
    > ```


**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[The MTA Deployment Descriptor](../030-HANA-Cloud-DB-Dev-Deployment/the-mta-deployment-descriptor-33548a7.md "Description of the deployment options for a multitarget application.")

