<!-- loioaf0c9701740c4fa4b495ff5bf96e186a -->

# Authentication with OAuth 2.0

To use OAuth 2.0 for authentication, the architecture needs to provide the OAuth 2.0 elements OAuth 2.0 client, OAuth 2.0 authorization server, and OAuth 2.0 resource server.

If you want to integrate an application in Cloud Foundry, the Cloud Foundry platform needs to know your application. With the XS User Account and Authentication \(UAA\) service, you initially integrate your application into the platform environment. The application needs to authenticate against the User Account and Authentication service, which uses OAuth 2.0 for authentication.

In this context, the UAA acts as the OAuth 2.0 authorization server. The application router itself is the OAuth 2.0 client. To integrate the application into the authentication process, you must create an instance of the `xsuaa` service and bind it to the application router and the application containers. From the OAuth 2.0 perspective, the containers \(for example the Node.js container\) are OAuth 2.0 resource servers. Their container security API validates the access tokens against the UAA.

The UAA uses OAuth 2.0 access tokens with the JSON web token \(JWT\) format for authenticating at the containers, the OAuth 2.0 resource servers.

Principal propagation is needed in the SAP HANA database, as the business users are “virtual database users”, and the database connection uses a technical user. To use OAuth 2.0, the SAP HANA database needs to be able to receive and evaluate OAuth 2.0 access tokens. For this reason, the SAP HANA database uses SAML 2.0 bearer tokens.

**Related Information**  


[http://ietf.org/](http://ietf.org/)

