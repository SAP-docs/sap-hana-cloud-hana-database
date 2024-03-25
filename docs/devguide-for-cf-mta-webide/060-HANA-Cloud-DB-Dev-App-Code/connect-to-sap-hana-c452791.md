<!-- loioc4527913de3a493c8c608ef880f59f8d -->

# Connect to SAP HANA

Use the `hdbcli` module to connect to SAP HANA Cloud.



## Procedure

1.  Modify the `requirements.txt` file:

    > ### Source Code:  
    > `requirements.txt`
    > 
    > ```
    > Flask==3.0.0
    > cfenv==0.5.3
    > hdbcli==2.19.21
    > ```

2.  Use the module to connect to SAP HANA Cloud and execute a simple query.

    Modify `server.py`:

    > ### Source Code:  
    > `server.py`
    > 
    > ```
    > import os
    > from flask import Flask
    > from cfenv import AppEnv
    > from hdbcli import dbapi
    > 
    > 
    > app = Flask(__name__)
    > env = AppEnv()
    > 
    > port = int(os.environ.get('PORT', 3000))
    > hana = env.get_service(label='hana')
    > 
    > @app.route('/')
    > def hello():
    >     conn = dbapi.connect(address=hana.credentials['host'], port=int(hana.credentials['port']), user=hana.credentials['user'], password=hana.credentials['password'])
    > 
    >     cursor = conn.cursor()
    >     cursor.execute("select CURRENT_UTCTIMESTAMP from DUMMY", {})
    >     ro = cursor.fetchone()
    >     cursor.close()
    >     conn.close()
    > 
    >     return "Current time is: " + str(ro["CURRENT_UTCTIMESTAMP"])
    > 
    > 
    > if __name__ == '__main__':
    >     app.run(port=port)
    > 
    > ```

    > ### Note:  
    > For more information about the API, see *Related Information* below.

3.  Provide the application package dependencies.

    Create a folder called `vendor` in the root folder of the application. This is the target location for the dependent Python package that are downloaded with `pip download`. For more information about the `pip download` command and the `vendor` folder, see *Download and Consume Python Libraries* in the *Related Information* below.

4.  Push the Python application to the target application run-time environment and display its URL.

    ```
    cf push <pyapp>
    ```

    ```
    cf apps
    ```

    Locate the URL of the Python application and paste it into a Web browser; you should see the current SAP HANA Cloud time.

    ***Current time is: 14:38:25*** 


**Related Information**  


[Python Support](https://help.sap.com/viewer/0eec0d68141541d1b07893a39944924e/2.0.02/en-US/f3b8fabf34324302b123297cdbe710f0.html)

[Download and Consume Python Libraries](download-and-consume-python-libraries-842824f.md "Python client libraries developed by SAP on the Python Package Index (PyPI).")

