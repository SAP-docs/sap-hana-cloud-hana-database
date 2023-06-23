<!-- loio8635e0b43f6744d6b40ba247b11b352e -->

# Multitarget Application Resource Files

SAP HANA Cloud multitarget applications require some mandatory configuration artifacts.

In SAP HANA Cloud, multitarget applications require a number of mandatory configuration and deployment files. Which files are required depends on the language you are using to develop the application, for example, JavaScript \(including node.js\) or Java, and the deployment options you need. The following table provides an overview of the artifacts required by each application. There are rules and requirements concerning where to store these artifacts in the application folder hierarchy.

**Application Artifacts Overview**


<table>
<tr>
<th valign="top">

File Name



</th>
<th valign="top">

Description



</th>
<th valign="top">

Database



</th>
<th valign="top">

App Router



</th>
<th valign="top">

Node/JS



</th>
<th valign="top">

Java



</th>
<th valign="top">

Python



</th>
</tr>
<tr>
<td valign="top">

 `mta.yaml` 



</td>
<td valign="top">

MTA development descriptor



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
</tr>
<tr>
<td valign="top">

 `mtad.yaml` 



</td>
<td valign="top">

MTA deployment descriptor



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
</tr>
<tr>
<td valign="top">

 `package.json` 



</td>
<td valign="top">

Description and dependencies of node modules



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `xs-app.json` 



</td>
<td valign="top">

Application router description



</td>
<td valign="top">



</td>
<td valign="top">

✔



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `*.hdi*` 



</td>
<td valign="top">

Configuration artifacts for the SAP HANA Cloud deployment infrastructure \(HDI\), for example, `.hdiconfig` and `.hdinamespace` 



</td>
<td valign="top">

✔



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `*.java` 



</td>
<td valign="top">

Java application source files



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

✔



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `*.js` 



</td>
<td valign="top">

JavaScript \(node.js\) source files



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

✔



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

 `*.py` 



</td>
<td valign="top">

Python source files



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

✔



</td>
</tr>
<tr>
<td valign="top">

 `xs-security.json` 



</td>
<td valign="top">

Shared description of OAuth2 client



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
</tr>
</table>

> ### Note:  
> If you use SAP Web IDE Full-Stack to develop an MTA, both the `mta.yaml` \(**development** descriptor\) and the `mtad.yaml` \(**deployment** descriptor\) are created automatically. The `mta.yaml` is generated when you create the application project in SAP Web IDE Full-Stack, and the `mtad.yaml` file is created when you build the project.
> 
> The command-line Cloud MTABuild Tool \(MBT\) requires either a development descriptor \(`mta.yaml`\) or a deployment descriptor \(`mtad.yaml`\) to build an MTA.

**Related Information**  


[Maintaining the Multitarget Application Development & Deployment Descriptors](../030-HANA-Cloud-DB-Dev-Deployment/maintaining-the-multitarget-application-development-deployment-descriptors-b2e355a.md "Development descriptors are used to generate deployment descriptors, which define the details required at application-deployment time.")

[The Application Descriptor](../090-HANA-Cloud-DB-Dev-MTA-Routes/the-application-descriptor-96c7545.md "Understand the contents of the file used to configure the multitarget application router.")

[The Multitarget Application Package Descriptor](../060-HANA-Cloud-DB-Dev-App-Code/the-multitarget-application-package-descriptor-0818c56.md "A file describing the prerequisites and dependencies that apply to a JavaScript multitarget application in Cloud Foundry on SAP Business Technology Platform.")

[The SAP HDI Container Configuration File](../040-HANA-Cloud-DB-Dev-Persistence-Model/the-sap-hdi-container-configuration-file-6400400.md "Bind design-time file types to the corresponding build plug-in required in the SAP HANA Deployment Infrastructure (HDI).")

[The HDI Name-Space Configuration File](../040-HANA-Cloud-DB-Dev-Persistence-Model/the-hdi-name-space-configuration-file-6188d22.md "The SAP HANA Deployment Infrastructure (HDI) uses a JSON resource to define naming rules for run-time objects.")

[The Application Security Descriptor](../100-HANA-Cloud-DB-Dev-Security/the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

