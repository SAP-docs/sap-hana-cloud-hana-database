<!-- loio3bfb120045694e21bfadb1344a693d1f -->

# The Application Security Descriptor

A file that defines the details of the authentication methods and authorization types to use for access to your application.

The `xs-security.json` file uses JSON notation to define the security options for an application; the information in the application-security file is used at application-deployment time, for example, for authentication and authorization. Applications can perform scope checks \(functional authorization checks with Boolean result\) and checks on attribute values \(instance-based authorization checks\). The `xs-security.json` file declares the scopes and attributes on which to perform these checks. This enables the User Account and Authentication \(UAA\) service to limit the size of an application-specific JSON Web Token \(JWT\) by adding only relevant content.

Scope checks can be performed by the application router \(declarative\) and by the application itself \(programmatic, for example, using the container API\).

Checks using attribute values can be performed by the application, for example, using the container API.

The contents of the `xs-security.json` are used to configure the OAuth 2.0 client; the configuration is shared by all components of an SAP multi-target application. The contents of the `xs-security.json` file cover the following areas:

-   Authorization scopes

    A list of limitations regarding privileges and permissions and the areas to which they apply

-   Attributes

    A list of as-yet undefined information or sources \(for example, the name of a cost center\)

-   Role templates

    A description of one or more roles to apply to a user and any attributes that apply to the roles


The following example shows a simple application-security file:

> ### Sample Code:  
> Example `xs-security.json` File
> 
> ```
> {
>   "xsappname" : "node-hello-world", 
>   "scopes"     : [ { 
>                     "name" : "$XSAPPNAME.Display", 
>                     "description" : "display" }, 
>                    { 
>                     "name" : "$XSAPPNAME.Edit", 
>                     "description" : "edit" }, 
>                    { 
>                     "name" : "$XSAPPNAME.Delete", 
>                     "description" : "delete"  } 
>                  ], 
>   "attributes" : [ { 
>                     "name" : "Country", 
>                     "description" : "Country", 
>                     "valueType" : "string" }, 
>                    {
>                     "name" : "CostCenter", 
>                     "description" : "CostCenter", 
>                     "valueType" : "int" } 
>                  ], 
>   "role-templates": [ { 
>                        "name"                : "Viewer", 
>                        "description"         : "View all books", 
>                        "scope-references"    : [ 
>                                           "$XSAPPNAME.Display" ], 
>                        "attribute-references": [ "Country" ]  
>                       }, 
>                       { "name"               : "Editor", 
>                         "description"        : "Edit, delete books", 
>                         "scope-references"   : [ 
>                                               "$XSAPPNAME.Edit", 
>                                               "$XSAPPNAME.Delete" ], 
>                         "attribute-references" : [ 
>                                               "Country", 
>                                               "CostCenter"] 
>                       } 
>                      ] 
> }
> 
> ```



<a name="loio3bfb120045694e21bfadb1344a693d1f__section_ad3_5r5_bt"/>

## Scopes

Scopes are functional authorizations that are assigned to users by means of security roles, which are mapped to the user group\(s\) to which the user belongs. Scopes are used for authorization checks by the application router and the application's HDI container. The authorization checks can be performed declaratively \(for example, by the application router or in the Java run-time container\) or programmatically, for example, in either the Java or the Node.js run-time containers.

-   Application router

    URL prefix patterns can be defined and a scope associated with each pattern. If one or more matching patterns are found when a URL is requested, the application router checks whether the OAuth 2.0 access token included in the request contains at least the scopes associated with the matching patterns. If not all scopes are found, access to the requested URL is denied. Otherwise, access to the URL is granted.

-   Application container

    The container security API includes the `hasScope` method that allows you to programmatically check whether the OAuth 2.0 access token used for the current request has the appropriate scope. Among other things, the access token contains a list of scopes that the user is allowed to access in the current context. Each scope name must be unique in the context of the current UAA installation.




<a name="loio3bfb120045694e21bfadb1344a693d1f__section_w5n_5r5_bt"/>

## Attributes

You can define attributes so that you can perform checks based on a source that is not yet defined. Attributes are used to define **instance**-based authorizations, which change according to the context, for example, location, time-zone, or cost center. In the example `xs-security.json` file included here, the check is based on a cost center, whose name is not known at design time, because the name of the cost center differs according to context.



<a name="loio3bfb120045694e21bfadb1344a693d1f__section_j55_5r5_bt"/>

## Role Templates

A role template describes a role and any attributes that apply to the role.

It is important to remember that a role template must be instantiated, for example, using role-building tools in the *Cloud Cockpit*. This is especially true with regards to any attributes defined in the role template and their concrete values, which are subject to customization and, as a result, cannot be provided automatically. Role templates that only contain local scopes can be instantiated without user interaction. The same is also true for foreign scopes where the scope “owner” has declared his consent in a kind of allow list \(for example, either for “public” use or for known “friends”\).

> ### Note:  
> If a role template does not contain any attributes, then a role is generated automatically with the same name as the role template. Otherwise, a role based on a role template can be generated using the administration tools.

The version information defined in the role template can be used to check if an instantiated role needs to be updated. This assumes that the instantiated role contains not only a reference to the role template from which it was derived but also the corresponding version information.

> ### Note:  
> The resulting application-specific role instance needs to be assigned to one or more user groups.

**Related Information**  


[Create the Security Descriptor for a Multitarget Application](create-the-security-descriptor-for-a-multitarget-application-df31a08.md "The security descriptor defines details of an application's security-related dependencies.")

[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

