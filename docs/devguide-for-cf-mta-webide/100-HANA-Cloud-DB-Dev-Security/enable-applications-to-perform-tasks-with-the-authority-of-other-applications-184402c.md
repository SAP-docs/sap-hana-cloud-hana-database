<!-- loio184402c0da574164ab6e715e73b9d595 -->

# Enable Applications to Perform Tasks with the Authority of Other Applications

You can use authorization scopes to enable an application to perform tasks on behalf of another application and in the second application's container.



## Context

It is possible to enable an application to grant the authorization defined in its own scopes to another application on request, for example, to allow the requesting \(external\) application to perform tasks on behalf of the local application; that is, with the authority of the local application, and in the local application's container. To configure one application to perform tasks with the authority of another application, perform the following steps:



## Procedure

1.  Enable an application to grant scope authorities to another \(requesting\) application.

    In the security descriptor \(`xs-security.json`\) of the application granting the use of a scope authority, use the `"grant-as-authority-to-apps"` property to specify which individual scopes are to be "grantable" to another authorized application on request.

    ```
    "scopes": [
            {
              "name": "$XSAPPNAME.foreigncall",
              "description": "Enable Calls into Granting App",
              "grant-as-authority-to-apps": ["RequestingApp"]
            },
    ]
    ```

2.  Bind the application granting the scope authority to its respective UAA service.

    After you make the necessary changes to the scopes in the security descriptor of the application that is granting the scope authorities, you must rebind the application to its UAA service instance.

    ```
    cf bind-service GrantingApp xsuaa –c xs-security.json
    ```

    > ### Tip:  
    > If no such instance of the `xsuaa` service exists, then create it using the `create-service` command.

3.  Enable the requesting application to accept the scope authorities granted by another application.

    In the security descriptor of the application requesting the authorization scopes granted by another application, list the requested scopes and the application granting them in the <code>“authorities”</code> property. You can configure **all** granted scopes to be accepted and used, or individual named scopes, as indicated below:

    -   Accept all granted authorities:

        ```
        "authorities":["$ACCEPT_GRANTED_AUTHORITIES"],
        ```

    -   Accept the specified authorities from the named applications:

        ```
        "authorities":["<GrantingApp>.ForeignCall", "<GrantingApp2>.ExternalCall"],
        ```


4.  Bind the requesting application to its respective UAA service instance.

    After you have made the necessary changes to the security descriptor of the application requesting, accepting, and using the scope authorities granted by the first application, you must rebind the requesting application to its UAA service instance so that it updates its configuration with the scope changes made to the security descriptor \(`xs-security.json`\).

    ```
    cf bind-service RequestingApp xsuaa –c xs-security.json
    ```

    > ### Tip:  
    > If no such instance of the `xsuaa` service exists, then create it using the `cf create-service` command.

5.  Test the requesting and granting of the configured scopes and authorities.

    Start all applications and test that the requesting application receives the granted authority and can perform the planned task with the required authorization in the granting application's container.


**Related Information**  


[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

[Create an Instance of the XS UAA Service](create-an-instance-of-the-xs-uaa-service-41457ec.md "Use the service broker to create an instance of the xsuaa service.")

[Bind the XS UAA Service Instance to the Multitarget Application](bind-the-xs-uaa-service-instance-to-the-multitarget-application-a1b87ab.md "You must bind the UAA service instance you create to the multitarget application that is going to use it.")

