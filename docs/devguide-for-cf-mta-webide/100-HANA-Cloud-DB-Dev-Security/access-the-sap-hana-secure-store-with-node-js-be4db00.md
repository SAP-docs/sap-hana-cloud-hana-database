<!-- loiobe4db004d1ec4ce9b8dea7e367fbd404 -->

# Access the SAP HANA Secure Store with Node.js

Use a Node.js application to maintain entries in the SAP HANA Secure Store.



<a name="loiobe4db004d1ec4ce9b8dea7e367fbd404__prereq_yrs_ybb_fcb"/>

## Prerequisites

To maintain content in the SAP HANA Secure Store, bear in mind the following conditions:

-   The application must be bound to an instance of the `hana` service using the `securestore` service plan.

-   The resource type for the database connection specified in the multitarget application's deployment descriptor \(`mta.yaml` file\) must be `com.sap.xs.hana-securestore`.




<a name="loiobe4db004d1ec4ce9b8dea7e367fbd404__context_mqv_qbb_mgb"/>

## Context

In the context of the application run time, the SAP HANA Secure Store is used to maintain sensitive information such as user credentials. Access to the SAP HANA Secure Store is enabled by stored procedures which you can use to insert, retrieve, and delete entries in the Secure Store. Any application that is bound to an instance of the `hana` service with the service plan `securestore` has access to these stored procedures and can use them to maintain content stored in the Secure Store.

> ### Tip:  
> For more information about the parameters required when calling the Secure-Store procedures, see *Related Information* below.

The following examples show how to use Node.js applications to maintain entries programmatically in the SAP HANA Secure Store:



<a name="loiobe4db004d1ec4ce9b8dea7e367fbd404__steps_nqv_qbb_mgb"/>

## Procedure

1.  Insert encrypted values into the SAP HANA Secure Store.

    The following example shows how to use a Node.js application to insert encrypted entries into the SAP HANA Secure Store; the example uses `app.post()` to insert the entry and includes the content in the request body:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_INSERT \(Node.js Application\)
    > 
    > ```js
    > /*eslint no-console: 0, no-unused-vars: 0, no-shadow: 0, new-cap: 0*/
    > "use strict";
    > var express = require("express");
    > 
    > module.exports = () => {
    >      var app = express.Router();
    > 	
    >      var bodyParser = require("body-parser");
    >      app.use(bodyParser.raw({
    >              type: "text/plain"
    >      }));  //Process request Body and return a Buffer
    > 
    >      //Secure Store Insert
    >      app.post("/:key?", async(req, res) => { 
    >      	const hdbext = require("@sap/hdbext"); 
    >      	const key = req.params.key; 
    >      	let inputParams = ""; 
    >      	if (typeof key === "undefined" || key === null) { 
    >      	        res.type("text/plain").status(500).send("ERROR: No Secure Store Key Input Parameter Specified");
    >                   return; 
    >      	} else { 
    >      	        inputParams = { 
    >      	     	     KEY: key }; 
    >      	}
    >      	inputParams.STORE_NAME = "MY_SECURE_STORE";
    >      	inputParams.FOR_XS_APPLICATIONUSER = true;
    >      	inputParams.VALUE = req.body;
    >           const client = await getSecureStore();
    >      	//(client, Schema, Procedure, callback)
    >      	hdbext.loadProcedure(req.db, "SYS", "USER_SECURESTORE_INSERT", (err, sp) => {
    >      		if (err) {
    >      			res.type("text/plain").status(500).send(`ERROR: ${err.toString()}`);
    >      			return;
    >      		}
    >      		//(Input Parameters, callback(errors, Output Scalar Parameters, [Output Table Parameters])
    >      		sp(inputParams, (err, parameters, results) => {
    >      			if (err) {
    >      				res.type("text/plain").status(500).send(`ERROR: ${err.message.toString()}`);
    >      				return;
    >      			}
    >      			res.type("application/json").status(200).send(`Entry in secure store successfully created for key: ${key} and value: ${req.body.toString("utf8")} `);
    >      		});
    >      	});
    >      });
    >      //Secure Store Retrieve
    >      app.get("/:key?", (req, res) => {
    >      [...]
    >      });
    >      //Secure Store Delete
    >      app.delete("/:key?", (req, res) => {[...]
    >      });
    >      return app;
    > };
    > ```

    Bear in mind that, in the Node.js example above, the `KEY` parameter requires a `VALUE` of type `VARBINARY`, so any hard-coded values \(numbers, dates, strings\) in the `INSERT` call need to be converted, for example, using `TO_BINARY` on the database side or by using a JavaScript Buffer. In this case, we specify a body-parsing module earlier in the code which sets the body content used to fill the `VALUE` parameter to `raw` and ensures that no conversion is required.

2.  Retrieve encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Node.js application to retrieve encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_RETRIEVE \(Node.js Application\)
    > 
    > ```js
    > //Secure Store Retrieve
    > app.get("/:key?", async(req, res) => {
    >      const hdbext = require("@sap/hdbext"); 
    >      const key = req.params.key; 
    >      let inputParams = ""; 
    >      if (typeof key === "undefined" || key === null) { 
    >             res.type("text/plain").status(500).send("ERROR: No Secure Store Key Input Parameter Specified");
    >             return; 
    >      } else { 
    > 	        inputParams = { 
    >           	     KEY: key }; 
    > 	}
    > 	inputParams.STORE_NAME = "MY_SECURE_STORE";
    > 	inputParams.FOR_XS_APPLICATIONUSER = true;
    >      const client = await getSecureStore();
    > 	//(client, Schema, Procedure, callback)
    > 	hdbext.loadProcedure(req.db, "SYS", "USER_SECURESTORE_RETRIEVE", (err, sp) => {
    > 		if (err) {
    > 			res.type("text/plain").status(500).send(`ERROR: ${err.toString()}`);
    > 			return;
    > 		}
    > 		//(Input Parameters, callback(errors, Output Scalar Parameters, [Output Table Parameters])
    > 		sp(inputParams, (err, parameters, results) => {
    > 			if (err) {
    > 				res.type("text/plain").status(500).send(`ERROR: ${err.message.toString()}`);
    > 				return;
    > 			}
    > 			res.type("application/json").status(200).send(`Entry in secure store successfully retrieved for key: ${key} and value: ${results.VALUE.toString("utf8")} `);
    > 		});
    > 	});
    > });
    > ```

    Bear in mind that, in the Node.js example above, the `KEY` parameter returns a `VALUE` of data type `VARBINARY`, which if required can be converted to a string, for example, by using `TO_NVARCHAR` in the database or by using a JavaScript Buffer for the content of the request body.

3.  Delete encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Node.js application to remove entries from the Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_DELETE \(Node.js Application\)
    > 
    > ```js
    > //Secure Store Delete
    > app.delete("/:key?", async(req, res) => { 
    >      const hdbext = require("@sap/hdbext"); 
    >      const key = req.params.key; 
    >      let inputParams = ""; 
    >      if (typeof key === "undefined" || key === null) { 
    >            res.type("text/plain").status(500).send("ERROR: No Secure Store Key Input Parameter Specified");
    >            return; 
    >      } else {
    >              inputParams = { 
    >                     KEY: key 
    >              }; 
    >      }
    >      inputParams.STORE_NAME = "MY_SECURE_STORE"; 
    >      inputParams.FOR_XS_APPLICATIONUSER = true; 
    >      const client = await getSecureStore();
    >      //(client, Schema, Procedure, callback)
    >      hdbext.loadProcedure(req.db, "SYS", "USER_SECURESTORE_DELETE", (err, sp) => {) in the database or
    > 						by ensuring that the content of the request body is written to a JavaScript
    >           if (err) {
    >                res.type("text/plain").status(500).send(`ERROR: ${err.toString()}`);//Secure Store Delete
    > 						ensure that the content used to fill the 
    > app.delete("/:key?", async(req, res) =
    >                return;>
    >           } { 
    >           //(Input Parameters, callback(errors, Output Scalar Parameters, [Output Table Parameters
    >      const hdbext = require("@sap/hdbext"); ]
    >      const key = req.params.key; )
    >      let inputParams = ""; 
    >           sp(inputParams, (err, parameters, results) =
    >      if (typeof key === "undefined" || key === null) { >
    >            res.type("text/plain").status(500).send("ERROR: No Secure Store Key Input Parameter Specified"); {
    >            return; 
    >                if (err) {
    >                     res.type("text/plain").status(500).send(`ERROR: ${err.message.toString()}`);
    >                     return;
    >                }
    >      } else {
    >                res.type("application/json").status(200).send(`Entry in secure store successfully deleted for key: ${key} `);
    >              inputParams = { 
    >           });
    >                     KEY: key 
    >      });
    >              }; 
    >      }
    >      inputParams.STORE_NAME = "MY_SECURE_STORE"; 
    > });
    >      inputParams.FOR_XS_APPLICATIONUSER = true; 
    > ```

4.  Encode the content of the application's request body so that it is compatible with the data type used for `INSERT` and `RETRIEVE` operations that require a `VARBINARY` value for the entry's `KEY` parameter.

    > ### Note:  
    > This example applies to Node.js applications only.

    For operations where the `KEY` expects a `VALUE` with the data type `VARBINARY`, any hard-coded values \(numbers, dates, strings\) in the `INSERT` or `RETRIEVE` calls need to be converted, for example, using `TO_BINARY` or `TO_VARCHAR`. In the following example, no conversion is necessary; the `body-parser` module used to build the request body that fills the `VALUE` parameter is set to `raw`, which returns a JavaScript buffer that matches the `VARBINARY` requirement.

    > ### Sample Code:  
    > Process Request Body and Return a JavaScript Buffer
    > 
    > ```js
    > "use strict"; 
    > const express = require("express"); 
    > 
    > module.exports = () => { 
    >      const app = express.Router(); 
    > 
    >      const bodyParser = require("body-parser"); 
    >        app.use(bodyParser.raw({ 
    >                type: "text/plain" 
    >        })); 
    > ```

5.  Set up a secure connection to the SAP HANA Secure Store.

    To avoid authorization problems when the multitarget application tries to connect to the database, it is essential to ensure that the resource type for the database connection specified in the MTA's development descriptor \(`mta.yaml` file\) is `com.sap.xs.hana-securestore`.

    1.  Add a new secure-connection resource type to the multitarget application's development descriptor.

        To ensure a secure connection to the database, we use an instance of the `hana` service with the service plan `securestore`. For this, we need to define a corresponding resource in the application's development descriptor \(`MTA.yaml`\), and specify that it is required by the Node.js module using it, as illustrated in the following \(**incomplete**\) code snippet:

        > ### Sample Code:  
        > Resources in the Development Descriptor \(`MTA.yaml`\) of a Node.js Application
        > 
        > ```
        > ID: MySecureStoreApp
        > _schema-version: '2.0'
        > version: 1.0.0
        > modules:
        >   - name: srv 
        >     type: nodejs 
        >     path: srv 
        >     requires: 
        >       - name: MyDBConnection-secure
        >     provides: 
        >       - name: srv_api 
        >         properties: 
        >           url: '${default-url}'
        > resources:
        >   - name: myHANA-hdi-container
        >     properties: 
        >       hdi-container-name: '${service-name}' 
        >     type: com.sap.xs.hdi-container 
        >   - name: mySAP-ex-uaa 
        >     type: com.sap.xs.uaa-space 
        >     parameters: 
        >       path: ./xs-security.json
        >   - name: MyDBConnection-secure
        >     type: com.sap.xs.hana-securestore
        > ```

    2.  Initialize a connection to the Secure Store resource.

        The following Node.js code shows a function \(`getSecureStore()`\) that uses two SAP Node.js modules \(`@sap/xsenv` and `@sap/hdbext`\) to request information about the `securestore` service instance required for the connection and then use this information to help set up a secure connection to the database:

        > ### Sample Code:  
        > Connect the Multitarget Application's Database Module to the Secure-Store Resource \(Node.js\)
        > 
        > ```
        > /*eslint no-console: 0, no-unused-vars: 0, no-shadow: 0, new-cap: 0*/
        > /*eslint-env node, es6 */
        > "use strict";
        > const express = require("express");
        > 
        > module.exports = () => {
        > 	const app = express.Router();
        > 
        > 	const bodyParser = require("body-parser");
        > 	app.use(bodyParser.raw({
        > 		type: "text/plain"
        > 	})); //Process request Body and return a Buffer
        > 
        > 	function getSecureStore() {
        > 		return new Promise((resolve, reject) => {
        > 			const xsenv = require("@sap/xsenv");
        > 			let hanaOptions = xsenv.getServices({
        > 				secureStore: {
        > 					plan: "securestore"
        > 				}
        > 			});
        > 
        > 			var hdbext = require("@sap/hdbext");
        > 			hdbext.createConnection(hanaOptions.secureStore, (error, client) => {
        > 				if (error) {
        > 					reject(error);
        > 				} else {
        > 					resolve(client);
        > 				}
        > 			});
        > 		});
        > 	}
        >      //Secure Store Insert
        >      app.post("/:key?", async(req, res) => {[...]};
        >      //Secure Store Retrieve
        >      app.get("/:key?", async(req, res) => {[...]};
        >      //Secure Store Delete
        >      app.delete("/:key?", async(req, res) => {[...]};
        >      return app;
        > };
        > ```



**Related Information**  


[Maintain Values in the SAP HANA Secure Store](maintain-values-in-the-sap-hana-secure-store-8a82c9e.md "Insert entries into (and retrieve and remove entries from) the SAP HANA Secure Store.")

[SAP HANA Secure-Store Interface Procedures and Parameters](sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

