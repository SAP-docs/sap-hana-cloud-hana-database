<!-- loio0393ce339acf49bf97b17c671ce92b9f -->

# Service Plans and Resources

A service plan is a particular type of service \(for example, a database configuration\) that is available for use.



A service broker advertises **service plans** using the service catalog. You can use the advertised plans to configure the service you want to create. For example, you can use the “`hdi-shared`” service plan to create a plain HDI container on a shared SAP HANA database system. The service plan is mapped to a corresponding application “resource type” that is typically specified in the `resources` section of the application's MTA deployment descriptor \(`mtad.yaml`\).

For example, the resource type “`com.sap.xs.hdi-shared`” is mapped to the “`hana`” service plan “`hdi-shared`”; the resource type “`com.sap.xs.uaa-application`” is mapped to the “`xsuaa`” service plan “`application`”.

To display details of the service plans that are available for a particular service, use the `cf marketplace` command with the `-e` option, as illustrated in the following example:

> ### Sample Code:  
> Display Details of the Service Plans Offered for a Specific Service
> 
> ```
> $ cf marketplace -e hana
> Getting service plan information for service hana as admin...
> OK
> 
> service plan   description                                 free or paid
> 
> hdi-shared     HDI container on a HANA database            free
> schema         Schema on a HANA database                   free
> securestore    User with permissions to use secure store   free
> ```

Similar information is available in the *Service Marketplace* in SAP BTP cockpit, where a longer and more descriptive label is assigned to some of the service names listed in the table below, for example, *Audit Log Management Service* \(`auditlog-management`\) or *SAP HANA Schemas and HDI Containers* \(`hana`\).

> ### Note:  
> The list of services displayed in the Service Marketplace is determined by the `Entitlements` \(services you are **entitled** to use\) configured for the corresponding SAP BTP subaccount. If you are not entitled to use a service, you will not see it listed in the Service Marketplace, and the SAP BTP administrator will have to add the new \(or missing\) service to the list of entitlements manually, for example, in the SAP BTP cockpit.

**Services, Service Plans, and MTA Resources**


<table>
<tr>
<th valign="top">

Service

</th>
<th valign="top">

Service Plan

</th>
<th valign="top">

Platform

</th>
<th valign="top">

Resource

</th>
<th valign="top">

Created Service

</th>
</tr>
<tr>
<td valign="top">

auditlog-api

</td>
<td valign="top">

default

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.auditlog

</td>
<td valign="top" rowspan="2">

Audit-log service

</td>
</tr>
<tr>
<td valign="top">

auditlog-management

</td>
<td valign="top">

default

</td>
<td valign="top">

CF

</td>
<td valign="top">

auditlog

</td>
</tr>
<tr>
<td valign="top" rowspan="3">

hana

</td>
<td valign="top">

hdi-shared

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.hdi-container

</td>
<td valign="top">

HDI container service

</td>
</tr>
<tr>
<td valign="top">

schema

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.hana-schema

</td>
<td valign="top">

Plain schema service

</td>
</tr>
<tr>
<td valign="top">

securestore

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.hana-securestore

</td>
<td valign="top">

SAP HANA secure-store service

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

xsuaa

</td>
<td valign="top">

application

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.uaa-application

</td>
<td valign="top">

PaaS-enabled UAA application service plan for CF scenarios

</td>
</tr>
<tr>
<td valign="top">

apiaccess

</td>
<td valign="top">

CF

</td>
<td valign="top">

com.sap.xs.uaa-apiaccess

</td>
<td valign="top">

Access Plan for Authorization, Users and IDPS API endpoints in CF

</td>
</tr>
<tr>
<td valign="top">

application-logs

</td>
<td valign="top">

lite

</td>
<td valign="top">

CF

</td>
<td valign="top">

application-logs

</td>
<td valign="top">

Streams the logs of bound applications to a central application logging stack

</td>
</tr>
<tr>
<td valign="top">

autoscaler

</td>
<td valign="top">

standard

</td>
<td valign="top">

CF

</td>
<td valign="top">

autoscaler

</td>
<td valign="top">

Automatically increases or decreases the number of application instances based on a policy you define.

</td>
</tr>
<tr>
<td valign="top">

connectivity

</td>
<td valign="top">

lite

</td>
<td valign="top">

CF

</td>
<td valign="top">

connectivity

</td>
<td valign="top">

Establishes secure, reliable connectivity between Cloud applications and on-premise systems

</td>
</tr>
<tr>
<td valign="top">

content-agent

</td>
<td valign="top">

standard

application

</td>
<td valign="top">

CF

</td>
<td valign="top">

content-agent

</td>
<td valign="top">

Enables you to view, export, and import application content and track all activity along with logs, status, etc.

</td>
</tr>
<tr>
<td valign="top">

destination

</td>
<td valign="top">

lite

</td>
<td valign="top">

CF

</td>
<td valign="top">

destination

</td>
<td valign="top">

Retrieves the back-end destination details that you need to configure applications in the Cloud Foundry environment.

</td>
</tr>
<tr>
<td valign="top">

feature-flags

</td>
<td valign="top">

lite

standard

</td>
<td valign="top">

CF

</td>
<td valign="top">

feature-flags

</td>
<td valign="top">

Enables the use of feature flags to the control the rollout of product features

</td>
</tr>
<tr>
<td valign="top">

objectstore

</td>
<td valign="top">

s3-standard

</td>
<td valign="top">

CF

</td>
<td valign="top">

objectstore

</td>
<td valign="top">

Provides a highly available, distributed, consistent object store for CF applications. Service plan corresponds to the underlying infrastructure: Microsoft Azure Blobs, AWS S3 buckets, Google Cloud buckets, etc.

</td>
</tr>
<tr>
<td valign="top">

saas-registry

</td>
<td valign="top">

application

</td>
<td valign="top">

CF

</td>
<td valign="top">

saas-registry

</td>
<td valign="top">

Enables application providers to register multitenant applications and services and manage the application lifecycle

</td>
</tr>
<tr>
<td valign="top">

lps-service

</td>
<td valign="top">

resource

service

</td>
<td valign="top">

CF

</td>
<td valign="top">

lps-service

</td>
<td valign="top">

Enables access to SaaS API to retrieve resources from resource providers and update the dependencies of SaaS tenants

</td>
</tr>
</table>

**Related Information**  


[MTA Deployment Descriptor Syntax](../030-HANA-Cloud-DB-Dev-Deployment/mta-deployment-descriptor-syntax-4050fee.md "Description of an MTA's deployment-related prerequisites and dependencies.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Service Types](service-types-9baaaf2.md "The services provided in Cloud Foundry are available in different types.")

[SAP Discovery Center \(Services\)](https://discovery-center.cloud.sap/protected/index.html#/viewServices)

[Managing Services Using the SAP BTP Cockpit \(SAP Service Manager\)](https://help.sap.com/docs/SERVICEMANAGEMENT/09cc82baadc542a688176dce601398de/cdce096d411242bcbfb9644d0860fd0f.html?version=Cloud)

