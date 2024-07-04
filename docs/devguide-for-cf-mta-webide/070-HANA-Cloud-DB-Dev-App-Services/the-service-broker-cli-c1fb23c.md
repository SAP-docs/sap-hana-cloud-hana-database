<!-- loioc1fb23c2e9754e0bb5b67fa44c4e196c -->

# The Service-Broker CLI

Maintain and manage Cloud Foundry services and service brokers, for example: list, create, delete, bind, and update.



```
cf <Service_Broker_COMMAND> <Service_Broker_NAME>
```

```
cf <Service_COMMAND> <Service_NAME>
```

**CF CLI: Services Command Overview**


<table>
<tr>
<th valign="top">

Command

</th>
<th valign="top">

Alias

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`marketplace` 

</td>
<td valign="top">

`m` 

</td>
<td valign="top">

List available services in the marketplace

</td>
</tr>
<tr>
<td valign="top">

`services` 

</td>
<td valign="top">

`s` 

</td>
<td valign="top">

List all services in the target space

</td>
</tr>
<tr>
<td valign="top">

`create-service` 

</td>
<td valign="top">

`cs` 

</td>
<td valign="top">

Create a new service instance

</td>
</tr>
<tr>
<td valign="top">

`update-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Update an existing service instance

</td>
</tr>
<tr>
<td valign="top">

`delete-service` 

</td>
<td valign="top">

`ds` 

</td>
<td valign="top">

Delete a service instance

</td>
</tr>
<tr>
<td valign="top">

`rename-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Rename a service instance

</td>
</tr>
<tr>
<td valign="top">

`bind-service` 

</td>
<td valign="top">

`bs` 

</td>
<td valign="top">

Bind a service instance to an application

</td>
</tr>
<tr>
<td valign="top">

`unbind-service` 

</td>
<td valign="top">

`us` 

</td>
<td valign="top">

Remove the binding between a service instance and an application

> ### Caution:  
> Unbinding a service instance deletes the corresponding HDI containers's run-time \(\_RT\) user, too.



</td>
</tr>
<tr>
<td valign="top">

`bind-route-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Bind a service instance to an HTTP route

</td>
</tr>
<tr>
<td valign="top">

`unbind-route-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Remove the binding between a service instance and an HTTP route

</td>
</tr>
<tr>
<td valign="top">

`service-keys` 

</td>
<td valign="top">

`sks` 

</td>
<td valign="top">

List all service keys for a specified service instance.

</td>
</tr>
<tr>
<td valign="top">

`service-key` 

</td>
<td valign="top">

`sk` 

</td>
<td valign="top">

Displays a service key for a specified service instance.

</td>
</tr>
<tr>
<td valign="top">

`create-service-key` 

</td>
<td valign="top">

`csk` 

</td>
<td valign="top">

Create a service key for a specified service instance.

</td>
</tr>
<tr>
<td valign="top">

`delete-service-key` 

</td>
<td valign="top">

`dsk` 

</td>
<td valign="top">

Delete a service key for a specified service instance.

> ### Caution:  
> Deleting a service key deletes the corresponding HDI containers's run-time \(\_RT\) user, too.



</td>
</tr>
<tr>
<td valign="top">

`create-user-provided-service` 

</td>
<td valign="top">

`cups` 

</td>
<td valign="top">

Create a user-provided service instance and make it available for use by applications. \*

</td>
</tr>
<tr>
<td valign="top">

`update-user-provided-service` 

</td>
<td valign="top">

`uups` 

</td>
<td valign="top">

Update the name-values pairs used to define a user-provided service instance

</td>
</tr>
<tr>
<td valign="top">

`share-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Share a shared service instance from a space

</td>
</tr>
<tr>
<td valign="top">

`unshare-service` 

</td>
<td valign="top">



</td>
<td valign="top">

Unshare a shared service instance from a space

</td>
</tr>
</table>

> ### Note:  
> To access databases not managed by the SAP HANA Service Broker, you can create “user provided services”. To create a user-provided service, you must provide the service credentials for access to the database and bind the service to the application.



<a name="loioc1fb23c2e9754e0bb5b67fa44c4e196c__section_f2s_b3p_hlb"/>

## Services Administration

**CF CLI: Services Administration Command Overview**


<table>
<tr>
<th valign="top">

Command

</th>
<th valign="top">

Alias

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`service-brokers` 

</td>
<td valign="top">



</td>
<td valign="top">

List all available service brokers

</td>
</tr>
<tr>
<td valign="top">

`create-service-broker` 

</td>
<td valign="top">



</td>
<td valign="top">

Create a space-specific service broker \(with the `space-scoped` option\)

</td>
</tr>
<tr>
<td valign="top">

`service-auth-tokens` 

</td>
<td valign="top">



</td>
<td valign="top">

List service authentication tokens

> ### Note:  
> The `service-auth-tokens` command has been deprecated; it only works up to CF API version 2.46.0.



</td>
</tr>
<tr>
<td valign="top">

`create-service-auth-token` 

</td>
<td valign="top">



</td>
<td valign="top">

Create a service authentication token

</td>
</tr>
<tr>
<td valign="top">

`update-service-auth-token` 

</td>
<td valign="top">



</td>
<td valign="top">

Update a service authentication token

</td>
</tr>
<tr>
<td valign="top">

`delete-service-auth-token` 

</td>
<td valign="top">



</td>
<td valign="top">

Delete a service authentication token

</td>
</tr>
<tr>
<td valign="top">

`migrate-service-instances` 

</td>
<td valign="top">



</td>
<td valign="top">

Migrate service instances from one service plan to another

</td>
</tr>
<tr>
<td valign="top">

`purge-service-offering` 

</td>
<td valign="top">



</td>
<td valign="top">

Recursively remove a service and child objects from Cloud Foundry database without making requests to a service broker

</td>
</tr>
<tr>
<td valign="top">

`purge-service-instance` 

</td>
<td valign="top">



</td>
<td valign="top">

Recursively remove a service instance and child objects from Cloud Foundry database without making requests to a service broker

</td>
</tr>
<tr>
<td valign="top">

`service-access` 

</td>
<td valign="top">



</td>
<td valign="top">

List service access settings

</td>
</tr>
<tr>
<td valign="top">

`enable-service-access` 

</td>
<td valign="top">



</td>
<td valign="top">

Enable access to a service or service plan for one or all organizations

</td>
</tr>
<tr>
<td valign="top">

`disable-service-access` 

</td>
<td valign="top">



</td>
<td valign="top">

Disable access to a service or service plan for one or all organizations

</td>
</tr>
</table>

**Related Information**  


[Create a Service Instance](create-a-service-instance-355f3b1.md "Make a service instance available to applications.")

[The Service Brokers](the-service-brokers-662d971.md "Service brokers manage instances of services used by applications running in the Cloud Foundry run time.")

