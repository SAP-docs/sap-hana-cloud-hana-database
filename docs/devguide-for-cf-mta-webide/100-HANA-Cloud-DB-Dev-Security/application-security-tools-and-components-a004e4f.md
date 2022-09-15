<!-- loioa004e4fb650c480f9beee556295f21af -->

# Application Security Tools and Components

Setting up security for multitarget applications involves multiple tasks and multiple tools and components.



The following table lists the tasks you need to perform to set up security for your multitarget application, shows which tools or components are involved, and indicates the privileges and permissions required by the persona who typically performs the task, for example, "developer" or "administrator".

> ### Note:  
> The tasks and tools listed in the following table are not exhaustive; some tools are not included. The aim of the table is to provide guidance concerning where to find information about the more typical areas of concern for application security. For more information about the individual tools mentioned in this topic, see *Related Information*.

<a name="loioa004e4fb650c480f9beee556295f21af__table_qhw_bwp_3bb"/>Security-Related Tasks and Tools for Multitarget Applications


<table>
<tr>
<th valign="top">

Task



</th>
<th valign="top">

Tool



</th>
<th valign="top">

Persona/Permissions



</th>
</tr>
<tr>
<td valign="top">

Application container: access and security



</td>
<td valign="top">

Container Security API

-   JavaScript/Node.js: `@sap/xssec` 

-   Java: `java-security`

-   Python: `sap_xssec`




</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Application Security



</td>
<td valign="top">

Java:

-   `java-security` 
-   `spring-xsuaa`

> ### Tip:  
> The open-source SAP BTP Java security clients `java-security` and `spring-xsuaa` are available on GitHub and on Maven Central. For more details, see *Related Information* below



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

JavaScript/Node.js:

-   `@sap/xssec` \(security APIs\)
-   `@sap/xss-secure` \(cross-site scripting\)
-   `@sap/node-vsi` \(anti-virus\)

    > ### Note:  
    > The `@sap/node-vsi` package does not perform any virus scanning; the virus-scanning tools must be installed and configured independently.




</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Python

-   `sap_xssec` \(Security API; included in SAP's `XS PYTHON package`\)
-   `sap_audit_logging` \(included in SAP's `XS PYTHON package`\)



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

Application authentication \(method, type, …\)



</td>
<td valign="top">

Application router configuration \(`xs-app.json`\)

OAuth 2.0 configuration \(`xs-security.json`\)

JSON Web Tokens \(JWT\)



</td>
<td valign="top">

Developer

Developer

Developer



</td>
</tr>
<tr>
<td valign="top">

User Account and authentication service \(`UAA`\)

CF CLI:

-   `create-service`

-   `bind-service`




</td>
<td valign="top">

Developer: during development and testing

XS advanced administrator: for installation and update on productive systems



</td>
</tr>
<tr>
<td valign="top">

Single Sign-on \(SSO\) with SAP HANA OpenID Connect \(OIDC\). The default XSUAA server configuration \(`xsuaaserver.ini`\) enables support for X.509 certificates \(`uaa.oidc.enablex509 = true`\). Support for SPNego/Kerberos on the other hand is not enabled by default \(`uaa.oidc.enablespnego = false`\) but can be enabled in the XUAA server configuration file manually, if required.



</td>
<td valign="top">

XS advanced administrator: maintaining run-time certificates

SAP HANA administrator: maintaining database users



</td>
</tr>
<tr>
<td valign="top">

Application authorization \(scopes\)



</td>
<td valign="top">

Application security descriptor \(`xs-security.json`\)

Application router configuration \(`xs-app.json`\)



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Application routes



</td>
<td valign="top">

Application router configuration \(`xs-app.json`\)



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Application destinations \(login/logout\)



</td>
<td valign="top">

Application router configuration \(`xs-app.json`\)

Application deployment manifest \(`manifest.yml`\)

> ### Note:  
> Destinations specified in the `manifest.yml` must match the destinations defined the application-router configuration \(`xs-app.json`\). For more information, see the section application routes and destinations.



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Click Jacking protection



</td>
<td valign="top">

Application router configuration \(`xs-app.json`\):

```
"whitelistService": {"endpoint":"<path>"}
```

Application router environment variable:

```
CJ_PROTECT_WHITELIST {<protocol>, <hostname>, <portNr>}
```



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Cross-Origin Resource Sharing \(CORS\) configuration



</td>
<td valign="top">

Application router environment variable \(<code><i class="varname">&lt;CORS&gt;</i></code>\), for example:

```
[{"uriPattern": "^\route1$", 
  "allowedMethods": ["GET"],
  "allowedOrigin": [
      {
       "host": "host.acme.com",
       "protocol": "https",
       "port": 345
      }]
}]
```

> ### Tip:  
> CORS configuration is also possible in the application `manifest.yml` file. For more information, see *Related Information* below.



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Cross-Site Resource Forgery \(CSRF\) protection



</td>
<td valign="top">

Application router configuration \(`xs-app.json`\)



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Cross-site scripting \(XSS\) protection



</td>
<td valign="top">

Node.js package `@sap/xss-secure` 



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Data anonymity



</td>
<td valign="top">

Calculation views with the *k-anonymity* \(and differential privacy\) anonymization methods.



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

Secure Store



</td>
<td valign="top">

An application bound to an instance of the platform service `hana` with the service plan `securestore` can use the following stored procedures to access to the SAP HANA Secure Store:

-   `SYS.USER_SECURESTORE_INSERT`

    Insert an encrypted entry into the SAP HANA Secure Store.

-   `SYS.USER_SECURESTORE_RETRIEVE`

    Retrieve an encrypted entry from the SAP HANA Secure Store.

-   `SYS.USER_SECURESTORE_DELETE`

    Delete an encrypted entry from the SAP HANA Secure Store.




</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

User identification



</td>
<td valign="top">

User accounts and subaccounts \(SAP BTP Cockpit\)



</td>
<td valign="top">

SAP BTP administrator

XS advanced administrator



</td>
</tr>
<tr>
<td valign="top">

User roles



</td>
<td valign="top">

Application security descriptor \(`xs-security.json`\)

-   Role Templates
-   Scopes/Attributes



</td>
<td valign="top">

Developer



</td>
</tr>
<tr>
<td valign="top">

User role collections



</td>
<td valign="top">

SAP BTP Cockpit



</td>
<td valign="top">

XS advanced administrator

SAP BTP administrator



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

User organizations/spaces



</td>
<td valign="top">

CF CLI:

-   `create-[org|space]`

-   `set-[org|space]-role`




</td>
<td valign="top">

orgManager

spaceManager



</td>
</tr>
<tr>
<td valign="top">

Administrator tools:

-   *Organization and Space Management*

-   *Application Role Builder*

-   *SAML ID Provider Configuration*

-   *User Management*




</td>
<td valign="top">

XS advanced administrator



</td>
</tr>
<tr>
<td valign="top">

Virus protection



</td>
<td valign="top">

Anti-virus scanning configuration in Node.js package `@sap/node-vsi` 

> ### Note:  
> The `@sap/node-vsi` package does not perform any virus scanning; the virus-scanning tools must be installed and configured independently.



</td>
<td valign="top">

Developer



</td>
</tr>
</table>

**Related Information**  


[The Security Descriptor \(xs-security.json\)](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

[Application Router Environment Variables](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-environment-variables-0aac697.md "A list of environment variables that can be used to configure the application router.")

[The Application Descriptor \(xs-app.json\)](../090-HANA-Cloud-DB-Dev-MTA-Routes/the-application-descriptor-96c7545.md "Understand the contents of the file used to configure the multitarget application router.")

[Consume SAP Node.js Packages](../060-HANA-Cloud-DB-Dev-App-Code/consume-sap-node-js-packages-ddcff14.md "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.")

[Download and Consume Java Libraries](../060-HANA-Cloud-DB-Dev-App-Code/download-and-consume-java-libraries-8783c06.md "A selection of SAP-specific and ready-to-use Java client libraries is available for download from the Maven Central Repository.")

[Download and Consume Python Libraries](../060-HANA-Cloud-DB-Dev-App-Code/download-and-consume-python-libraries-842824f.md "A selection of SAP-specific and ready-to-use Python client libraries is available for download from the SAP Service Marketplace.")

[SAP HANA Cloud Deployment-Infrastructure Services](../070-HANA-Cloud-DB-Dev-App-Services/sap-hana-cloud-deployment-infrastructure-services-ebf0aa2.md "The SAP HANA Cloud Deployment Infrastructure service (HDI) is the central infrastructure component for application-container management.")

[Maintain Values in the SAP HANA Secure Store](maintain-values-in-the-sap-hana-secure-store-8a82c9e.md "Insert entries into (and retrieve and remove entries from) the SAP HANA Secure Store.")

[SAP Cloud Security XSUAA Integration \(GitHub\)](https://github.com/SAP/cloud-security-xsuaa-integration/)

[Maven Central Repository](https://mvnrepository.com/search?q=SAP&d=com.sap)

