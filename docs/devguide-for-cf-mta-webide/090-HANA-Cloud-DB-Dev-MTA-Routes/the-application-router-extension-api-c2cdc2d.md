<!-- loioc2cdc2d2237e4c7ba47dc2a9d54645eb -->

# The Application Router Extension API

A detailed list of the features and functions provided by the application router extension API.



The application router extension API enables you to create new instances of the application router, manage the `approuter` instance, and insert middleware using the Node.js “connect” framework. This section contains detailed information about the following areas:

-   Approuter Extension API Reference

-   Middleware Slot




<a name="loioc2cdc2d2237e4c7ba47dc2a9d54645eb__section_ijc_vmh_wx"/>

## Middleware Slot

Manage the insertion of middleware slots with the application router.

**Middleware Slot Management**


<table>
<tr>
<th valign="top">

Function



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `use(path, handler)` 



</td>
<td valign="top">

Inserts a request handling middleware in the current slot.

-   `path`

    Handle only requests starting with this path \(string, optional\)

-   `handler`

    A middleware function to invoke \(function, mandatory\)


Returns `this` for chaining.



</td>
</tr>
</table>

**Related Information**  


[Maintaining Multitarget Application Routes and Destinations](maintaining-multitarget-application-routes-and-destinations-0117b71.md "Define application routes and destinations.")

[Application Router Extensions](application-router-extensions-caaa92b.md "Configure application-specific extensions to the application router.")

[Middleware Connect Framework](https://github.com/senchalabs/connect)

