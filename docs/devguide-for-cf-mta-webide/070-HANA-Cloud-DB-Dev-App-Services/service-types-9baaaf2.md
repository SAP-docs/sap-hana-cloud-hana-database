<!-- loio9baaaf2399f2499a90c58a85b204cd17 -->

# Service Types

The services provided in Cloud Foundry are available in different types.



Multitarget applications running in Cloud Foundry can make use of services that are either created by a user or available for general use in the service market place. Services available in the Service Marketplace are managed by a service broker. The following table lists and explains the types of service to which you can bind your multitarget applications:

**Cloud Foundry Service Types**


<table>
<tr>
<th valign="top">

Service Type

</th>
<th valign="top">

Description

</th>
<th valign="top">

Example

</th>
</tr>
<tr>
<td valign="top">

Managed

</td>
<td valign="top">

Services that are available in pre-configured scopes in the Service Marketplace for Cloud Foundry

</td>
<td valign="top">

`xsuaa`

`hana`

`auditlog`

`portal-services`

</td>
</tr>
<tr>
<td valign="top">

User-provided

</td>
<td valign="top">

Services that are provided on demand and by hand for use by applications in a specific, dedicated space. User-provided services are **not** available in \(or managed by\) the Service Marketplace and are not associated with a service plan. Unlike managed services, user-provided services do not include any automatic provisioning of resources or credentials; these must by provided manually.

</td>
<td valign="top">

`-` 

</td>
</tr>
</table>

To display a list the services running in the current organizational space, log in to an Cloud Foundry space and run the `services` command, as illustrated in the following example:

```
$ cf services

Getting services in org "myorg" / space "SAP" as ADMIN...
Found services:

name                      service        plan         bound apps
-----------------------------------------------------------------------
myHdiService              hana           hdi-shared   xml_app
myUaaService              xsuaa          application  xml_app
cf-cockpit-db             hana           schema       cf-cockpit
cf-cockpit-uaa            xsuaa          application  cf-cockpit
```

For details of the services available in the service marketplace, and the corresponding service plans, use the `marketplace` command, as illustrated in the following example:

```
$ cf marketplace
Getting services from marketplace in org acme / space devel as admin...
OK

service              plans                            description                     broker
----------------------------------------------------------------------------------------------------------
hana                 hdi-shared, schema, securestore  SAP HANA database               sm-hana-broker...
xsuaa                space, application, apiaccess    Manage app authorizations...    sm-xsuaa-...
application-logs     lite                             Create, store, access...        sm-sleeve-broker...
... 
autoscaler           standard                         Automatically increase or...    sm-autoscaler-brok...
auditlog-api         default                          Audit log API...                sm-auditlog-api-...
auditlog-management  default                          Retrieve logs and change...     sm-auditlog-manage...
...
```

**Related Information**  


[Maintaining Multitarget Application Services in Cloud Foundry](maintaining-multitarget-application-services-in-cloud-foundry-33e3c59.md "In Cloud Foundry, applications can make use of services managed by a service broker.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Service Plans and Resources](service-plans-and-resources-0393ce3.md "A service plan is a particular type of service (for example, a database configuration) that is available for use.")

