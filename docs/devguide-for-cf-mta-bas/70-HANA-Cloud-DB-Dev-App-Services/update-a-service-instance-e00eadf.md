<!-- loioe00eadf291424e49935b460d2f2b3902 -->

# Update a Service Instance

Update configuration details of an existing service instance.



## Context

You can modify details of an existing service and make the modified service available to the applications that use it. As part of the update operation, you can perform the following tasks:

-   Change the service plan associated with a service

-   Modify the service configuration

    Configuration details can be provided either in a JSON formatted file or as a JSON-compliant string as an argument on the command line.


To update the configuration of an existing service plan in the Cloud Foundry application run time, perform the following steps:



## Procedure

1.  Log on to the Cloud Foundry run time where the service that you want to update is running.

    <code>cf login -a https://<i class="varname">&lt;API end point&gt;</i> -u <i class="varname">&lt;Username&gt;</i> -p <i class="varname">&lt;Password&gt;</i> -o <i class="varname">&lt;myorg&gt;</i> -s <i class="varname">&lt;myspace&gt;</i></code> 

2.  Check that the service instance you want to update is running.

    To display a list of the service instances running in the current organization and space, run the following command in a command shell:

    `cf services`

    > ### Output Code:  
    > ```
    > cf services
    > 
    > Getting services in org "myorg" / space "SAP" as XSMASTER...
    > Found services:
    > 
    > name                         service   plan          bound apps
    > ----------------------------------------------------------------------
    > hdi-container                hana      hdi-shared
    > hdi-schema                   hana      schema
    > uaa                          xsuaa     default
    > deploy-service-ss            hana      securestore   deploy-service
    > deploy-service-database      hana      schema        deploy-service
    > deploy-service-uaa           xsuaa     default       deploy-service
    > product-installer-database   hana      schema        product-installer
    > product-installer-uaa        xsuaa     default       product-installer
    > ```

3.  Update details of an existing service plan.

    You can change the service plan associated with an existing service.

    > ### Restriction:  
    > It is not possible to update the service plan assigned to an instance of the XS User Account and Authentication \(XSUAA\) service.

    To change the service plan associated with a running service, use the `cf update-service` command as follows:

    <code>cf update-service <i class="varname">&lt;SERVICE_INSTANCE&gt;</i> -p <i class="varname">&lt;NEW_SERVICE_PLAN&gt;</i> </code> 

4.  Update details of an existing service's configuration.

    Some services are configured with a service descriptor. For example, the XSUAA service for user authentication is configured using the security descriptor `xs-security.json`. You can change selected details of the security configuration and update the service with the modified configuration.

    To modify details of an existing XSUAA service's security configuration, use the `cf update-service` command as follows:

    <code>cf update-service <i class="varname">&lt;SERVICE_INSTANCE&gt;</i> -p <i class="varname">&lt;SERVICE_PLAN&gt;</i> -c xs-security.json</code>

    > ### Restriction:  
    > When updating the configuration of the XSUAA service, you can add or delete any defined scopes, any security-related attributes, and any role templates. However, you can only **modify** the following elements of an existing service's security configuration:
    > 
    > -   A security scope's description and “granted applications”
    > -   A security attribute's description
    > 
    >     When updating the XSUAA service, it is not permitted to change the value type of an attribute defined in the `xs-security.json` application security descriptor.
    > 
    > -   A role template's description, scope reference, or attribute reference


**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Set up Application Security](https://help.sap.com/viewer/b9902c314aef4afb8f7a29bf8c5b37b3/2022_2_QRC/en-US/b8236393290048dda17b4545d17eac66.html "Help ensure a multitarget application is protected from Web-based attacks.") :arrow_upper_right:

