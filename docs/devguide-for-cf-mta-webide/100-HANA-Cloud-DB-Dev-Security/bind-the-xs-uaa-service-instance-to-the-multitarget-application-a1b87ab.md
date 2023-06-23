<!-- loioa1b87ab603ba4220ae2c920c7acac4a6 -->

# Bind the XS UAA Service Instance to the Multitarget Application

You must bind the UAA service instance you create to the multitarget application that is going to use it.



## Context

You must bind the service instance that acts as OAuth 2.0 client to your multitarget application. The name of the service is defined in the `services` property in the application's manifest file \(`manifest.yml`\). The manifest file is located in the root folder of your multitarget application, for example `node-hello-world`.



## Procedure

Bind an application to a service instance:

<code>cf bind-service <i class="varname">&lt;APP_NAME&gt;</i> <i class="varname">&lt;SERVICE_INSTANCE&gt;</i></code>

> ### Example:  
> `cf bind-service hello-world xsuaa`

You can now deploy your application with the authorization artifacts that were created earlier.

**Related Information**  


[Create a Service Instance](../070-HANA-Cloud-DB-Dev-App-Services/create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Application Routes and Destinations](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-routes-and-destinations-875809c.md "The application router is the single point of entry for an application.")

