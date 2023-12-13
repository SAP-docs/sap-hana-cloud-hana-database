<!-- loio67b375554f434ddfa4444f007ace4b4b -->

# Application Authorization Tasks, Roles, and Tools

An overview of the steps required to set up user authorization for multitarget applications.



Developers store authorization information as design-time role templates in the security descriptor file `xs-security.json`. Using the `xsuaa` service broker, they deploy the security information in a dedicated multitarget application. The administrators view the authorization information in role templates, which they use as part of the run-time configuration. The administrators use the role templates to build roles, which are aggregated in role collections. The role collections are assigned, in turn, to business users.

The tasks required to set up authorization artifacts in Cloud Foundry on SAP Business Technology Platform are performed by two distinct user roles: the application developer and the SAP HANA administrator. After the deployment of the authorization artifacts as role templates, the administrator of the multitarget application uses the role templates provided by the developers to build role collections and assign them to business users, for example, using in the *SAP Cockpit* section of the *SAP HANA Cloud Administration Guide*.

**Setting Up Authorization Artifacts**


<table>
<tr>
<th valign="top">

Step

</th>
<th valign="top">

Task

</th>
<th valign="top">

User Role

</th>
<th valign="top">

Tool

</th>
</tr>
<tr>
<td valign="top">

1

</td>
<td valign="top">

Specify the security descriptor file containing the functional authorization scopes for your application

</td>
<td valign="top">

Application developer

</td>
<td valign="top">

Text editor

</td>
</tr>
<tr>
<td valign="top">

2

</td>
<td valign="top">

Create role templates for the multitarget application using the security descriptor file

</td>
<td valign="top">

Application developer

</td>
<td valign="top">

Text editor

</td>
</tr>
<tr>
<td valign="top">

3

</td>
<td valign="top">

Create a service instance from the `xsuaa` service in Cloud Foundry using the service broker

</td>
<td valign="top">

Application developer

</td>
<td valign="top">

CF CLI tool

</td>
</tr>
<tr>
<td valign="top">

4

</td>
<td valign="top">

Bind the service instance to the multitarget application by including it into the manifest file

</td>
<td valign="top">

Application developer

</td>
<td valign="top">

Text editor

</td>
</tr>
<tr>
<td valign="top">

5

</td>
<td valign="top">

Deploy the multitarget application

</td>
<td valign="top">

Application developer

</td>
<td valign="top">

CF CLI tool

</td>
</tr>
<tr>
<td valign="top">

6

</td>
<td valign="top">

If required, create a new role in the application role builder using role templates

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Application role builder

</td>
</tr>
<tr>
<td valign="top">

7

</td>
<td valign="top">

Create a role collection and assign roles to it

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Application role builder

</td>
</tr>
<tr>
<td valign="top">

8

</td>
<td valign="top">

Assign the role collection to a SAML 2.0 identity provider or to SAP HANA database users

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

Application role builder, and SAML IDP Tool

</td>
</tr>
<tr>
<td valign="top">

9

</td>
<td valign="top">

Assign the users to roles using the role collections

</td>
<td valign="top">

Administrator

</td>
<td valign="top">

SAP BTP cockpit

</td>
</tr>
</table>

**Related Information**  


[Set up Generic Authorization for a Multitarget Application](set-up-generic-authorization-for-a-multitarget-application-c8c578e.md "Define an authorization model for your multitarget application and configure generic authorization for any application end point (route path).")

[Application Security Tools and Components](application-security-tools-and-components-a004e4f.md "Setting up security for multitarget applications involves multiple tasks and multiple tools and components.")

