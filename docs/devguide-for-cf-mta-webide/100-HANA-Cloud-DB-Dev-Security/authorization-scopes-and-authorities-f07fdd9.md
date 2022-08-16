<!-- loiof07fdd9e415f4c9cb338ff7daecc6ce6 -->

# Authorization Scopes and Authorities

An overview of the configuration required to enable an application to perform a task with the authority of another application.

In the application run-time environment, it is possible to authorize one application to make calls to other applications to trigger an action on the other application's behalf. For example, you could configure one application to trigger a scheduled job that cleans up unwanted logs and collects run-time "garbage" on behalf \(and with the authority\) of another application. In this scenario, one application grants the authorities, and another application requests the authorities, accepts them, and uses the authorities to access the granting application and perform tasks on the granting application's behalf. By enabling applications to grant and use authorities in this way, it is possible to ensure that not only the communication between the applications but also the execution of the task itself run securely; that is, with the required permissions and in the correct application run-time container.

To enable the exchange and use of authorities between applications, at least two applications are required: one that grants the authority, and a second, named, application that performs the desired action on behalf of the application granting the authority. In the security descriptor \(`xs-security.json`\) of the application granting a named scope as an authority, you need to flag the specified scope as “grantable”, for example, using the property <code>“grant-as-authority-to-apps”</code>, as illustrated in the following example:

> ### Code Syntax:  
> Granting Scopes as Authorities \(`xs-security.json` of Granting Application\)
> 
> ```
> "scopes": [
>         {
>           "name": "$XSAPPNAME.foreigncall",
>           "description": "Enable Calls into Granting App",
>           "grant-as-authority-to-apps": ["RequestingApp"]
>         },
> ]
> ```

In the application that requires the granted authority, you need to add the property <code>“authorities”</code> to the requesting application's security descriptor and either list the individual, named authorities that can be used, or specify that **all** authorities granted by another application can be accepted and used, as illustrated in the following example:

> ### Code Syntax:  
> Requesting and Using Scopes as Authorities \(`xs-security.json` of Requesting Application\)
> 
> ```
> "authorities":["$ACCEPT_GRANTED_AUTHORITIES"],
> ```

Each of the applications involved in the exchange of authorities must be bound to its own an instance of the XS User Account and Authentication \(UAA\) service; the service binding creates the respective OAuth 2.0 clients and enables secure communication between the applications involved in the exchange of authorities. The UAA binding also enables the application requesting an authority to authenticate itself at the granting application **on its own behalf** using the OAuth 2.0 client credentials.

> ### Tip:  
> When an OAuth 2.0 client acts on behalf of a user, it requires authorization scopes, which are defined in its own security descriptor, \(`xs-security.json`\). When an OAuth 2.0 client acts on its **own** behalf and no user is involved, the client requires “authorities”, which are defined in the security descriptor of another application - the granting application. An authority is a scope that is flagged as “grantable” so that it can be granted to another application in order to enable the requesting application to perform tasks with the authority of the granting application.

**Related Information**  


[Enable Applications to Perform Tasks with the Authority of Other Applications](enable-applications-to-perform-tasks-with-the-authority-of-other-applications-184402c.md "You can use authorization scopes to enable an application to perform tasks on behalf of another application and in the second application's container.")

[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

[The Application Security Descriptor](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

