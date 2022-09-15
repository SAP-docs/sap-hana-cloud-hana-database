<!-- loio35d910ee7c7a445a950b6aad989a5a26 -->

# Maintaining Application Security in Cloud Foundry on SAP BTP

Set up the security components required in the context of multitarget applications on SAP BTP .

SAP multitarget applications contain content \(for example, Web content and micro services\), which is deployed to different containers. Static Web content is deployed to the application router; application logic is deployed to Node.js and Java containers; database logic is deployed to the SAP HANA database. Access to the content requires user identification and authentication as well as the appropriate authorization. Additional security can be built into the business logic code \(Java or JavaScript\) and the SQL connection to the database.

> ### Note:  
> For more information about the tools available to enhance security in the application code, itself, see the sections describing the Java and JavaScript run-time environments in this guide. For more information about enhancing security in SQL and SQLScript, see the corresponding SQL and SQLScript Reference Guides.

An multitarget application must be able to identify and authenticate users, and ensure that the required authorizations are defined and granted, too.

The authentication process is triggered by the application router component, which is configured in the design-time artifact `xs-app.json`, often referred to as the Application Descriptor. Authorizations are defined in the security descriptor \(`xs-security.json`\) with so-called scopes; authorization scopes enable you to restrict access to resources based on user permissions specified in role templates. In the context of multitarget applications, “resources” are services provided by a container \(for example, an OData Web service\) or SAP HANA database artifacts such as tables and views in an HDI container.

Multitarget applications perform the authentication process with OAuth 2.0; the applications use the XS User Account and Authentication \(UAA\) service as an “OAuth 2.0 authorization server”. The OAuth 2.0 client is the application router, and the role of the “OAuth 2.0 resource server” is performed by the application logic running in Node.js and Java back-end services.



<a name="loio35d910ee7c7a445a950b6aad989a5a26__section_cjx_ynv_m2b"/>

## The Security Descriptor

The central component for the configuration and maintenance of application security is the `xs-security.json` file, which is often referred to as the Security Descriptor. The contents of the `xs-security.json` file describe any required user authorizations \(for example, with OAuth 2\) using scopes \(view, edit\), attributes \(dynamically defined cost center, department, etc.\), and role templates \(used to build roles\).

> ### Sample Code:  
> ```
> AppName
> |- db/                         
> |  |- package.json              
> |  |- src/                      
> |     |- .hdiconfig             
> |     |- .hdinamespace          
> |     |- myEntity.hdbtable        
> |     |- myView.hdbview      
> |     \- myCalcview.hdbcalculationview           
> |- web/                         
> |  |- xs-app.json               
> |  \- resources/                
> |- js/
> |  |- start.js                
> |  |- package.json                         
> |  \- src/                    
> |- xs-security.json        # Security artifacts/scopes/auths
> |- manifest.yml
> \- mtad.yaml
> 
> ```

**Related Information**  


[Authorization in SAP HANA Services and Resources](authorization-in-sap-hana-services-and-resources-e8dde5f.md "Authorization restricts access to resources and services based on defined user permissions.")

[Set up Application Security](set-up-application-security-b823639.md "Help ensure a multitarget application is protected from Web-based attacks.")

[Create the Security Descriptor for a Multitarget Application](create-the-security-descriptor-for-a-multitarget-application-df31a08.md "The security descriptor defines details of an application's security-related dependencies.")

[The Cloud Foundry JavaScript Run Time](../060-HANA-Cloud-DB-Dev-App-Code/the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

[The Cloud Foundry Java Run Time](../060-HANA-Cloud-DB-Dev-App-Code/the-cloud-foundry-java-run-time-2b5a9a4.md "SAP Business Technology Platform provides a Cloud Foundry Java run time to which you can deploy your Java applications.")

[The Cloud Foundry Python Run Time](../060-HANA-Cloud-DB-Dev-App-Code/the-cloud-foundry-python-run-time-8d786ec.md "SAP Business Technology Platform provides a Cloud Foundry Python run time to which you can deploy your Python applications.")

