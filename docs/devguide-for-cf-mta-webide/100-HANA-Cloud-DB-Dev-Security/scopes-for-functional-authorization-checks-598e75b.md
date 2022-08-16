<!-- loio598e75bf336542b282e72d68e1ea7c77 -->

# Scopes for Functional Authorization Checks

Authorization in the application router and container are handled by scopes. Scopes are groupings of functional organizations defined by the application.

From a technical point of view, the resource server \(the relevant security container API\) provides a set of services \(the resources\) for functional authorizations. The functional authorizations are organized in scopes.

Scopes are used to define the authorizations required by business users for access to the features provided by a specific SAP HANA multitarget application, for example: view, change, or delete. Scopes are created when you deploy or update the application. Scopes are defined in an application's security descriptor file `xs-security.json`. It is possible to define so-called “local” \(application-specific\) scopes and, if necessary, also any “foreign” scopes, which are valid for other applications, too.

> ### Tip:  
> Scopes can be checked declaratively or programatically. For example, a declarative check of the scopes can be performed by the application router or in the Java run-time container; a programmatic check can be performed in either the Java or Node.js run-time containers.

The security descriptor is also used to define a set of role templates for a named application; the role templates contain the authorizations \(“`scope-references`”\) for business users’ actions, for example: viewing, editing, or deleting data. Information retrieved from the user's identity \(such as location, department, or cost center\) is stored in attributes.

After the developer has created the role templates and deployed them to the relevant application, it is the administrator’s task to use the role templates to build roles, aggregate roles into role collections, and assign the role collections to business users in the application.

To assign scopes to an application, you need to perform the following steps:

1.  Create an instance of the User Account and Authentication \(UAA\) service.

    You can use the service broker to create an instance of the UAA service. This ensures the creation of a new OAuth 2.0 client in the UAA.

2.  Assign scopes for the application.

    Scopes are configured and assigned in the application descriptor file `xs-security.json`, which can be placed in the root folder of the application or in a `security` folder in your multitarget application project along with a `package.json` file.


> ### Tip:  
> For access to SAP HANA objects, the privileges of the technical user \(container owner\) apply; for business data, instance-based authorizations using DCL are used.

The following example, of a simple security descriptor for a multitarget application shows how to define authorization scopes and reference them in role templates:

> ### Sample Code:  
> ```
> {
>   "xsappname": "tinyworld",
>   "scopes": [ { "name": "$XSAPPNAME.view", "description": "View data" },
>               { "name": "$XSAPPNAME.create", "description": "Create data"}
>             ],
> 
>   "role-templates": [ { "name": "tinyworldView",
>                         "description": "Role for viewing data",
>                         "scope-references": [ "$XSAPPNAME.view" ] },
>                       { "name": "tinyworldCreate",
>                         "description": "Role for creating data", 
>                         "scope-references": [ "$XSAPPNAME.create","$XSAPPNAME.view" ] }
>                     ]
> }
> ```

**Related Information**  


[The Application Security Descriptor](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

