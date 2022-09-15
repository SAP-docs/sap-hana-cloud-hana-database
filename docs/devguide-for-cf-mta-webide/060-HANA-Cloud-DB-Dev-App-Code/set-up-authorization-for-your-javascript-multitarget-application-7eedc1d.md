<!-- loio7eedc1dc3f254cca8236924a728c8894 -->

# Set up Authorization for your JavaScript Multitarget Application

Set up user authorization for your JavaScript multitarget application in Cloud Foundry on SAP Business Technology Platform.



<a name="loio7eedc1dc3f254cca8236924a728c8894__prereq_ogg_tlf_21b"/>

## Prerequisites

-   You have configured you command-line interface to use the public NPM registry. For more information, see *Related Links* below.

-   The tutorials in this section require tools provided with the CF command-line client, but you can also use graphical developer tools, for example, *SAP Web IDE Full-Stack*.




## Context

The Web application can also handle user authorization, for example, with defined scopes and role templates. Scopes and role templates are defined in the application security descriptor \(`xs-security.json`\), and the application router's descriptor \(`xs-app.json`\) can contain configurations with authorization restrictions, for example, the specific scopes a user requires to access a resource. For information about setting up authorization scopes, role assignment, and role collections, see *Related Links* below.

It is a general recommendation to implement authorization in the different microservices as well.



<a name="loio7eedc1dc3f254cca8236924a728c8894__steps_myj_j4j_qv"/>

## Procedure

1.  Add an authorization check to your application.

    To add an authorization check in the `myapp` application, you need to modify the application's startup file `start.js` file; replace the express handler for `GET` requests to path “/” with the following code:

    ```
    app.get('/', function (req, res, next) {
      var isAuthorized = req.authInfo.checkScope('uaa.user');
      if (isAuthorized) {
        res.send('Application user: ' + req.user.id);
      } else {
        res.status(403).send('Forbidden');
      }
    });
    ```

2.  Deploy the modified application.

    You can update the `myapp` application by redeploying, for example, by executing the command `cf push myapp` in the `node-tutorial` directory.

    In this example the `myapp` application checks whether the current user has the authorization scope `uaa.user`. Since this is a default scope, the authorization check is successful.

    > ### Tip:  
    > It is possible to create a UAA service instance with scopes that are specific to your application.


**Related Information**  


[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[Set up Application Security](../100-HANA-Cloud-DB-Dev-Security/set-up-application-security-b823639.md "Help ensure a multitarget application is protected from Web-based attacks.")

[Maintaining Multitarget Application Routes and Destinations](../090-HANA-Cloud-DB-Dev-MTA-Routes/maintaining-multitarget-application-routes-and-destinations-0117b71.md "Define application routes and destinations.")

