<!-- loio56956fec78134abdb3ef85dc0b5b7fcb -->

# Consume Platform Services



## Procedure

1.  Create an instance of the SAP HANA service with the following command:

    `cf create-service hana hdi-shared myhana`

2.  Bind the service instance to the application. Modify the `manifest.yml`:

    > ### Source Code:  
    > `manifest.yml`
    > 
    > ```
    > ---
    > applications:
    > - name: pyapp
    > 	host: pyapp
    > 	path: .
    > 	command: python server.py
    > 	
    > 	services: 
    > 		- myhana
    > ```

    > ### Caution:  
    > Cutting and pasting from this code block will probably cause white-space formatting issues in the `yaml` file. After pasting, remember to adjust the indenting to conform to valid yaml formatting.

3.  Add a module that will help read the service settings from the environment. Modify `requirements.txt`:

    > ### Source Code:  
    > `requirements.txt`
    > 
    > ```
    > Flask==3.0.0
    > cfenv==0.5.3
    > ```

4.  Consume the backing service `hana`.

    Modify the `server.py` file to `get` the service `hana`, as illustrated in the following example:

    > ### Source Code:  
    > `server.py`
    > 
    > ```
    > import os
    > from flask import Flask
    > from cfenv import AppEnv
    > 
    > app = Flask(__name__)
    > env = AppEnv()
    > 
    > port = int(os.environ.get('PORT', 3000))
    > hana = env.get_service(label='hana')
    > 
    > @app.route('/')
    > def hello():
    > 	return "Hello World"
    > if __name__ == '__main__':
    > app.run(port=port)
    > ```




<a name="loio56956fec78134abdb3ef85dc0b5b7fcb__result_xcx_j5g_qcb"/>

## Results

The SAP HANA service instance `myhana` is now bound to the application, and you can connect to it.

**Related Information**  


[Connect to SAP HANA](connect-to-sap-hana-c452791.md "Use the hdbcli module to connect to SAP HANA Cloud.")

