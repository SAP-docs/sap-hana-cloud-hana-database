<!-- loioea92108fb3dc4d93a574a67b3bcb3c0d -->

# Trouble Shoot JavaScript Multitarget Applications

Investigate problems that occur during deployment and execution of a multitarget JavaScript application.



## Enhancing the logs

SAP provides several possibilities to enhance the logs for Node.js applications. SAP-specific packages usually use the `@sap/logging` module. With the `@sap/logging` module, you can set the logging and tracing severity level to the most verbose level in the following ways:

-   Set the environment variable `XS_APP_LOG_LEVEL` to `debug`.

    > ### Note:  
    > You must restart the application to reset the logging level.

-   Use the `cf set-logging-level` command, as illustrated in the following example:

    `cf set-logging-level <application-name> '*' debug`

    > ### Note:  
    > You do not need to restart the application to reset the logging level.


Other Node.js packages \(or dependencies of SAP-specific packages\) might use different logging mechanisms. For example, many applications use the `debug` package. Additional traces can also be enabled by setting the *<DEBUG\>* environment variable; setting *<DEBUG\>* to \* will write a large amount of information to the logs and traces very quickly, which could cause problems with disk space.

Internal Node.js traces can be enabled with the `NODE_DEBUG` environment variable.

> ### Caution:  
> Enabling some of these options may write sensitive data to logs and traces in an insecure form.

**Related Information**  


[The Cloud Foundry JavaScript Run Time](the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

[Consume SAP Node.js Packages](consume-sap-node-js-packages-ddcff14.md "A selection of SAP-specific and ready-to-use Node.js packages is available on the public NPM registry.")

[Tutorial: Setting up your JavaScript Application in Cloud Foundry](tutorial-setting-up-your-javascript-application-in-cloud-foundry-30d629e.md "Tutorials that show you how to set up JavaScript applications for Cloud Foundry .")

