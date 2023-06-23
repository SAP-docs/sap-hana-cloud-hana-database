<!-- loioc6f36d5d49844bd790798ea36538e024 -->

# User Account and Authentication Services

The SAP HANA XS User Account and Authentication service \(UAA\) is the central infrastructure component for user authentication and trust manageement.

The UAA uses OAuth 2.0 for the purposes of authentication when granting access to the application and the database containers. In the context of the OAuth flow, the UAA provides scopes, role templates, and attributes to applications deployed in the application run time. If a business user has a certain scope, an access token with this scope is issued, which enables a user to run the application: the scopes are used to define the model that describes who has the authorization to start an application running in the application run time.

> ### Note:  
> The UAA service supports an SAML 2.0 identity provider \(IDP\).

The XSUAA service provides a programming model for developers; it enables developers to define templates that can be used to build role and authorization models for business users of applications deployed to the application run time. In the OAuth 2.0 work flow, the UAA acts as an OAuth server, which includes both token and revocation end points.



## Security Services in the Application Router

The application router is the single point-of-entry for a multitarget application running in Cloud Foundry on SAP Business Techology Platform \(SAP BTP\); the application router is part of the multitarget application instance and triggers the user-authentication process in the UAA. In the OAuth work flow, the multitarget application instance \(including the application router and any bound containers\) is the OAuth 2.0 client, which handles user authentication and authorization.



## Container Security APIs

In the context of OAuth 2.0, the security APIs for the application run time container act as resource servers; the APIs provide the security context for user authentication. When the user authentication process is triggered, the application container security APIs receive an HTTP header with “`Authorization: Bearer`” and a JSON Web token \(JWT\) from the application router.

The token contains information describing the user and any authorization scopes, which must be validated by the application container security APIs using the security libraries provided by the UAA. Applications deployed in the Cloud Foundry run time can use the security API to check if scope values have been assigned to the user or application. The container security API provides the security **context** for multitarget applications \(for example, scopes, attributes, token information\); the JWT token initializes the security context. A security API is available for the following application run time containers:

-   Node.js API

-   XS JavaScript \(compatibility layer\) API

-   Java API


Every multitarget application's run time container must use the container security API to provide the security context. The security context is initialized with the JWT token and enables you to perform the following functions:

-   Get user information

-   Check an authorization scope

-   List authentication attributes

-   Get a token




<a name="loioc6f36d5d49844bd790798ea36538e024__section_itl_xjb_5z"/>

## XS UAA Service Plans

The XSUAA service plan you use determines the impact on the `xsappname` that is written into the credentials section of the environment from the application bound to the service \(<code>cf env <i class="varname">&lt;appname&gt;</i></code>. Each of the XSUAA service plans is designed for use with a particular kind of user-security scenario, and service availability depends on platform, for example, `cf` on SAP Cloud Plaftorm @ Cloud Foundry, as illustrated in the following example:

> ### Sample Code:  
> SAP HANA Managed Service \(SAP BTP/Cloud Foundry\)
> 
> ```
> cf marketplace -e xsuaa
>  
> Getting services from marketplace...
> Getting plans for service "xsuaa"...
>   
> service plan   description                                                                          free/paid
> –––––––––––––––––––––--––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––––--
> application    Application plan to be used for business applications                                free 
> apiaccess      Access Plan for Authorization, Users and IDPS API endpoints.                         free
> ```

The XS User Account and Authentication service provides the following plans for Cloud Foundry on SAP BTP:



<a name="loioc6f36d5d49844bd790798ea36538e024__section_wqx_vlb_5z"/>

## XSUAA Service Plan: “application”

For platform applications that need to integrate with the platform User Account and Authentication \(UAA\) service for **user-related** operations \(for example, business users of applications\), the `xsuaa` service broker provides the `"application"` service plan.

The `"application"` service plan requires the value of the `"xsappname"` property specified in the `xs-security.json` file to be unique in the Cloud Foundry landscape within the tenant in which the application is deployed. This means that an application may be deployed in several tenants at the same time but not twice in the same tenant \(unless you modify the value of `"xsappname"` in the second application's `xs-security.json` security descriptor\). Failure to adjust the application name results in an error message during the second deployment.

> ### Tip:  
> The `"xsappname"` that is written into the credentials section of the environment is enhanced with a suffix and has the following format: <code>"<i class="varname">&lt;xsappname&gt;</i>!t<i class="varname">&lt;tenant index&gt;</i>"</code>, where the *<tenant index\>* is a number that the UAA maintains internally and differs from landscape to landscape, for example, `myapp!i5`.

The PaaS-enabled service plan `"application"` is only available in Cloud Foundry landscapes. It is highly recommended to use the `"application"` service plan for all standard Cloud Foundry deployments. The main features and advantages of the `"application"` service plan include the following:

-   Tenant isolation
-   Support for different OAuth flows

    Client credentials, authorization code, and SAML bearer assertion

-   One OAuth client per service instance



<a name="loioc6f36d5d49844bd790798ea36538e024__section_myv_lrv_gnb"/>

## XSUAA Service Plan: “apiaccess”

The service plan `apiaccess` creates an OAuth Client during creation of the service instance, which comprises all scopes required to access the XSUAA APIs, for example:

-   `xs_authorization.read` and `xs_authorization.write`
-   `xs_user.read` and `xs_user.write`
-   `xs_idp.read` and `xs_idp.write`

The prerequisite for the service-instance creation is that the corresponding platform user also owns the scopes listed above. This is the case if the platform user is administrator in the corresponding subaccount where the service instance is to be created.

> ### Tip:  
> An administrator is assigned the role User & Role Administrator, and you can check this in the subaccount view in the SAP BTP cockpit \(*Security* \> *Administrators*\).

It is not possible to pass any parameters \(for example, in the security descriptor `xs-security.json`\) during creation of the service instance \(indeed, any input is ignored\). And after the service instance is created, the OAuth client's credentials can be retrieved by means of the service key. It is also important to bear in mind that it is not possible to subscribe to any services instances created with the `apiaccess` service plan. The advantage of this plan is that the V2 authorization and SCIM endpoints of the XSUAA can be used by a technical user and do not require a space developer or admin user.

**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Maintaining Multitarget Application Services in Cloud Foundry](maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

