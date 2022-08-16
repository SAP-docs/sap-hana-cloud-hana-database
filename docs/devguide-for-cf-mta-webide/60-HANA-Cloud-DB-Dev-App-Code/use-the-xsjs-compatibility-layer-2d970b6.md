<!-- loio2d970b65462c4ff3bc674f2ddbd5da9f -->

# Use the XSJS Compatibility Layer

The XSJS compatibility layer is a framework that allows you to run XS classic JavaScript applications in the Cloud Foundry run-time environment on SAP Business Technology Platform.



<a name="loio2d970b65462c4ff3bc674f2ddbd5da9f__steps_ky5_vrj_qv"/>

## Procedure

1.  Create a new directory inside `node-tutorial` named `xsjs`.

2.  Create `package.json` file in the `xsjs` directory containing the following code.

    ```
    {
      "name": "xsjs",
      "version": "6.0.1",
      "scripts": {
        "start": "node start.js"
      }
    }
    ```

3.  Execute `npm install @sap/xsenv@^1.2.9 --save` to install the `@sap/xsenv` module and add it as a dependency in the `package.json` file.

4.  Execute `npm install @sap/xsjs@^3.3.1 --save` to install the `@sap/xsjs` module and add it as a dependency in the `package.json` file.

5.  Create `start.js` file in the `xsjs` directory containing the following.

    ```
    var xsjs = require('@sap/xsjs');
    var xsenv = require('@sap/xsenv');
    var port = process.env.PORT || 3000;
    
    var options = xsenv.getServices({ hana:{tag:'hana'}, uaa:{tag:'xsuaa'} });
    
    xsjs(options).listen(port);
    console.log('XSJS application listening on port %d', port);
    ```

    The XSJS compatibility layer takes an object containing configurations. In this example SAP HANA and UAA configurations are provided.

6.  Create a new directory named `lib` inside the directory `xsjs`.

7.  Create a new file named `get-time.xsjs` inside the `lib` directory and add the following content to it.

    ```
    var conn = $.hdb.getConnection();
    var resultSet = conn.executeQuery('SELECT CURRENT_UTCTIMESTAMP FROM DUMMY');
    $.response.setBody('Current HANA time (UTC): ' + resultSet[0].CURRENT_UTCTIMESTAMP);
    conn.close();
    ```

8.  Navigate to the `node-tutorial` directory and add the following content at the end of the `manifest.yml` file.

    ```
    - name: xsjs
      path: xsjs
      services:
        - myhana
        - myuaa
    ```

9.  Deploy the XS JavaScript application with the following command executed from the `node-tutorial` directory:

    `cf push xsjs`

10. Get the URL of the `xsjs` application by running the `cf app xsjs --urls` command.

    > ### Note:  
    > Authentication is enabled by default in the compatibility layer; you are not able to directly access the `xsjs` application.

11. Update the configuration for the Web application in the `manifest.yml` file in the `node-tutorial` directory:

    ```
    - name: web
      path: web
      env:
        destinations: >
          [
            {
              "name":"myapp",
              "url":"<myapp url>",
              "forwardAuthToken": true
            },
            {
              "name":"xsjs",
              "url":"<xsjs url>",
              "forwardAuthToken": true
            }
          ]
      services:
        - myuaa
    ```

    Set the `url` property of the `xsjs` destination to the URL of the `xsjs` application.

    > ### Note:  
    > The application-router based application can forward requests to two microservices: the `myapp` application and the `xsjs` application. This should be configured in the application descriptor \(`xs-app.json`\) located in the `web` directory.

12. Navigate to the `web` directory and replace the content of the application descriptor \(`xs-app.json`\) with the following content:

    ```
    {
      "routes": [
        {
          "source": "^/myapp/(.*)$",
          "target": "$1",
          "destination": "myapp"
        },
        {
          "source": "^/xsjs/(.*)$",
          "target": "$1",
          "destination": "xsjs"
        }
      ]
    }
    ```

13. Add a link to the `xsjs` application in `web/resources/index.html`, which should then look like the following example:

    ```
    <html>
    <head>
        <title>JavaScript Tutorial</title>
    </head>
    <body>
      <h1>JavaScript Tutorial</h1>
      <a href="/myapp/">myapp</a>
      <p>
      <a href="/xsjs/get-time.xsjs">xsjs</a>
    </body>
    </html>
    ```

14. Navigate to the `node-tutorial` directory and execute the command `cf push web` to update the `web` application.

15. Display the URL required for access to the `web` application by executing the command `cf apps` command and use the URL to start the application in a Web browser.

    > ### Note:  
    > You may need to log in again, for example, if your session has expired.

16. Choose the link `xsjs` to see a page displaying the current SAP HANA Cloud time.


**Related Information**  


[Tutorial: Setting up your JavaScript Application in Cloud Foundry](tutorial-setting-up-your-javascript-application-in-cloud-foundry-30d629e.md "Tutorials that show you how to set up JavaScript applications for Cloud Foundry .")

[The Cloud Foundry JavaScript Run Time](the-cloud-foundry-javascript-run-time-18c0192.md "Cloud Foundry on SAP Business Technology Platform provides a JavaScript run time environment to which you can deploy your Node.js and JavaScript applications.")

