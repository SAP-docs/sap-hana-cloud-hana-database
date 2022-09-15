<!-- loioc8c578ec58ce459d9181c00d157dfc73 -->

# Set up Generic Authorization for a Multitarget Application

Define an authorization model for your multitarget application and configure generic authorization for any application end point \(route path\).



<a name="loioc8c578ec58ce459d9181c00d157dfc73__prereq_t1f_3cx_3bb"/>

## Prerequisites

The following files are required:

-   `xs-app.json`

    Application descriptor \(application-router configuration file\)

-   `xs-security.json`

    Security descriptor \(security configuration file\)




## Context

To enable user access to an application, it is necessary to declare a "start authorization" for the application's security descriptor \(`xs-security.json`\) and reference the start authorization from the application router's \(`approuter`\) configuration file \(`xs-app.json`\). This enables the multitarget application's application router to perform a generic authorization check on the declared start authorization. The authorization itself is based not only on scopes, which determine the type and extent of access allowed \(for example, view, edit, manage\), but also on roles, which are defined in templates. For example, the role template defines the authorization scopes that are associated with a given role. Users can then be assigned to a role that corresponds to the type of access authorization that they need.

To set up authorization for your multitarget application, perform the following steps:



## Procedure

1.  Define authorization scopes and role templates.

    Define the role templates that specify the authorization scopes for each role. Users can then be assigned to one or more roles which ensure that the specified scopes are assigned as authorization keys.

    To declare the role templates, modify the security descriptor file `xs-security.json` by including the following authorization model for your application:

    > ### Sample Code:  
    > ```
    > {
    >   "xsappname"     : "myApp-tenantID", 
    >   "description"   : "Enable myApp for multi tenants", 
    >   "tenant-mode"   : "shared", 
    >   "scopes"        : [ 
    >                      { 
    >                        "name"             : "$XSAPPNAME.Display", 
    >                        "description"      : "Display Info." 
    >                      }, 
    >                      {
    >                        "name"             : "$XSAPPNAME.Update", 
    >                        "description"      : "Update Info."
    >                      } 
    >                     ],
    >   "role-templates": [  
    >                      {  
    >                        "name"             : "Viewer",  
    >                        "description"      : "View Info.",  
    >                        "scope-references" : [ 
    >                                              "$XSAPPNAME.Display"
    >                                             ] 
    >                      }, 
    >                      { 
    >                        "name"             : "Editor",  
    >                        "description"      : "Maintain Info",  
    >                        "scope-references" : [ "$XSAPPNAME.Display", 
    >                                               "$XSAPPNAME.Update"  
    >                                             ]
    >                      }
    >   ] 
    > }
    > ```

    > ### Note:  
    > For multi-tenant scenarios, the value of `"xsappname"` must be unique within the whole Cloud Foundry Organization, which is why the tenant ID here ensures that the value for `"xsappname"` refers to this unique instance. The shared `"tenant-mode"` makes it possible for the XS UAA service instance to trust other tenants in addition to the one specified here.

2.  Configure start conditions for application routes and end points.

    To define the start condition, we need to assign the required scope definition to the application's route\(s\). For example, in the approuter configuration file \(`xs-app.json`\), add an entry \(`"scope:"`\) that references the authorization scope \(`"Display"`\) previously defined in the application's security descriptor `xs-security.json`, as illustrated in the following example:

    > ### Sample Code:  
    > ```
    > {
    >   "welcomeFile": "index.html", 
    >   "routes": [{ 
    >      "source": "^/foo/api/", 
    >      "target": "/api/",
    >      "destination": "foo-destination", 
    >      "scope": "$XSAPPNAME.Display" 
    >      }, 
    >      {  
    >      "source": "^/foo",  
    >      "target": "/",  
    >      "destination": "foo-destination"  
    >      }] 
    > }
    > ```

3.  Inform the XS User Account and Authentication \(UAA\) service about the security updates.

    The XS UAA service needs to know about any changes to the application's authorization model, which is described in the security descriptor \(`xs-security.json`\).

    ```
    cf update-service <myServiceInstance> -c <path>/xs-security.json
    ```

4.  Bind your application to the XS UAA service.

    Add a service entry to the application's deployment manifest `manifest.yml`.

    > ### Note:  
    > The `manifest.yml` file is formatted according to YAML rules, which requires strict and consistent adherence to indents.

    > ### Sample Code:  
    > ```
    > - name: myApp 
    >   ...
    >   services: 
    >     - ...
    >     - uaa-myApp
    > ```

5.  Deploy the application.

    ```
    cf push
    ```

6.  Maintain the roles and authorizations defined in your application's security model.

    At this point, that, the XSUAA is aware of the role-templates defined in the application's security descriptor \(`xs-security.json`\). However, since the required scopes and roles are not yet assigned to a user, the user does not yet have the permissions required to access the advertised application end points.

    In this step, you need to create a new role based on the role-template specified in the application's `xs-security.json` file; add the role to a **role collection** \(either existing or newly created\); and assign a user to the role collection. Logging into the application as the user with the assigned role collection ensures that the configured authorizations are assigned to the logged in user.

    > ### Tip:  
    > You can set up roles and role collections, and assign users to role collections using the SAP BTP cockpit. Access to these tools requires administrator privileges.


**Related Information**  


[Application Security Descriptor Configuration Syntax](application-security-descriptor-configuration-syntax-6d3ed64.md "The syntax required to set the properties and values defined in the xs-security.json application-security description file.")

[Application Router Configuration Syntax](../090-HANA-Cloud-DB-Dev-MTA-Routes/application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[Set up Authorization for your JavaScript Multitarget Application](../060-HANA-Cloud-DB-Dev-App-Code/set-up-authorization-for-your-javascript-multitarget-application-7eedc1d.md "Set up user authorization for your JavaScript multitarget application in Cloud Foundry on SAP Business Technology Platform.")

