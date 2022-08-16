<!-- loio7c242c7b0af243e5b5ebe2fb44ff4f6c -->

# Set up Logging and Tracing for your JavaScript Multitarget Application

Write log and trace files for your JavaScript application in Cloud Foundry.



<a name="loio7c242c7b0af243e5b5ebe2fb44ff4f6c__prereq_ogg_tlf_21b"/>

## Prerequisites

-   You have configured you command-line interface to use the public NPM registry. For more information, see *Related Links* below.

-   The tutorials in this section require tools provided with the CF command-line client, but you can also use graphical developer tools, for example, *SAP Web IDE Full-Stack*.




## Context

SAP provides a Node.js package for logging and tracing \(`@sap/logging`\).

> ### Note:  
> Logs are for the administrator of an application; trace files are for developers or support.

Events that need to be logged are related to how an application operates. For example, entries are created in logs and trace files if a user has been refused access to an application after too many failed log-in attempts, or the application cannot display results returned by a remote HTTP service because the remote server is down. The administrator of an application does not need to know how it is implemented; they should just be able to determine the state of the application itself.

Traces are mainly used when a problem has occurred and further investigation is necessary at the JavaScript code level.

To consume the `@sap/logging` library, execute the following steps:



<a name="loio7c242c7b0af243e5b5ebe2fb44ff4f6c__steps_d1r_xqj_qv"/>

## Procedure

1.  Change to the `myapp` directory.

2.  Execute `npm install @sap/logging --save` to install the `@sap/logging` module and add it as a dependency in the `package.json` file.

    ```
    "dependencies": {
      "express": "4.16.2",
      "@sap/xsenv": "1.2.9",
      "@sap/hdbext": "^4.7.0",
      "@sap/xssec": "^2.1.6",
      "passport": "^0.3.2",
      "@sap/logging": "^4.0.2"
    }
    ```

3.  Replace the content of the application startup file \(`start.js`\) with the following code:

    ```
    var express = require('express');
    var xsenv = require('@sap/xsenv');
    var passport = require('passport');
    var JWTStrategy = require('@sap/xssec').JWTStrategy;
    var logging = require('@sap/logging');
    var appContext = logging.createAppContext();
    
    var app = express();
    
    app.use(logging.middleware({ appContext: appContext }));
    
    passport.use(new JWTStrategy(xsenv.getServices({uaa:{tag:'xsuaa'}}).uaa));
    
    app.use(passport.initialize());
    app.use(passport.authenticate('JWT', { session: false }));
    
    app.get('/', function (req, res, next) {
      var logger = req.loggingContext.getLogger('/Application');
      var tracer = req.loggingContext.getTracer(__filename);
    
      var isAuthorized = req.authInfo.checkScope('example.scope');
      if (isAuthorized) {
        tracer.debug("Authorization success. User: " + req.user.id + ", Path: '/'.");
        res.send('Application user: ' + req.user.id);
      } else {
        logger.info("Authorization failed. User: " + req.user.id + ", Path: '/'.");
        res.status(403).send('Forbidden');
      }
    });
    
    var port = process.env.PORT || 3000;
    app.listen(port, function () {
      console.log('myapp listening on port ' + port);
    });
    ```

    > ### Note:  
    > To demonstrate what happens with a failed authorization, the used scope \(`example.scope`\) is not among the scopes the test user should possess.

4.  Update the `myapp` application by executing the command `cf push myapp` in the `node-tutorial` directory.

5.  Call the `web` application using the path `/myapp/`.

    A message is displayed in the Web browser saying you are not authorized.

6.  Check the logs of the `myapp` application.

    In a command shell, execute the command `cf logs myapp --recent`. The displayed output should contain an entry in the log format used by the `@sap/logging` library with the severity level “`info`” and a message similar to the following example:

    ```
    Authorization failed. User: <HANA-user>, Path: '/'.
    ```

    If you change the required user scope in the JavaScript code to one already assigned to the requesting user \(for example, “`uaa.user`”\) and update the application in the Cloud Foundry run-time, for example, using the `cf push myapp` command, then a trace entry with severity status `debug` is generated.

    > ### Tip:  
    > The `debug` level is not enabled by default; this entry is only generated if the `debug` level is enabled for the application.

7.  Enable `debug` tracing for the application.

    > ### Note:  
    > If you are using SAP Web IDE, you can use the `<XS_APP_LOG_LEVEL>` environment variable to set the logging level. In SAP Web IDE, the default application logging level is `ERROR`.

8.  Call the `web` application using the path */myapp/*.

    The result should contain the name of the requesting user.

9.  View the application trace files.

    In a command shell, execute the command `cf logs myapp --recent` to view the trace entries. The trace entries with severity `debug` should contain a message similar to the following example:

    ***Authorization success. User: *<HANA-user\>*, Path: '/'***


**Related Information**  


[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

