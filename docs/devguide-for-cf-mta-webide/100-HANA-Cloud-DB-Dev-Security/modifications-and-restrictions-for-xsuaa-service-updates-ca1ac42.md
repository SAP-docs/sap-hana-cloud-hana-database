<!-- loioca1ac4204b1c4a6d8b1cf85c7b4488a9 -->

# Modifications and Restrictions for XSUAA Service Updates

Restrictions apply to which parts of the application's security description you can change and apply when updating an instance of the XSUAA service.



The service broker allows you to update the configuration of an existing service, for example, to change the service plan associated with a service. You can also use a service update to modify the XSUAA service's security configuration, for example, by adding, deleting, or changing the artifacts defined in the `xs-security.json` security descriptor. If you want to use a service-update operation to make changes to the XSUAA service's security configuration, bear in mind that certain restrictions apply, as illustrated in the following table:

**Permitted Changes to xs-security.json when Updating the XSUAA Service**


<table>
<tr>
<th valign="top">

Security Artifacts



</th>
<th valign="top">

Add



</th>
<th valign="top">

Delete



</th>
<th valign="top">

Change



</th>
</tr>
<tr>
<td valign="top">

Authorization Scope



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

You can only modify the scope's:

-   `description`
-   `granted-apps`



</td>
</tr>
<tr>
<td valign="top">

Attribute



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

You can only modify the attribute's:

-   `description`

> ### Note:  
> It is not possible to change an attribute's `valueType` during a service-update operation.



</td>
</tr>
<tr>
<td valign="top">

Role template



</td>
<td valign="top">

✔



</td>
<td valign="top">

✔



</td>
<td valign="top">

You can only modify a role template's:

-   `description`
-   `scope-references`
-   `attribute-references`

> ### Restriction:  
> An attribute reference can only be deleted; it cannot be modified during a service-update operation.



</td>
</tr>
</table>

**Related Information**  


[Create the Security Descriptor for a Multitarget Application](create-the-security-descriptor-for-a-multitarget-application-df31a08.md "The security descriptor defines details of an application's security-related dependencies.")

[The Application Security Descriptor](the-application-security-descriptor-3bfb120.md "A file that defines the details of the authentication methods and authorization types to use for access to your application.")

[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

