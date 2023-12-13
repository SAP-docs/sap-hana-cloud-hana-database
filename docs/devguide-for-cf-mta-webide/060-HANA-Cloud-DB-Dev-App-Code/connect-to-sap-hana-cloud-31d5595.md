<!-- loio31d5595ee67c484290621fdc6d6a197f -->

# Connect to SAP HANA Cloud

Connect an application to SAP HANA Cloud



<a name="loio31d5595ee67c484290621fdc6d6a197f__prereq_ogg_tlf_21b"/>

## Prerequisites

-   You have configured you command-line interface to use the public NPM registry. For more information, see *Related Links* below.

-   The tutorials in this section require tools provided with the CF command-line client, but you can also use graphical developer tools, for example, *SAP Web IDE Full-Stack*.




## Context

SAP provides the package \(`@sap/hdbext`\) which Node.js applications can use to connect to SAP HANA Cloud. If you want to use it, you must add it to your list of application dependencies.

> ### Tip:  
> To ensure that both SSL and trust certificates are set up automatically, it is recommended to use [@sap/hdbext](https://www.npmjs.com/package/@sap/hdbext) to connect to SAP HANA rather than use @sap/hana-client.



## Procedure

1.  Navigate to the <code><i class="varname">&lt;myapp&gt;</i></code> directory.

2.  Execute `npm install @sap/hdbext@^5.0.0 --save` to install the `@sap/hdbext` module and add it as a dependency in the `package.json` file.

    After the installation of the package is complete, the dependencies section in the `package.json` file should have the following content:

    ```
      "dependencies": {
        "express": "4.18.2",
        "@sap/xsenv": "^4.2.0"
        "@sap/hdbext": "^8.0.2"
      },
    ```

3.  Update the `start.js` file and replace the following content:

    ```
    app.get('/', function (req, res) {
      res.send('Using HANA ' + services.hana.host + ':' + services.hana.port);
    });
    ```

    with the following content:

    ```
    var hdbext = require('@sap/hdbext');
    
    app.use('/', hdbext.middleware(services.hana));
    
    
    app.get('/', function (req, res, next) {
    	req.db.exec('SELECT CURRENT_UTCTIMESTAMP FROM DUMMY', function (err, rows) {
    	if (err) { return next(err); }
    	res.send('Current HANA time (UTC): ' + rows[0].CURRENT_UTCTIMESTAMP);
      });
    });
    ```

    `hdbext.middleware` will connect to SAP HANA Cloud automatically on each access to the specified path \( */*\) in this case. Afterwards the connection is available in `req.db`. This is the client object of the [hdb](https://www.npmjs.com/package/hdb) driver. The connection is closed automatically at the end of the request.

4.  Update the application in Cloud Foundry.

    Execute the following command in the `node-tutorial` directory.

    ```
    cf push
    ```

5.  Open a browser window with the <code><i class="varname">&lt;myapp&gt;</i></code> application URL.

    You should see the current SAP HANA Cloud time.


**Related Information**  


[Standard SAP Node.js Packages](standard-sap-node-js-packages-5451327.md "A collection of Node.js packages developed by SAP is provided to help you develop Node.js applications for Cloud Foundry and SAP HANA Cloud.")

[The NPM Registry](the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

[https://www.npmjs.com/package/@sap/hdbext](https://www.npmjs.com/package/@sap/hdbext)

