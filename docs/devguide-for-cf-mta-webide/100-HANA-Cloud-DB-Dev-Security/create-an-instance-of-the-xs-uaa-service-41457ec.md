<!-- loio41457ec69606454a9cebeb8360e266ed -->

# Create an Instance of the XS UAA Service

Use the service broker to create an instance of the `xsuaa` service.



## Context

If you want to grant users access to an application, you must create an instance of the XS User Account and Authentication service \(XSUAA\) for this application; the XSUAA service instance acts as an OAuth 2.0 client for the bound application.



## Procedure

1.  Create a service instance based on the `xsuaa` service and using the service plan “default” and the security descriptors defined in the `xs-security.json` file.

    <code>cf create-service <i class="varname">&lt;service _name&gt;</i> <i class="varname">&lt;service_plan&gt;</i> <i class="varname">&lt;service_instance_name&gt;</i> -c xs-security.json</code>

    > ### Example:  
    > `cf create-service xsuaa default authorizationtest-uaa -c xs-security.json`

    The name of the OAuth 2.0 client you created is similar to the following example: ***sb-577a76db-21f9-412b-ad4e-a740f3991136***.

2.  Display a list of the OAuth 2.0 clients that are available.

    To check that your new service instance is among the list of currently available OAuth 2.0 clients, log on to the UAA using the following URL and a known UAA user:

    <code>http://<i class="varname">&lt;host_name&gt;</i>:<i class="varname">&lt;uaa port&gt;</i></code>

    1.  Log on to Cloud Foundry.

        <code>cf login -a <i class="varname">&lt;api_endpoint&gt;</i> -u <i class="varname">&lt;username&gt;</i> -p <i class="varname">&lt;password&gt;</i></code>

    2.  List the applications and services currently running.

        The information displayed in the console includes URL and port numbers.

        `cf apps`

        `cf services`


3.  Update details of an existing XSUAA service's configuration.

    The XSUAA service for user authentication is configured using the security descriptor `xs-security.json`. You can change selected details of the security configuration and update the XSUAA service with the modified configuration.

    To modify details of an existing XSUAA service's security configuration, use the `cf update-service` command as follows:

    <code>cf update-service <i class="varname">&lt;SERVICE_INSTANCE&gt;</i> -c xs-security.json</code>

    > ### Restriction:  
    > It is not possible to update the service plan assigned to an instance of the XS User Account and Authentication \(XSUAA\) service.

    When updating the configuration of the XSUAA service, you can add or delete any defined scopes, security-related attributes, or role templates. However, **modifications** are only permitted to the following elements of an existing service's security configuration:

    -   A security scope's description and “granted applications”
    -   A security attribute's description

        When updating the XSUAA service, it is not permitted to change the value type of an attribute defined in the `xs-security.json` application security descriptor.

    -   A role template's description, scope reference, or attribute reference

    > ### Restriction:  
    > When updating the configuration of an XSUAA service instance, it is only possible to delete an attribute reference; it is not possible to add or modify them.


**Related Information**  


[Create a Service Instance](../070-HANA-Cloud-DB-Dev-App-Services/create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Modifications and Restrictions for XSUAA Service Updates](modifications-and-restrictions-for-xsuaa-service-updates-ca1ac42.md "Restrictions apply to which parts of the application's security description you can change and apply when updating an instance of the XSUAA service.")

