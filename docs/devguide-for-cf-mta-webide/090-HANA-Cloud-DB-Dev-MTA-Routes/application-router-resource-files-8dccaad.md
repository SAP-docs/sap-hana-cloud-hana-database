<!-- loio8dccaad632964b96877924bc25376ff9 -->

# Application-Router Resource Files

The routing configuration for an application is defined in one or more so-called "destinations" that are defined in a destinations configuration.



The application router is used to serve static content, authenticate users, rewrite URLs, and forward \(or proxy\) requests to other micro services while propagating user information. The following table lists the configuration files used to define routes for multitarget applications:

**Application-Router Resource Files Overview**


<table>
<tr>
<th valign="top">

File

</th>
<th valign="top">

Description

</th>
<th valign="top">

Mandatory

</th>
</tr>
<tr>
<td valign="top">

`package.json` 

</td>
<td valign="top">

The package descriptor is used by the node.js package manager \(`npm`\) to start the application router; in the <code>“dependencies”: {} section</code> 

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`xs-app.json` 

</td>
<td valign="top">

The application descriptor contains the configuration used by the application router \(for example, destinations for request forwarding\)

</td>
<td valign="top">

Yes

</td>
</tr>
<tr>
<td valign="top">

`resources/` 

</td>
<td valign="top">

A folder that contains all static resources which should be served by the application router. If no `resources/` folder is present, the application router will not serve any static content. However, it still forwards requests to the configured destinations.

> ### Tip:  
> Static resources can be stored in multiple folders, and the folder name “`resources/`” is optional.



</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

`default-services.json` 

</td>
<td valign="top">

Defines the configuration for one or more special User Account and Authentication \(UAA\) services for local development; this is typically used for testing in local environments.

</td>
<td valign="top">

\-

</td>
</tr>
</table>

**Related Information**  


[Configure the Multitarget Application Router](configure-the-multitarget-application-router-6ba8959.md "The application routes to the available microservices are described in the xs-app.json file.")

