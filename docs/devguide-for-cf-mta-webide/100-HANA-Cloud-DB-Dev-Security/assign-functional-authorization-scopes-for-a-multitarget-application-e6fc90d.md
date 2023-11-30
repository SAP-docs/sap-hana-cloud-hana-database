<!-- loioe6fc90df44464a29952e1c2c36dd9861 -->

# Assign Functional Authorization Scopes for a Multitarget Application

Declare authorization scopes for your application in the security descriptor and then assign the security descriptor file to the application.



## Context

The functional authorization scopes for your application must be known to the User Account and Authentication \(UAA\) service. You declare the scopes of your application in the security descriptor file named `xs-security.json` and then assign the security descriptor file to the application.

Once you have created an OAuth 2.0 client using the service broker, you specify the `xs-security.json` file that is relevant for your application. Using this security descriptor file, the OAuth 2.0 client that has been created for your application receives permission to access the scopes of your application automatically.



## Procedure

1.  Define the authorization scopes for your application.

    Authorization scopes for multitarget applications are defined in the application's security descriptor \(`xs-security.json`\). You also need to provide a reference for each authorization scope in a corresponding role template. The following example of an `xs-security.json` file defines scopes for viewing and creating data:

    > ### Sample Code:  
    > Authorization Scopes in the Security Descriptor \(`xs-security.json`\)
    > 
    > ```
    > {
    >   "xsappname": "tinyworld",
    >   "scopes": [ { "name": "$XSAPPNAME.view", "description": "View data" },
    >               { "name": "$XSAPPNAME.create", "description": "Create data"}
    >             ],
    > 
    >   "role-templates": [ { "name": "tinyworldView",
    >                         "description": "Role for viewing data",
    >                         "scope-references": [ "$XSAPPNAME.view" ] 
    >                       },
    >                       { "name": "tinyworldCreate",
    >                         "description": "Role for creating data", 
    >                         "scope-references": [ "$XSAPPNAME.create","$XSAPPNAME.view" ] 
    >                       }
    >                     ]
    > }
    > ```

2.  Assign the `xs-security.json` file to the multitarget application for which you defined the authorization scopes.

    You can use the following command:

    <code>cf create-service <i class="varname">&lt;service_name&gt;</i> <i class="varname">&lt;service_plan&gt;</i> -c <i class="varname">&lt;security_descriptor_file&gt;</i></code>

    > ### Example:  
    > `cf create-service xsuaa default -c xs-security.json`

    This creates an instance of the UAA service with the scopes defined in the security descriptor and ensures it is bound to the corresponding application.

    > ### Note:  
    > After the developer has created the role templates and deployed them to the relevant application, it is the administrator’s task to use the role templates to build roles, aggregate the roles into role collections, and assign the role collections to business users in the application. For more information, see the *SAP HANA Cloud Administration Guide*.


**Related Information**  


[Create the Security Descriptor for a Multitarget Application](create-the-security-descriptor-for-a-multitarget-application-df31a08.md "The security descriptor defines details of an application's security-related dependencies.")

