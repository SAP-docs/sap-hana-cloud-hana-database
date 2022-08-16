<!-- loioc0ec0d09a80e4cd39618e4e449d32a51 -->

# Set up Authorization

To control access to the content you serve, use the Python `xssec` security library.



## Procedure

1.  Modify the `requirements.txt` file to include the `xssec` library:

    > ### Source Code:  
    > `requirements.txt`
    > 
    > ```
    > Flask==0.12.2
    > cfenv==0.5.3
    > hdbcli
    > xssec==1.0.0
    > ```

2.  Modify the `manifest.yml` file and bind the same UAA service:

    > ### Source Code:  
    > `manifest.yml`
    > 
    > ```
    > ---
    > applications:
    > - name: pyapp
    >   host: pyapp
    >   path: .
    >   command: python server.py
    >   services:
    >     - myhana
    >     - myuaa
    > 
    > 
    > ```

    > ### Caution:  
    > Cutting and pasting from this code sample will probably cause white-space formatting issues in the resulting `yaml` file. After pasting, remember to adjust the indenting to conform to valid `yaml` formatting.

3.  Modify the `server.py` file to use the security library:

    > ### Source Code:  
    > server.py
    > 
    > ```
    > import os
    > from flask import Flask
    > from cfenv import AppEnv
    > from flask import request
    > from flask import abort
    > 
    > import xssec
    > 
    > from hdbcli import dbapi
    > 
    > app = Flask(__name__)
    > env = AppEnv()
    > 
    > port = int(os.environ.get('PORT', 3000))
    > hana = env.get_service(label='hana')
    > uaa_service = env.get_service(name='myuaa').credentials
    > 
    > @app.route('/')
    > def hello():
    >     if 'authorization' not in request.headers:
    >         abort(403)
    >     access_token = request.headers.get('authorization')[7:]
    >     security_context = xssec.create_security_context(access_token, uaa_service)
    >     isAuthorized = security_context.check_scope('openid')
    >     if not isAuthorized:
    >         abort(403)
    > 
    > 
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
    > if __name__ == '__main__':
    >     app.run(port=port)
    > 
    > ```

4.  Modify the application's package dependencies to include the security library in the download to the `vendor` folder.

    Follow the steps described in *Download and Consume Python Libraries* in the *Related Information* below.

5.  Try to access the Python application directly, for example, using the application URL displayed by the `cf app pyapp --urls` command; you should see an HTTP 403 error.

    If you however access the Python application through the application router, you should see the current SAP HANA Cloud time, provided you have the security scope `openid` assigned to user who is calling the URL and logging on.


**Related Information**  


[Download and Consume Python Libraries](download-and-consume-python-libraries-842824f.md "A selection of SAP-specific and ready-to-use Python client libraries is available for download from the SAP Service Marketplace.")

