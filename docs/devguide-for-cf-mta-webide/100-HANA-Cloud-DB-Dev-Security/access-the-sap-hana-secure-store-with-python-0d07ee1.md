<!-- loio0d07ee1462c141beb8a86a92bc9cb92e -->

# Access the SAP HANA Secure Store with Python

Use an multitarget Python application to maintain entries in the SAP HANA Secure Store.



<a name="loio0d07ee1462c141beb8a86a92bc9cb92e__prereq_yrs_ybb_fcb"/>

## Prerequisites

To maintain content in the SAP HANA Secure Store, bear in mind the following conditions:

-   The application must be bound to an instance of the `hana` service using the `securestore` service plan.

-   The resource type for the database connection specified in the multitarget application's deployment descriptor \(`mta.yaml` file\) must be `com.sap.xs.hana-securestore`.

-   The Python driver for SAP HANA is required; it contains the `dbapi` module that must be imported to enable connections to the database. For more information, see *SAP HANA Client Interface Programming Reference* in *Related Information*.
-   This tutorial requires the following Python libraries:

    -   `hdbcli`, which is included in the SAP archive `XS PYTHON 1`

    -   `sap_cf_logging`, an open-source library that is developed by SAP and published on the Python Package Index \(Pypi\)


    For more information about downloading these libraries, see *Related Information*.




<a name="loio0d07ee1462c141beb8a86a92bc9cb92e__context_mqv_qbb_mgb"/>

## Context

In the context of the application run time, the SAP HANA Secure Store is used to maintain sensitive information such as user credentials. Access to the SAP HANA Secure Store is enabled by stored procedures which you can use to insert, retrieve, and delete entries in the Secure Store. Any application that is bound to an instance of the `hana` service with the service plan `securestore` has access to these stored procedures and can use them to maintain content stored in the Secure Store.

The following examples show how to use an multitarget Python application to maintain entries in the SAP HANA Secure Store:

> ### Tip:  
> The sources used for the code samples in this tutorial are also available on GitHub. For more information, see *Related Information* below.



## Procedure

1.  Request details of the service bound to the Python application that needs access to the SAP HANA Secure Store.

    You can read the port number from the relevant environment variable or choose port “9099” as the local default. In this example, we also use the module `cfenv` to import `AppEnv()`, which we use to list details of the Python application's environment and retrieve information about the configuration of the platform service `hana` bound to the Python application.

    > ### Sample Code:  
    > SAP HANA database connection credentials \(Python Application\)
    > 
    > ```py
    > from flask import Flask
    > from flask import request
    > from flask import Response
    > 
    > from flask import send_from_directory
    >  
    > import os
    > import json
    > from cfenv import AppEnv
    > 
    > from hdbcli import dbapi
    > 
    > 
    > app = Flask(__name__)
    > env = AppEnv()
    > 
    > port = int(os.getenv("PORT", 9099))
    > hana = env.get_service(label='hana')
    > [. . .]
    > ```

2.  Set up routes for requests coming through the application router.

    This module's `Flask` Web server is configured to respond to these three routes \(URL paths\): insert, retrieve, and delete.

    1.  If there is no path, then the Web server just returns "Hello World" and the module's instance number. Any requests passed through the application router will never hit this route.

        > ### Sample Code:  
        > ```py
        > @app.route('/')
        > def hello_world():
        >     output = '<strong>Python SecureStore! Instance ' + str(os.getenv("CF_INSTANCE_INDEX", 0)) + '</strong> Try these links.</br>\n'
        >     output += '<a href="/python/links">/python/links</a><br />\n'
        >     return output
        > [. . .]
        > ```

    2.  Ensure that the Web browser's request for `favicon.ico` is answered so that the browser does not return a “404” \(not found\) error.

        > ### Sample Code:  
        > ```py
        > @app.route('/favicon.ico') 
        > def favicon(): 
        >     return send_from_directory(os.path.join(app.root_path, 'static'),'favicon.ico', mimetype='image/vnd.microsoft.icon')
        > [. . .]
        > ```

    3.  Define requests passed through the application router.

        The following code snippet shows how to set up routes \(URL paths\) that are resolved when requests are made to the Python application to perform an operation in the SAP HANA Secure Store, for example: "insert", "retrieve", or "delete":

        > ### Sample Code:  
        > ```py
        > @app.route('/python/links')
        > def python_links():
        >     output = '<strong>Python SecureStore! Instance ' + str(os.getenv("CF_INSTANCE_INDEX", 0)) + '</strong> Try these links.</br>\n'
        >     output += '<a href="/python/insert">/python/insert</a><br />\n'
        >     output += '<a href="/python/retrieve">/python/retrieve</a><br />\n'
        >     output += '<a href="/python/delete">/python/delete</a><br />\n'
        >     return output
        > [. . .]
        > ```


3.  Define the credentials to use when establishing a secure connection to the database.

    In this step, we provide the credentials used for the database connection and use the credentials along with the Python driver to establish a connection to the SAP HANA database:

    > ### Note:  
    > The credentials defined here are valid for the database connection used for all of the Secure Store operations described in this tutorial: `INSERT`, `RETRIEVE`, and `DELETE`.

    1.  Provide the credentials to use for anonymous access in a database connection.

        This information is required for each of the connection operations: insert, retrieve, and delete. For encrypted connections, provision is also provided for a certificate. The following example shows how to ensure that a Python application uses the appropriate credentials to establish a secure connection to a specific SAP HANA database host:

        > ### Note:  
        > The `output` variable is used to collect expected values and return them to the browser for confirmation.

        > ### Sample Code:  
        > SAP HANA database connection credentials \(Python Application\)
        > 
        > ```py
        > @app.route('/python/insert')
        > def securestore_insert():
        >     output = 'Python SecureStore Insert. \n'
        > 
        >     schema = hana.credentials['schema']
        >     host = hana.credentials['host']
        >     port = hana.credentials['port']
        >     user = hana.credentials['user']
        >     password = hana.credentials['password']
        > 
        >     # Certificate for SAP HANA service instances that require an encrypted connection
        >     if 'certificate' in hana.credentials:
        >         haascert = hana.credentials['certificate']
        >     
        >     output += 'schema: ' + schema + '\n'
        >     output += 'host: ' + host + '\n'
        >     output += 'port: ' + port + '\n'
        >     output += 'user: ' + user + '\n'
        >     output += 'pass: ' + password + '\n'
        > [. . .]
        > ```

    2.  Configure the secure connection to the SAP HANA database.

        The following section of the code sample stores the information obtained in the previous step \(a.\) in local variables so that they can be easily returned in the output response body in the browser. If necessary the certificate provided in the header is also obtained for use where a secure connection is required.

        > ### Sample Code:  
        > Secure connection to the SAP HANA Database \(Python Application\)
        > 
        > ```py
        > @app.route('/python/insert')
        > def securestore_insert():
        > [...]
        >    if 'certificate' in hana.credentials:
        >       connection = dbapi.connect(
        >          address=host,
        >          port=int(port),
        >          user=user,
        >          password=password,
        >          currentSchema=schema,
        >          encrypt="true",
        >          sslValidateCertificate="true",
        >          sslCryptoProvider="openssl",
        >          sslTrustStore=haascert
        >       )
        >    else:
        >       connection = dbapi.connect(
        >          address=host,
        >          port=int(port),
        >          user=user,
        >          password=password,
        >          currentSchema=schema
        >       )
        > ```


4.  Insert encrypted values into the SAP HANA Secure Store.

    The following example shows how to use a Python application to insert encrypted entries into the SAP HANA Secure Store; the example uses `dbapi.connect` function shown in the previous sub-step to insert the entry defined in the parameters of the SQL call:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_INSERT \(Python Application\)
    > 
    > ```py
    > @app.route('/python/insert')
    > def securestore_insert():
    > #    # Provide connection details and certificates
    > [...]
    > #    # Prepare a cursor for SQL execution
    >     cursor = connection.cursor()
    > 
    > #    # Form an SQL statement to retrieve some data
    > 
    >     string2store = 'Whatever!'
    > 
    >     import codecs
    >     hex2store = (codecs.encode(str.encode(string2store), "hex")).decode()
    > 
    >     try:
    >         cursor.callproc("SYS.USER_SECURESTORE_INSERT", ("TestStoreName", False, "TestKey", hex2store))
    >         output += 'key TestKey with value ' + string2store + '=' + hex2store + ' was inserted into store TestStoreName.' + '\n'
    >     except:
    >         output += 'key TestKey likely already exists. Try deleting first.' + '\n'
    > 
    > #    # Close the DB connection
    >     connection.close()
    > 
    >     # Return the results
    >     return Response(output, mimetype='text/plain' , status=200,)
    > ```

    Bear in mind that, in the Python example above, the `TestKey` parameter requires a `VALUE` of type “`hex`”, so any hard-coded values \(numbers, dates, strings\) in the `INSERT` call need to be converted to the `hex` format. Here, several Python encoding functions are chained together and the resulting value stored in the `hex2store` variable.

5.  Retrieve encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Python application to retrieve encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_RETRIEVE \(Python Application\)
    > 
    > ```py
    > @app.route('/python/retrieve')
    > def securestore_retrieve():
    > #    # Provide connection details and certificates
    > [...]
    > #    # Prepare a cursor for SQL execution
    >     cursor = connection.cursor()
    > 
    > #    # Form an SQL statement to retrieve some data
    > 
    >     hexvalue = cursor.callproc("SYS.USER_SECURESTORE_RETRIEVE", ("TestStoreName", False, "TestKey", None))
    > 
    > #    # Close the DB connection
    >     connection.close()
    > 
    >     import codecs
    > 
    >     if hexvalue[3] is None:
    >         output += 'key TestKey does not exist in store TestStoreName.  Try inserting a value first.' + '\n'
    >     else:
    >         retrieved = codecs.decode(hexvalue[3].hex(), "hex").decode()
    >         output += 'key TestKey with value ' + retrieved + ' was retrieved from store TestStoreName.' + '\n'
    > 
    >     # Return the results
    >     return Response(output, mimetype='text/plain' , status=200,)
    > ```

    Bear in mind that, in the Python example above, the `TestKey` parameter returns a `VALUE` of type “`hex`”, so any hard-coded values \(numbers, dates, strings\) in the `RETRIEVE` results need to be converted with Python functions. In this case, the conversion results in the retrieved variable.

6.  Delete encrypted values from the SAP HANA Secure Store.

    The following example shows how to use a Python application to remove encrypted entries from the SAP HANA Secure Store:

    > ### Sample Code:  
    > Call SYS.USER\_SECURESTORE\_DELETE \(Python Application\)
    > 
    > ```py
    > @app.route('/python/delete')
    > def securestore_delete():
    > #    # Provide connection details and certificates
    > [...]
    > #    # Prepare a cursor for SQL execution
    >     cursor = connection.cursor()
    > 
    > #    # Form an SQL statement
    >     cursor.callproc("SYS.USER_SECURESTORE_DELETE", ("TestStoreName", False, "TestKey"))
    > 
    > #    # Close the DB connection
    >     connection.close()
    >     
    >     output += 'key TestKey was deleted from store TestStoreName.' + '\n'
    > 
    >     # Return the results
    >     return Response(output, mimetype='text/plain' , status=200,)
    > ```

7.  Set up a secure connection to the service instance that enables access to the SAP HANA Secure Store.

    To avoid authorization problems when the Python application tries to connect to the database, it is essential to ensure that the resource type for the database connection specified in the multitarget application's development descriptor \(`mta.yaml` file\) is `com.sap.xs.hana-securestore`.

    To ensure a secure connection to the database, we use an instance of the `hana` service with the service plan `securestore`. For this, we need to define a corresponding resource in the application's development descriptor \(`MTA.yaml`\), and specify that it is required by the Python module using it, as illustrated in the following \(**incomplete**\) code snippet:

    > ### Sample Code:  
    > Resources in the Development Descriptor \(`MTA.yaml`\) of a Python Application
    > 
    > ```
    > ID: MySecureStoreApp
    > _schema-version: '2.0'
    > version: 1.0.0
    > modules:
    >   - name: srv 
    >     type: python 
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


**Related Information**  


[Python Samples for SAP HANA Secure-Store on GitHub](https://github.com/SAP/hana-python-securestore)

[Maintain Values in the SAP HANA Secure Store](maintain-values-in-the-sap-hana-secure-store-8a82c9e.md "Insert entries into (and retrieve and remove entries from) the SAP HANA Secure Store.")

[SAP HANA Secure-Store Interface Procedures and Parameters](sap-hana-secure-store-interface-procedures-and-parameters-a847b4d.md "A list of the parameters available for interaction with the SAP HANA Secure Store using the dedicated stored procedures.")

[Download and Consume Python Libraries](../060-HANA-Cloud-DB-Dev-App-Code/download-and-consume-python-libraries-842824f.md "Python client libraries developed by SAP on the Python Package Index (PyPI).")

[Connect to SAP HANA from Python \(Client Programming Reference\)](https://help.sap.com/viewer/f1b440ded6144a54ada97ff95dac7adf/2.latest/en-US/d12c86af7cb442d1b9f8520e2aba7758.html)

