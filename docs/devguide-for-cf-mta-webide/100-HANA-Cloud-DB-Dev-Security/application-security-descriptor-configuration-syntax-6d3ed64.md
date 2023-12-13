<!-- loio6d3ed64092f748cbac691abc5fe52985 -->

# Application Security Descriptor Configuration Syntax

The syntax required to set the properties and values defined in the `xs-security.json` application-security description file.



> ### Tip:  
> The following code-syntax example is for illustration purposes only; it contains links to further information. Click an attribute, for example, <code>“scopes”</code> to navigate to the section where the selected attribute is described in more detail.

> ### Sample Code:  
> The Application Security Descriptor Syntax \(`xs-security.json`\)
> 
> ```
> {
>   "xsappname" : "node-hello-world",
>   "tenant-mode"   : "shared", 
>   "scopes"     : [ { 
>                     "name" : "$XSAPPNAME.Edit", 
>                     "description" : "edit", 
>                     "granted-apps":  ["$XSAPPNAME","$XSAPPNAME(application,zone-guid-1,$XSAPPNAME)"],
>                     "grant-as-authority-to-apps" : ["$XSAPPNAME"]} 
>                  ], 
>   "foreign-scope-references": ["$ACCEPT_GRANTED_SCOPES"], 
>   "authorities":["$ACCEPT_GRANTED_AUTHORITIES"],
>   "attributes" : [ { 
>                     "name" : "Country", 
>                     "description" : "Country", 
>                     "valueType" : "string" }, 
>                    {
>                     "name" : "CostCenter", 
>                     "description" : "CostCenter", 
>                     "valueType" : "string" } 
>                  ], 
>   "role-templates": [ { 
>                     "name"               : "Editor", 
>                     "description"        : "Edit, delete books", 
>                     "scope-references"   : [ "$XSAPPNAME.Edit", 
>                                              "$XSAPPNAME.Delete" ], 
>                     "attribute-references" : ["Country", "CostCenter"] } 
>                    ], 
>   "oauth2-configuration": {
>                     "token-validity": 900, 
>                     "refresh-token-validity": 1800, 
>                     "redirect-uris": [	
>                                       "https://<host_name1>",
>                                       "https://<host_name2>"],  
>                     "autoapprove": "false", 
>                     "system-attributes": ["groups", "rolecollections"], 
>                     "allowedproviders": ["useridp1", "useridp2"] } 
> }
> 
> ```



<a name="loio6d3ed64092f748cbac691abc5fe52985__section_rhj_kn4_dt"/>

## xsappname

Use the `xsappname` property to specify the name of the application\(s\) to which the security description applies.

> ### Sample Code:  
> ```json
> 
>   "xsappname" "<app-name>",
> 
> ```

The `xsappname` property represents a developer-defined part of a system-generated OAuth Client ID. Since an OAuth Client ID must be unique within a given subaccount \(pka "identity zone"\), the `xsappname` property must be defined in such a way as to guarantee the uniqueness of the corresponding OAuth Client ID.

> ### Tip:  
> It is important to ensure that the name defined in `xsappname` can be easily recognized by other users when configuring additional security components, for example, when administrators are creating roles from role templates. See also *Blacklisted Application Names* below for a list of application names that are not permitted, for example, "zones" or "oauth".



### Naming Conventions

Bear in mind the following restrictions regarding the length and content of an application name in the `xs-security.json` file:

-   The following characters can be used in a multitarget application name: “aA”-“zZ”, “0”-“9”, “-” \(dash\), “\_” \(underscore\), “/” \(forward slash\), and “\\” \(backslash\)

-   The maximum length of an multitarget application name is 128 characters.


You can also include the other Cloud-Foundry-related plan: `application`. The suffix added to the `xsappname` has the format: <code>"!b<i class="varname">&lt;tenant index&gt;</i>"</code>, where *<tenant index\>* is a number that the UAA maintains internally and differs from landscape to landscape, for example, `myapp!i8`.

> ### Caution:  
> It is not recommended to rely on the application-name format used in the examples above, for example, by parsing code in order to retrieve the service plan used with a particular application instance. However, the general format of the application name is relevant, for example, when using the *Application Role Builder* tool to maintain application roles in the Cloud Cockpit.



### Invalid Application Names

It is not permitted to use any of the following names in the `xsappname` property:

-   "zones"

-   "clients"

-   "scim"

-   "password"

-   "oauth"

-   "approvals"

-   "groups"

-   "uaa"

-   "sap\_system"




### References to the Application Identity

You can use any of the following methods to refer to the application identity \(`appid`\) defined in the `xsappname` property:

-   `$XSAPPNAME`

    Used for references to the `"xsappname"` specified in the local `xs-security.json` security-descriptor file

-   <code>$XSAPPNAME(<i class="varname">&lt;plan&gt;</i>,<i class="varname">&lt;xsappname&gt;</i>)</code>

    Used for references to the specified `"xsappname"` in the subaccount of the current application

    > ### Restriction:  
    > For use in Cloud-Foundry environments only; the XSUAA service plan must be a PaaS-enabled plan, for example, “application”.




<a name="loio6d3ed64092f748cbac691abc5fe52985__section_myf_zzy_2bb"/>

## tenant-mode

In multi-tenant environments, tenants subscribe to and consume applications, which are registered as clients at the XS UAA. XS UAA creates a new OAuth2 client per application for each tenant. You can use the custom `tenant-mode` property to define the way the tenant's OAuth clients obtain their respective client secrets.

During the binding of the `xsuaa` service, the service broker writes the specified tenant mode into the service-broker credentials section. The application router uses the tenant-mode information for the implementation of multi-tenancy with the application's bound service plan.

> ### Sample Code:  
> ```json
> { 
>   "xsappname"   : "<application_name>", 
>   "tenant-mode" : "shared", 
>   "scopes"      : [ 
>                    { 
>                     "name"         : "$XSAPPNAME.Display", 
>                     "description"  : "display" }
>                   ],
> [...]
> } 
> 
> ```

The following tenant modes are available:

**Tenant Modes**


<table>
<tr>
<th valign="top">

Value

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`dedicated` 

</td>
<td valign="top">

The OAuth client receives a separate client secret for each subaccount. \(Default\)

If no value is specified for `tenant-mode`, the default value is assumed.

</td>
</tr>
<tr>
<td valign="top">

`shared` 

</td>
<td valign="top">

The OAuth client uses the same client secret in all subaccounts that subscribe to the application configured with this tenant mode. The `shared` tenant mode is mandatory for an application router configured for multi-tenancy applications, and the application router variable `TENANT_HOST_PATTERN` and a corresponding route must be mapped.

> ### Tip:  
> The `shared` tenant mode is used by the UAA `application` service plan intended for use with PaaS-enabled applications and in combination with Cloud Foundry resources.



</td>
</tr>
<tr>
<td valign="top">

`external` 

</td>
<td valign="top">

For tenants with multiple subscriptions to applications. For each subscription to an application the tenant receives an OAuth client with a client secret.

</td>
</tr>
</table>



<a name="loio6d3ed64092f748cbac691abc5fe52985__section_tch_vqr_xs"/>

## scopes

In the application-security file \(`xs-security.json`\), the `scopes` property defines an array of one or more security scopes that apply for an application. You can define multiple `scopes`; each scope has a name and a short description. The list of scopes defined in the `xs-security.json` file is used to authorize the OAuth client of the multitarget application with the correct set of **local** and **foreign** scopes; that is, the permissions the application requires to be able to respond to all requests.

> ### Sample Code:  
> Defining Local Scopes in the Security Descriptor
> 
> ```json
> "scopes": [ 
>     { 
>      "name" : "$XSAPPNAME.Display", 
>      "description" : "display" }, 
>     { 
>      "name" : "$XSAPPNAME.Edit", 
>      "description" : "edit" }, 
>     { 
>      "name" : "$XSAPPNAME.Delete", 
>      "description" : "delete"  }
> ], 
> 
> ```

Scopes are mostly “local”; that is, application-specific. Local scopes are checked by the application's own application router or checked programmatically within the application's run-time container. In the event that an application needs access to other services on behalf of the current user, the provided access token needs to contain the necessary “foreign” scopes. Foreign scopes are not provided by the application itself; they are checked by other sources outside the context of the application. For more information about how and where to use foreign scopes, see `foreign-scope-references` and `authorities`.

In the `xs-security.json` file, “local” scopes must be prefixed with the variable *<$XSAPPNAME\>*; at run time, the variable is replaced with the name of the corresponding local application name. Using a static application name could lead to deployment problems where the name's index suffix changes depending on the landscape. For more information, see *References to Application Identity* in the property ["xsappname"](application-security-descriptor-configuration-syntax-6d3ed64.md#loio6d3ed64092f748cbac691abc5fe52985__section_rhj_kn4_dt) above.

> ### Tip:  
> The variable *<$XSAPPNAME\>* is defined in the application's deployment manifest description \(`mtad.yaml` or `manifest.yml`\).

The following table lists the parameters and values that can be used with the `scopes` property:

**Parameters and Values for "scopes"**


<table>
<tr>
<th valign="top">

Key

</th>
<th valign="top">

Mandatory

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

`name` 

</td>
<td valign="top">

Yes

</td>
<td valign="top">

Name of the local scope, which must be prefixed with the name of the multitarget application defined in the property `"xsappname"`. It is highly recommended to prefix the scope name with the variable `$XSAPPNAME` in order to reference the element "xsappname" of the `xs-security.json` file. The `"name"` can contain up to 193 characters, must not start with a period '.' \(dot\), and cannot include any characters include in the so-called "denylist". Permitted characters include: 'a'-'z', 'A'-'Z', '0'-'9', '\_', '-', '\\', '/', ':', and '.'

</td>
<td valign="top">

`"$XSAPPNAME.LRApprove"` 

</td>
</tr>
<tr>
<td valign="top">

`description` 

</td>
<td valign="top">

Yes

</td>
<td valign="top">

A short summary of the specified scope; `"description"` must not be longer than 1000 characters.

</td>
<td valign="top">



</td>
</tr>
<tr>
<td valign="top">

`granted-apps` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Array of application-id values. It is highly recommended to use the `$XSAPPNAME` functions to reference the `appid` value of other Cloud Foundry applications. The value '\*' is allowed if the scope is intended to be granted to all applications, and for this reason should only be used with extreme care. `granted-apps` is only relevant for user scenarios.

> ### Restriction:  
> Value '\*' does not work if the receiving application defines `"$ACCEPT_GRANTED_SCOPES"` with the property `"foreign-scope-references"` in its `xs-security.json` file.



</td>
<td valign="top">

`["LR2","$XSAPPNAME(application,LR3)"],`

`["*"],`

</td>
</tr>
<tr>
<td valign="top">

`grant-as-authority-to-apps` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Array of application-id values. It is highly recommended to use the `$XSAPPNAME` functions to reference the application ID value of other Cloud Foundry applications. `grant-as-authority-to-apps` is only relevant for client-credential scenarios.

> ### Restriction:  
> Value '\*' is not permitted.



</td>
<td valign="top">

`["LR2","LR3"],`

</td>
</tr>
</table>

> ### Note:  
> The use of scope-granting features establish a strong dependency between the involved applications and should be avoided wherever possible. Instead of using the granting functionality, try to see if the features provided by the XSUAA broker plan supports your application's authorization needs in a better way.



### Granting Authorization Scopes to other Applications

If two applications are bound to the User Account and Authentication \(UAA\) service, an authorization scope defined in one application can be granted to the second application on request. The application requesting the scope authority must specify this acceptance \(of externally defined scopes\) in the `"authorities"` section of its own security descriptor, and the application granting the scope authority must flag the specified scope as “grantable” in its own security descriptor, as illustrated in the following example:

> ### Sample Code:  
> Defining Local Scopes in the Security Descriptor
> 
> ```json
> "scopes": [ 
>     { 
>      "name" : "$XSAPPNAME.Display", 
>      "description" : "display" }, 
>     { 
>      "name" : "$XSAPPNAME.Edit", 
>      "description" : "edit" }, 
>     { 
>      "name" : "$XSAPPNAME.Delete", 
>      "description" : "delete"  },
>     { 
>      "name" : "$XSAPPNAME.ForeignCall", 
>      "description" : "Enable calls into scope-granting app",
>      "granted-apps": [*],
>      "grant-as-authority-to-apps" : ["RequestingApp"]
>     }
> ], 
> 
> ```



### Naming Conventions

Bear in mind the following restrictions regarding the length and content of a scope name:

-   The following characters can be used in a scope name: “aA”-“zZ”, “0”-“9”, “-” \(dash\), “\_” \(underscore\), “/” \(forward slash\), “\\” \(backslash\), “:” \(colon\), and the “.” \(dot\)

-   Scope names cannot start with a leading dot “.” \(for example, `.myScopeName1`\)

-   The maximum length of a scope name, including the fully qualified application name, is 193 characters.


> ### Restriction:  
> Some scope names are already in use; these names are specified in a default denylist.

It is not permitted to use any of the following names in the `scopes` property:

-   "zones.read", "zones.write"

-   "clients.admin", "clients.write", "clients.secret"

-   "scim.write", "scim.read", "scim.create", "scim.userids", "scim.zones"

-   "password.write"

-   "oauth.approval", "oauth.login"

-   "approvals.me"

-   "groups.update"

-   "uaa.resource", "uaa.admin", "uaa.none"




<a name="loio6d3ed64092f748cbac691abc5fe52985__section_pv5_5qr_xs"/>

## attributes

In the application-security file \(`xs-security.json`\), the `attributes` property enables you to define an array listing one or more attributes that are applied to the role templates also defined in the `xs-security.json` file. You can define multiple `attributes`.

> ### Sample Code:  
> Defining Attributes in the Application's Security Descriptor
> 
> ```json
> "attributes" : [ 
>      { 
>       "name" : "Country", 
>       "description" : "Country", 
>       "valueType" : "string" }, 
>      {
>       "name" : "CostCenter", 
>       "description" : "Cost Center ID", 
>       "valueType" : "string" } 
> ], 
> 
> ```

The `"attributes"` property is only relevant for user scenarios. Each element of the attributes array defines an individual, named, attribute, which can be referenced by one or more role-templates. For this reason, if the user in this scenario has been assigned the corresponding roles, the defined attributes are added to the JSON Web Token and used to enable instance-based authorization checks for access to the SAP HANA database. The value of the attributes is assigned in the administrator's SAP HANA or SAP Cloud Cockpit, either by defining a static value or by referencing an attribute of the SAML assertion that is issued by the configured identity provider during authentication.

The `attributes` key can take the following parameters and values:

**Parameters and Values for Authorization-Scope "attributes"**


<table>
<tr>
<th valign="top">

Key

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

`name` 

</td>
<td valign="top">

The name of the attribute with a value to apply when building the role template

</td>
<td valign="top">

`Country`

`Costcenter`

</td>
</tr>
<tr>
<td valign="top">

`description` 

</td>
<td valign="top">

A short summary of the attribute defined

</td>
<td valign="top">

`Country`

`Cost Center ID`

</td>
</tr>
<tr>
<td valign="top">

`valueType` 

</td>
<td valign="top">

The type of value expected for the defined attribute; possible values are: “`string`”, “`int`” \(integer\), or “`date`” 

</td>
<td valign="top">

`int` 

</td>
</tr>
</table>

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of attribute names in the `xs-security.json` file:

-   The following characters can be used to declare an attribute name in the `xs-security.json` file: “aA”-“zZ”, “0”-“9”, “\_” \(underscore\)

-   The maximum length of a security attribute name is 64 characters.




<a name="loio6d3ed64092f748cbac691abc5fe52985__section_atm_5qr_xs"/>

## role-templates

In the application-security file \(`xs-security.json`\), the `role-templates` property enables you to define an array listing one or more roles \(with corresponding scopes and any required attributes\), which are required to access a particular application module. You can define multiple `role-templates`, each with its own scopes and attributes.

> ### Restriction:  
> It is not permitted to use the property `role-templates` in combination with the XS UAA `broker` “clone” service plan. For more information see *Service Plans and Resources* in *Related Information*.

> ### Sample Code:  
> Defining Role Templates in the Application Security Descriptor
> 
> ```json
> "role-templates": [ 
>      { 
>       "name"                : "Editor", 
>       "description"         : "View, edit, delete books", 
>       "scope-references"    : [ 
>                               "$XSAPPNAME.Edit", "$XSAPPNAME.Delete"  
>                               ], 
>       "attribute-references": [ 
>                               "Country", "CostCenter" 
>                               ]  
>      },
> ]
> 
> ```

A role template must be instantiated. This is especially true with regards to any attributes defined in the role template and the concrete attribute values, which are subject to customization and, as a result, cannot be provided automatically. Role templates that only contain “local” scopes can be instantiated without user interaction. The same is also true for “foreign” scopes where the scope **owner** has declared consent in a kind of allow list \(for example, either for “public” use or for known “friends”\).

> ### Note:  
> The resulting \(application-specific\) role instances need to be assigned to the appropriate user groups.

**Role-Template Parameters**


<table>
<tr>
<th valign="top">

Key

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

`name` 

</td>
<td valign="top">

The name of the role to build from the role template

</td>
<td valign="top">

<code>“Viewer”</code> 

</td>
</tr>
<tr>
<td valign="top">

`description` 

</td>
<td valign="top">

A short summary of the role to build

</td>
<td valign="top">

<code>“View all books”</code> 

</td>
</tr>
<tr>
<td valign="top">

`scope-references` 

</td>
<td valign="top">

The security \(authorization\) **scope** to apply to the application-related role

</td>
<td valign="top">

<code>“$XSAPPNAME.Display”</code> 

</td>
</tr>
<tr>
<td valign="top">

`attribute-references` 

</td>
<td valign="top">

One or more attributes to apply to the built role

</td>
<td valign="top">

<code>[“Country”, “CostCenter”]</code> 

</td>
</tr>
</table>

**Naming Conventions**

Bear in mind the following restrictions regarding the length and content of role-template names in the `xs-security.json` file:

-   The following characters can be used to declare the name of a role-template in the `xs-security.json` file: “aA”-“zZ”, “0”-“9”, “\_” \(underscore\)

-   The maximum length of a role-template name is 64 characters.




<a name="loio6d3ed64092f748cbac691abc5fe52985__section_r5h_k14_qcb"/>

## foreign-scope-references

The element `"foreign-scope-references"` defines whether an application accepts authorization scopes that where granted to it by another Cloud Foundry application. Only those scopes that are listed as `"foreign-scope-references"` will be accepted by an application; the accepted scopes are then added to the local application's own OAuth client. If the value `$ACCEPT_GRANTED_SCOPES` is used, the local application will accept all scopes that are granted to it by other applications.

> ### Note:  
> It is not permitted to use the property `"foreign-scope-references"` in combination with the XS UAA `broker` “clone” service plan. For more information see *Service Plans and Resources* in *Related Information*.

The element `"foreign-scope-references"` is only relevant for a user scenario where the roles are not defined in the application's own service instance. For example, an administrator application integrates different application components, each of which has its own `xs-security.json` security descriptor. The administrator application uses the values defined in `"foreign-scope-references"` in the application's security descriptor to request the specified scopes, while the roles are defined by the components.

The following code illustrates a simple example of the `"foreign-scope-references"` property as defined in an application's security descriptor:

> ### Sample Code:  
> ```json
> "foreign-scope-references": ["$ACCEPT_GRANTED_SCOPES"] 
> ```
> 
> ```json
> "foreign-scope-references": ["$XSAPPNAME(application,otherApp).scope1"] 
> ```

The `“foreign-scope-references”` property specifies a list of scopes, with the following rules and restrictions:

-   It is highly recommended to prefix the scope value with the `$XSAPPNAME` function to reference the application Id inside the scope value, as illustrated in the example above.
-   References to a scope of the local Cloud Foundry application are not permitted
-   `$ACCEPT_GRANTED_SCOPES` is an allowed value with a special meaning.

    If the value`$ACCEPT_GRANTED_SCOPES` is used, the local application where it is specified accepts **all** scopes that are granted to it by other \(foreign\) applications. Only those scopes listed in `"foreign-scope-references"` are accepted by the local application and added to the local application's OAuth client.


> ### Note:  
> The use of scope-granting features establish a strong dependency between the involved applications and should be avoided wherever possible. Instead of using the granting functionality, see if the features provided by the XSUAA broker plan supports your application's authorization needs in a better way.



<a name="loio6d3ed64092f748cbac691abc5fe52985__section_d1m_1nq_zy"/>

## authorities

To enable one \(requesting\) application to accept and use the authorization scopes granted by another application, each application must be bound to its own instance of the XS UAA service; this is required to ensure that the applications are registered as OAuth 2.0 clients at the UAA. You must also add an <code>“authorities”</code> section to the security descriptor file of the application that is requesting an authorization scope. In the <code>“authorities”</code> section of the requesting application's security descriptor, you can either specify that **all** scope authorities configured as grantable in the granting application should be accepted by the application requesting the scopes, or alternatively, only individual, named, scope authorities:

-   Request and accept **all** authorities flagged as "grantable" in the granting application's security descriptor

    > ### Sample Code:  
    > Specifying Scope Authorities in the Requesting Application's Security Descriptor
    > 
    > ```json
    > "authorities":["$ACCEPT_GRANTED_AUTHORITIES"]
    > ```

-   Request and accept only the **specified** scope authority that is flagged as grantable in the specified granting application's security descriptor:

    > ### Sample Code:  
    > Specifying Scope Authorities in the Requesting Application's Security Descriptor
    > 
    > ```json
    > "authorities":["<GrantingApp>.ForeignCall", "<GrantingApp2>.ForeignCall",]
    > ```


Since both the requesting application and the granting application are bound to UAA services using the information specified in the respective application's security descriptor, the requesting application can accept and use the specified authority from the granting application. The requesting application is now authorized to access the granting application and perform some tasks.

> ### Note:  
> The granted authority always includes the prefixed name of the application that granted it. This information tells the requesting application which granting application has granted which set of authorities.

The scope authorities listed in the requesting application's security descriptor must be specified as "grantable" in the granting application's security descriptor.

> ### Tip:  
> To flag a scope authority as "grantable", add the `"grant-as-authority-to-apps"` property to the respective scope in the granting application's security descriptor.



<a name="loio6d3ed64092f748cbac691abc5fe52985__section_mxn_fcz_2bb"/>

## oauth2-configuration

Use the custom `oauth2-configuration` property to define custom values for the OAuth 2.0 clients, such as the amount of time for which an OAuth token is valid or the Universal Resource Indicators \(URI\) to which you want to redirect application requests. The `xsuaa` service broker registers and uses the values defined in `oauth-configuration` to configure the OAuth 2.0 clients.

The following code illustrates a simple example of the OAuth 2.0 client configuration:

> ### Sample Code:  
> ```json
> "oauth2-configuration": {
>    "token-validity": 900, 
>    "refresh-token-validity": 1800, 
>    "redirect-uris": [	
>                      "https://<host_name1>",
>                      "https://<host_name2>"], 
>    "autoapprove": "false", 
>    "system-attributes": ["groups", "rolecollections"], 
>    "allowedproviders": ["useridp1", "useridp2"] 
> }
> ```

The following configuration keys are available:

**oauth2-configuration Parameters**


<table>
<tr>
<th valign="top">

Key

</th>
<th valign="top">

Mandatory

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

`token-validity` 

</td>
<td valign="top">

No

</td>
<td valign="top">

The amount of time \(in seconds\) for which the application's JSON Web Token \(JWT\) is valid. If no value is defined, the default value of 12 hours \(43,200 seconds\) is used.

</td>
<td valign="top">

`900` \(15 minutes\)

</td>
</tr>
<tr>
<td valign="top">

`refresh-token-validity` 

</td>
<td valign="top">

No

</td>
<td valign="top">

The amount of time \(in seconds\) for which the application's refresh JSON Web Token \(JWT\) is valid. If no value is defined, the default value \(30 days\) is used.

</td>
<td valign="top">

`1800` \(30 minutes\)

</td>
</tr>
<tr>
<td valign="top">

`redirect-uris` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Array defining a allow list of the allowed redirect URIs. This list overwrites the default URIs provided by the User Account and Authentication service \(UAA\).

Default: localhost, `[xs | cf ] apps domain`

</td>
<td valign="top">

<code>["https://<i class="varname">&lt;host_name1&gt;</i>","https://<i class="varname">&lt;host_name2&gt;</i>"]</code> 

</td>
</tr>
<tr>
<td valign="top">

`autoapprove` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Determines whether the user has to approve the requested scopes \(“false”\) or if the scopes are assigned without approval \(“true”\) during the token retrieval. Allowed values are “true” \(default\) and “false” 

</td>
<td valign="top">

<code>“false”</code> 

</td>
</tr>
<tr>
<td valign="top">

`system-attributes` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Array of system attributes to add to the JSON Web Token. Allowed values are: “groups”, “rolecollections”

> ### Restriction:  
> Only for use in Cloud-Foundry environments.



</td>
<td valign="top">

`["groups", "rolecollections"]` 

</td>
</tr>
<tr>
<td valign="top">

`allowedproviders` 

</td>
<td valign="top">

No

</td>
<td valign="top">

Array listing the allowed identity providers \(IdP\) to use for authentication purposed. By default **all** providers are allowed.

</td>
<td valign="top">

`["useridp1", "useridp2"]` 

</td>
</tr>
</table>

**Related Information**  


[Create the Security Descriptor for a Multitarget Application](create-the-security-descriptor-for-a-multitarget-application-df31a08.md "The security descriptor defines details of an application's security-related dependencies.")

[Application Router Configuration Syntax](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[Service Plans and Resources](../070-HANA-Cloud-DB-Dev-App-Services/service-plans-and-resources-0393ce3.md "A service plan is a particular type of service (for example, a database configuration) that is available for use.")

[User Account and Authentication Services](../070-HANA-Cloud-DB-Dev-App-Services/user-account-and-authentication-services-c6f36d5.md "The SAP HANA XS User Account and Authentication service (UAA) is the central infrastructure component for user authentication and trust manageement.")

