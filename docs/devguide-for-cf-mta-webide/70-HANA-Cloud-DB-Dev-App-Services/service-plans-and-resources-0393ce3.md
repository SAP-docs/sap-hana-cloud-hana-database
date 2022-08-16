<!-- loio0393ce339acf49bf97b17c671ce92b9f -->

# Service Plans and Resources

A service plan is a particular type of service \(for example, a database configuration\) that is available for use.



A service broker advertises **service plans** using the catalog. You can use the advertised plans to configure the service you want to create. For example, you can use the “`hdi-shared`” service plan to create a plain HDI container on a shared SAP HANA database system. The service plan is mapped to a corresponding application “resource type” that is typically specified in the `resources` section of the application's MTA deployment descriptor \(`mtad.yaml`\).

For example, the resource type “`com.sap.xs.hdi-shared`” is mapped to the “`hana`” service plan “`hdi-shared`”; the resource type “`com.sap.xs.uaa-application`” is mapped to the “`xsuaa`” service plan “`application`”.

> ### Tip:  
> For more information about the service plans available with a particular service, see *Discovery Center* in *Related Information* below. Similar information is available in the *Service Marketplace* in SAP BTP cockpit.

<a name="loio0393ce339acf49bf97b17c671ce92b9f__table_vxy_hcx_bz"/>Services, Service Plans, and MTA Resources


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
<td valign="top">

portal



</td>
<td valign="top">

standard



</td>
<td valign="top">

CF



</td>
<td valign="top">

portal



</td>
<td valign="top">

Portal DB site-host, content, and admin service



</td>
</tr>
<tr>
<td valign="top">

sds



</td>
<td valign="top">

default



</td>
<td valign="top">

CF



</td>
<td valign="top">

com.sap.xs.sds



</td>
<td valign="top">

Global streaming analytics service



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

xsuaa



</td>
<td valign="top">

space



</td>
<td valign="top">

CF



</td>
<td valign="top">

com.sap.xs.uaa-space



</td>
<td valign="top">

UAA service for a space



</td>
</tr>
<tr>
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

Streams logs of bound applications to a central application logging stack



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

Automatically increase or decrease the number of application instances based on a policy you define.



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

Feature Flags service for the control of feature rollout



</td>
</tr>
<tr>
<td valign="top">

ml-foundation-services



</td>
<td valign="top">

lite



</td>
<td valign="top">

CF



</td>
<td valign="top">

ml-foundation-services



</td>
<td valign="top">

Provides access to foundation services by provisioning and deprovisioning “ml foundation” services



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
</table>

**Related Information**  


[MTA Deployment Descriptor Syntax](../30-HANA-Cloud-DB-Dev-Deployment/mta-deployment-descriptor-syntax-4050fee.md "Description of an MTA's deployment-related prerequisites and dependencies.")

[Core Application Services](core-application-services-b0200e9.md "A selection of essential application services are available with the run-time platform.")

[Service Types](service-types-9baaaf2.md "The services provided in Cloud Foundry are available in different types.")

[SAP Discovery Center \(Services\)](https://discovery-center.cloud.sap/protected/index.html#/viewServices)

