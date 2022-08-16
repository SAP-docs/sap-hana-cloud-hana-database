<!-- loioe8dde5fb0d484a26beb6e11a71de51f9 -->

# Authorization in SAP HANA Services and Resources

Authorization restricts access to resources and services based on defined user permissions.

In SAP HANA, multitarget applications contain content that is deployed to different database containers. Access to the content requires not only user authentication but also the appropriate **authorization**.

The access-control process controlled by the authorization policy can be divided into the following two phases:

-   Authorization

    Defined in the deployment security descriptor \(`xs-security.json`\), where access is authorized

-   Policy enforcement

    The general rules by which requests for access to resources are either approved or disapproved.


Access enforcement is based on user identity and performed in the following distinct application components:

-   Application router

    After successful authentication at the application router, the application router starts an authorization check \(based on scopes\).

-   Application containers

    For authentication purposes, containers, for example the node.js and Java containers, receive an HTTP header `Authorization: Bearer` *<JWT token\>* from the application router; the token contains details of the user and scope. This token **must** be validated using the Container Security API. The validation checks are based on scopes and attributes defined in the security descriptor \(`xs-security.json`\).

-   SAP HANA database

    Every multitarget application uses its own dedicated database schema and its own dedicated \(technical\) database user for requests to connect to the database \(for example, to manage persistent application data\). This architecture ensures data isolation between the applications. The technical database user is assigned the SAP HANA privileges required by the application; this defines the boundaries for all SAP HANA users accessing that application.

    > ### Note:  
    > Instance-based authorization checks using the data control language \(DCL\) are also supported; the checks are based on attributes, for example, those defined in the security descriptor \(`xs-security.json`\).


**Related Information**  


[Maintaining Application Security in Cloud Foundry on SAP BTP](maintaining-application-security-in-cloud-foundry-on-sap-btp-35d910e.md "Set up the security components required in the context of multitarget applications on SAP BTP .")

[The Application Security Descriptor](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

[Scopes for Functional Authorization Checks](scopes-for-functional-authorization-checks-598e75b.md "Authorization in the application router and container are handled by scopes. Scopes are groupings of functional organizations defined by the application.")

