<!-- loio63b26ec63c644e22b5c401cddaa84650 -->

# Set up Logging

To add logging support, use the SAP Python library `sap_cf_logging`.



## Procedure

1.  Modify the `requirements.txt` file to include the logging module:

    > ### Source Code:  
    > requirements.txt
    > 
    > ```
    > Flask==0.12.2
    > cfenv==0.5.3
    > hdbcli
    > xssec==1.0.0
    > sap_cf_logging==3.0.0
    > 
    > ```

2.  Modify `server.py` file to use the logging library and log some messages when the application is accessed:

    > ### Source Code:  
    > server.py
    > 
    > ```
    > import os
    > import logging
    > from flask import Flask
    > from cfenv import AppEnv
    > from flask import request
    > from flask import abort
    > 
    > import xssec
    > from hdbcli import dbapi
    > from cf_logging import flask_logging
    > 
    > app = Flask(__name__)
    > env = AppEnv()
    > 
    > flask_logging.init(app, logging.INFO)
    > 
    > port = int(os.environ.get('PORT', 3000))
    > hana = env.get_service(label='hana')
    > uaa_service = env.get_service(name='myuaa').credentials
    > 
    > @app.route('/')
    > def hello():
    >     logger = logging.getLogger('route.logger')
    >     logger.info('Someone accessed us')
    > 
    >     if 'authorization' not in request.headers:
    >         abort(403)
    >     access_token = request.headers.get('authorization')[7:]
    >     security_context = xssec.create_security_context(access_token, uaa_service)
    >     isAuthorized = security_context.check_scope('openid')
    >     if not isAuthorized:
    >         abort(403)
    > 
    >     logger.info('Authorization successful')
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

3.  Modify the application's package dependencies to include the logging library in the download to the `vendor` folder.

    Follow the steps described in *Download and Consume Python Libraries* in the *Related Information* below.

4.  Push the application and access its URL.

    ```
    $ cf push
    $ cf app pyapp --urls
    ```

5.  Verify the message you logged is part of the application logs:

    Display the most recent messages logged in the `pyapp` application's logs:

    ```
    cf logs pyapp --recent
    ```


**Related Information**  


[Download and Consume Python Libraries](download-and-consume-python-libraries-842824f.md "A selection of SAP-specific and ready-to-use Python client libraries is available for download from the SAP Service Marketplace.")

