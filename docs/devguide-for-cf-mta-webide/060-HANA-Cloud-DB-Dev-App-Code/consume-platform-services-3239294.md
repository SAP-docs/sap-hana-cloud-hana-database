<!-- loio32392948cb1844b2a6ed22ad641d4461 -->

# Consume Platform Services

Cloud Foundry provides services, which can be used by applications.



<a name="loio32392948cb1844b2a6ed22ad641d4461__prereq_ogg_tlf_21b"/>

## Prerequisites

-   You have configured you command-line interface to use the public NPM registry. For more information, see *Related Links* below.

-   The tutorials in this section require tools provided with the CF command-line client, but you can also use graphical developer tools, for example, *SAP Web IDE Full-Stack*.




## Context

SAP provides a convenient package \(`@sap/xsenv`\) for Node.js applications, which can be used to read bound services. To use the `@sap/xsenv` package, you have to add it to your application's dependencies, which are specified in a corresponding `package.json` file.



<a name="loio32392948cb1844b2a6ed22ad641d4461__steps_pjj_r4j_qv"/>

## Procedure

1.  Navigate to the `myapp` directory.

2.  Execute `npm install @sap/xsenv@^1.2.9 --save` to install the `@sap/xsenv` module and add it as a dependency in the `package.json` file.

    After the installation of the package is complete, the dependencies section in the `package.json` file should have the following content:

    ```
      "dependencies": {
        "express": "4.18.2",
        "@sap/xsenv": "^4.2.0"
      },
    ```

3.  Update the `start.js` file with the content shown in the following example:

    ```
    var express = require('express');
    var app = express();
    
    var xsenv = require('@sap/xsenv');
    var services = xsenv.getServices({ hana:'myhana' });
    
    app.get('/', function (req, res) {
      res.send('Using HANA ' + services.hana.host + ':' + services.hana.port);
    });
    
    var port = process.env.PORT || 3000;
    app.listen(port, function () {
      console.log('myapp listening on port ' + port);
    });
    ```

4.  Create a service instance named `myhana` .

    The new service instance must have the service type “`hana`” and the service plan “`hdi-shared`”, as illustrated in the following command:

    ```
    cf create-service hana hdi-shared myhana
    ```

5.  Replace the content of the `manifest.yml` file in the `node-tutorial` directory with the following:

    ```
    ---
    applications:
    - name: myapp
      path: myapp
      services:
        - myhana
    ```

    The Cloud Foundry run time binds the `myhana` service instance to the `myapp` application during deployment.

6.  Update the application on Cloud Foundry.

    Install the modified version of the application to Cloud Foundry run-time environment by running the `cf push` command in the `node-tutorial` directory, as follows:

    ```
    cf push
    ```

7.  Display the URL for accessing the updated application after deployment.

    ```
    cf app myapp --urls
    ```

8.  Open a browser window and paste the displayed URL in to start the application.

    You should see a message similar to: Using SAP HANA *<hana host\>*:*<hana port\>*.


**Related Information**  


[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

