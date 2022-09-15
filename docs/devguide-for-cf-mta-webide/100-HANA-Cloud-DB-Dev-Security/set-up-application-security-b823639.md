<!-- loiob8236393290048dda17b4545d17eac66 -->

# Set up Application Security

Help ensure a multitarget application is protected from Web-based attacks.



## Context

In addition to enabling an application to identify, authenticate, and grant the appropriate authorization to users logging on to a multitarget application, it is also essential to ensure that the application itself uses all available tools to guard against Web-based attacks, for example, by setting a session timeout and closing unused and unwanted sessions; using CORS to enable or disable the shared access to resources between domains; enabling protection against cross-site request forgery \(CSRF\); and configuring protection against click-jacking attempts.

The following steps provides useful tips and tricks to help you understand what needs to be done to set up application security and where to find the information to help you do it:



## Procedure

1.  Set up user authentication for your multitarget application.

    You can choose between various authentication methods and types for users logging into a multitarget application. It is also recommended to set up the OAuth 2.0 client.

    -   Authentication method and type

        The **method** used to authenticate the user of a multitarget application defined in the application-router configuration file \(`xs-app.json`\), as illustrated in the following \(incomplete\) example:

        "`authenticationMethod": ["route"|"none"]`

        > ### Note:  
        > If `authenticationMethod` is set to “`none`”, logon with the User Account and Authentication \(UAA\) service is disabled.

        The **type** of authentication used for user logon to a multitarget application is defined in the individual route specified in the application-router configuration file \(`xs-app.json`\), as illustrated in the following \(incomplete\) example:

        `"routes": [{...},{[...]"authenticationType": ["xsuaa"|"basic"|"none"]}]`

        > ### Note:  
        > If `authenticationType` is set to “`none`”, then no authentication is required for the specified application route.

    -   OAuth 2.0 configuration

        The OAuth 2.0 client configuration is defined in the multitarget application's security descriptor \(`xs-security.json`\), as illustrated in the following \(incomplete\) example:

        `"oauth2-configuration": {"token-validity": "900", "autoapprove": "false"}`

    -   Single Sign-on \(SSO\)

        The Cloud Foundry run-time platform on SAP Business Technology Platform supports Single Sign-On \(SSO\) with SAP HANA OpenID Connect \(OIDC\), for example, using X.509 certificates or SPNego with Kerberos, provided that the corresponding back-end services are configured and enabled in SAP HANA. The XS UAA server enables support for X.509 certificates by default \(`uaa.oidc.enablex509 = true`\); support for SPNego/Kerberos on the other hand is not enabled by default \(`uaa.oidc.enablespnego = false`\) but can be enabled in the XS UAA server configuration file \(`xsuaaserver.ini`\) manually, if required.

        > ### Note:  
        > Administrator privileges are required to maintain security certificates in the application run-time; SAP HANA administrator privileges are required to maintain database users.

        For more information about setting up SSO for SAP HANA users and multitarget applications, see the *SAP HANA Cloud Administration Guide* in *Related Information* below.


2.  Set up cross-origin resource sharing \(CORS\).

    The CORS environment variable enables you to provide support for cross-origin requests, for example, by allowing the modification of the request header, which is normally disabled by default. Cross-origin resource sharing \(CORS\) permits Web pages from other domains to make HTTP requests to your application domain, where normally such requests would automatically be refused by the Web browser's security policy.

    You can enable cross-origin support in the application router by setting the *<CORS\>* environment variable.

    > ### Sample Code:  
    > ```
    > cf set-env <AppName> CORS {<CORS_Configuration>}
    > ```

    When setting the CORS environment variable, the properties `"uriPattern"` and `"allowedOrigin"` are mandatory.

    > ### Tip:  
    > If you use a simple comma-separated list or a JSON structure to define *<CORS\_Configuration\>*, the rules that apply for escaping quotes or spaces included in the string differ according to the command shell you are using \(Windows or Unix-like\). The following example shows a Unix example using single quotes \(`'{}'`\) to enclose the CORS configuration values.

    > ### Sample Code:  
    > ```
    > cf set-env myApp1 CORS '{"uriPattern": "^\route1$", "allowedOrigin": [ { "host": "www.acme.com", "protocol": "https", "port": 345 } ]}'
    > ```

3.  Enable protection against cross-site request forgery \(CSRF\).

    In the application router configuration, you can specify if a route needs protection for CSRF tokens. The default value is “true” where the application router enforces CSRF protection for any HTTP request that changes state on the server side, for example: `PUT`, `POST`, or `DELETE`.

    > ### Tip:  
    > The SAP Node.js package `@sap/xss-secure` is a utility that provides additional protection against cross-site scripting as described in a subsequent step.

    The following example shows how to enable CSRF protection for an application route. For more information about configuring the application router, see the *Related Information*.

    > ### Sample Code:  
    > ```
    > {
    > ...
    >   "routes": [
    >       {
    >         "source": "^/sap/ui5/1(.*)$",
    >         "target": "$1",
    >         "destination": "ui5",
    >         "csrfProtection": true
    >       },
    > ...
    > }
    > ```

4.  Set up protection against click-jacking attempts.

    In the application router configuration, you can enable the so-called whitelistservice which allows requests from defined sources to help prevent against click-jacking attacks. Enabling the allow-list service opens an endpoint that accepts `GET` requests at the relative path configured in the `endpoint` property, as illustrated in the following example:

    > ### Sample Code:  
    > ```
    > {
    >   "whitelistService": {
    >     "endpoint": "/allowlist/service"
    >   }
    > }
    > ```

    If the allow-list service is enabled in the application router, each time an HTML page needs to be rendered in a frame, the allow-list service is used check if the parent frame is allowed to render the content in a frame. For more information about configuring the application router, see *Related Information*.

    > ### Tip:  
    > You can use the *<CJ\_PROTECT\_WHITELIST\>* environment variable to define a list of origins \(host or domain names\) that do not need to be protected against click-jacking attacks.

    This list of allowed host names and domains are used by the application router's allow-list service to protect multitarget applications against click-jacking attacks. When an HTML page needs to be rendered in a frame, a check is done by calling the allow-list service to validate if the parent frame is allowed to render the requested content in a frame. The following example shows how to add a host name to the allow list for protection against click-jacking:

    > ### Sample Code:  
    > ```
    > cf set-env myApp1 CJ_PROTECT_WHITELIST {<protocol>, <hostname>, <portNr>}
    > ```

5.  Set up protection against cross-site scripting \(XSS\).

    Cross-site Scripting \(XSS\) is the name of a class of security vulnerabilities that can occur in Web applications, for example, when these applications dynamically generate HTML, JavaScript, or even CSS. Attackers can use these vulnerabilities to include arbitrary HTML, JavaScript, or CSS into an application's client front end; this code is, in turn, rendered by the victim's Web browser and, in this way, interpreted in the victim's current authentication context. To help you protect your application against XSS attacks, SAP provides the Node.js package `@sap/xss-secure` which includes APIs to encode CSS, HTML, JavaScript, URLs, and even XML code.

    The following example shows how to start using `@sap/xss-secure`:

    > ### Sample Code:  
    > ```
    > var xsssecure = require('@sap/xss-secure'); 
    > ```

    For more information about standard SAP Node.js packages, see *Related Information*.

6.  Set up timeouts for application user sessions.

    You can configure the triggering of an automatic central log-out from the User Account and Authentication \(UAA\) service if an application session is inactive for a specified time. A session is considered to be inactive if no requests are sent to the application router. The following command shows how to set the environment variable *<SESSION\_TIMEOUT\>* to 10 \(ten\) minutes for the application *<myApp\>*:

    > ### Sample Code:  
    > ```
    > cf set-env <myApp> SESSION_TIMEOUT 10
    > ```

    > ### Tip:  
    > If the authentication type for a route is set to `"xsuaa"` \(for example, `"authenticationType": "xsuaa"`\), the application router depends on the UAA server for user authentication, and the UAA server might have its own session timeout defined. To avoid problems caused by unexpected timeouts, it is recommended that the session timeout values configured for the application router and the UAA are identical."

7.  Set up anti-virus scanning for multitarget applications.

    The `@sap/node-vsi` package contains the Virus Scan Interface \(VSI\) binding for Node.js. The package also includes the native libraries required to run on Windows, Linux, and MacOS operating systems.

    > ### Note:  
    > The `@sap/node-vsi` package does not perform any virus scanning; the virus-scanning tools must be installed and configured independently.

    The following example shows how to start using `@sap/node-vsi`:

    > ### Sample Code:  
    > ```
    > var vsi = require('@sap/node-vsi'); 
    > ```

    For more information about standard SAP Node.js packages, see *Related Information*.

8.  Secure your Node.js application.

    SAP HANA includes a selection of standard Node.js packages that provide help when enabling and configuring security for your Node.js application. The packages are available for download and use either from the NPM public registry at `https://registry.npmjs.org` or, for customers and partners who have the appropriate access authorization, from the SAP Service Marketplace \(SMP\).

    The following security-related Node.js/JavaScript libraries are available:

    -   `@sap/audit-logging`

        A Node.js client that enables applications to make use of the features and functionality provided by the audit-log service

    -   `@sap/hdbext`

        A JavaScript client for Node.js which implements the SAP HANA Database SQL Command Network Protocol

    -   `@sap/xsenv`

        A utility that allows the easy setup of \(and access to\) Cloud Foundry environment variables and services \(for example, CORS, CSRF, …\)

    -   `@sap/xssec`

        Security API for Node.js; this includes the application **container** security API for Node.js described in the *SAP HANA Cloud Administration Guide*

    -   `@sap/xss-secure`

        A utility that provides protection against cross-site scripting


    > ### Tip:  
    > For more information about which Node.js packages are available, see *Related Information* below. For more details about the contents of an individual package, see the `README` file in the corresponding package after download.

9.  Secure your Java application.

    SAP HANA includes a selection of standard Java libraries, which are available for download from the SAP Service Marketplace \(SMP\) to customers and partners who have the appropriate access authorization. The following security-related Java libraries are included:

    -   `xs-env`

        A utility for setting up and accessing Cloud Foundry environment variables and services

    -   `audit-java-client-api`

        A client that enables applications to use the audit-log service

    -   `java-security` \(or `spring-xsuaa`\)

        > ### Tip:  
        > The open-source Java security client \(`java-security` and `spring-xsuaa`\) for SAP Business Technology Platform are available on GitHub and on Maven Central. For more details, see *Related Information* below


    For more information, see *Related Information* below.

    > ### Tip:  
    > For more details of the contents of an individual package, see the `README` file in the corresponding package after download or, if available, the JavaDoc reference guide.

10. Secure your Python application.

    SAP HANA includes a selection of standard Python libraries, which are available for download from the SAP Service Marketplace \(SMP\) to customers and partners who have the appropriate access authorization. The following security-related Python libraries are included:

    -   `sap_xssec`

        Container Security API for Python.

    -   `sap_audit_logging`

        Audit-logging functionality for multitarget Python applications


11. Configure data privacy and anonymity in views.

    You can use so-called view nodes in calculation views to ensure the anonymity of private data in result sets. The graphical calculation view editor in the *SAP Web IDE Full-Stack* provides an **anonymize** view node, which you can use to select the required anonymization method and to define the level of privacy for a data set. The “anonymize” view node must always be used as a leaf node in the calculation view. You can preview the output of the calculation view modeled with anonymize view nodes only if the query on the calculation view includes all output columns of the calculation view.

    > ### Tip:  
    > For more information about data-anonymity in calculation views, see the *SAP HANA Cloud Data Anonymization Guide* in *Related Information*.


**Related Information**  


[Application Security Tools and Components](application-security-tools-and-components-a004e4f.md "Setting up security for multitarget applications involves multiple tasks and multiple tools and components.")

[Application Router Configuration Syntax](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[Application Router Environment Variables](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-environment-variables-0aac697.md "A list of environment variables that can be used to configure the application router.")

[Standard SAP Node.js Packages](../060-HANA-Cloud-DB-Dev-App-Code/standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[Standard SAP Java Client Libraries for Cloud Foundry](../060-HANA-Cloud-DB-Dev-App-Code/standard-sap-java-client-libraries-for-cloud-foundry-6511bc0.md "A collection of Java client libraries developed by SAP is provided to help you develop Java applications for Cloud Foundry.")

[Standard Python Packages for Cloud Foundry](../060-HANA-Cloud-DB-Dev-App-Code/standard-python-packages-for-cloud-foundry-8732609.md "A list of Python packages developed by SAP, which are available for download and use.")

[SAP CP Java Security Library \(GitHub\)](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/java-security)

[SAP CP Spring XSUAA Library \(GitHub\)](https://github.com/SAP/cloud-security-xsuaa-integration/tree/master/spring-xsuaa)

[Maven Central Repository](https://mvnrepository.com/search?q=SAP&d=com.sap)

[SAP HANA Cloud Data Anonymization Guide](https://help.sap.com/viewer/DRAFT/cacb29f98ffb4518819a8cf4a4ed3572/dev/en-US)

