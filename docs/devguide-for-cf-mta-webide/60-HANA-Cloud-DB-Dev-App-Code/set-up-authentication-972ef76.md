<!-- loio972ef76f777647fca39570a82e1d28cb -->

# Set up Authentication

To set up authentication, you use the application router and the XS User Account and Authentication \(UAA\) service.



## Procedure

1.  Create a service instance of the XS UAA service, with the following command:

    `cf create-service xsuaa default myuaa`

2.  Create a new directory for the application router.

    Inside the new application-router directory, create the following files:

    -   `manifest.yml`

        The application's manifest file.

    -   `package.json`

        The list of packages that `pyapp` requires.

    -   `xs-app.json`

        The application descriptor which is used to configure the application router.


    1.  Create and configure the application manifest file `manifest.yml`:

        In this example, you bind the UAA service to the application router and create a destination for the Python application specifying you want an authentication token to be sent.

        > ### Source Code:  
        > `manifest.yml`
        > 
        > ```
        > ---
        > applications:
        > - name: web
        >   path: .
        >   env:
        >     destinations: >
        >       [
        >         {
        >           "name":"pyapp",
        >           "url":"https://host:port_of_python_app",
        >           "forwardAuthToken": true
        >         }
        >       ]
        >   services:
        >     - myuaa
        > 
        > ```

        > ### Caution:  
        > Cutting and pasting from this code sample will probably cause white-space formatting issues in the `yaml` file. After pasting, remember to adjust the indenting to conform to valid `yaml` formatting.

    2.  Create and configure the package-dependencies file `package.json`.

        > ### Source Code:  
        > `package.json`
        > 
        > ```json
        > {
        >   "name": "myapp-entry-point",
        >   "scripts": {
        >     "start": "node node_modules/@sap/approuter/approuter.js"
        >   },
        >   "dependencies": {
        >     "@sap/approuter": "^3.0.1"
        >   }
        > }
        > 
        > ```

        > ### Note:  
        > You list the application router as a dependency and use it for the authentication.

    3.  Create and configure the application descriptor `xs-app.json` for the Python application `pyapp`:

        > ### Source Code:  
        > `xs-app.json`
        > 
        > ```json
        > {
        >   "routes": [
        >     {
        >       "source": "^/pyapp/(.*)$",
        >       "target": "$1",
        >       "destination": "pyapp"
        >     }
        >   ]
        > }
        > 
        > ```

        In this example, you redirect all traffic to `/pyapp/` to the Python application `pyapp`. For more information about routes and destinations, see *Maintaining Application Routes and Destinations* in the *Related Information* below.


3.  Push the Python application `pyapp` to the Cloud Foundry run-time environment.

    `cf push pyapp`

4.  Check the URL of the application router:

    After deployment is complete, use the command `cf apps` to display a list of all deployed applications and the corresponding URL at which each application is reachable. Locate the URL of the application router for the `pyapp` application and note the assigned URL.

5.  In a Web browser, navigate to the URL of the application router: *<URL\_of\_approuter\>*/pyapp/.

    You should be prompted to log in, and then you should see the current SAP HANA Cloud time displayed by the Python application.

6.  Enter the credentials of a valid user. If no custom identity provider \(IDP\) is configured, you should use the credential of a known SAP HANA Cloud user.

    You should see a message similar to the following in the browser:

    -   *Application user: *<login user\>**

        The name of the user who logs on to the application.

    -   *HANA user: *<db user\>**

        The technical user used to connect to SAP HANA Cloud.


    > ### Note:  
    > An application user is not the same as a database user.
    > 
    > Since the application `pyapp` and the application `web` are both bound to the same UAA service instance, authentication is handled by the `web` application.


**Related Information**  


[Maintaining Multitarget Application Routes and Destinations](../90-HANA-Cloud-DB-Dev-MTA-Routes/maintaining-multitarget-application-routes-and-destinations-0117b71.md "Define application routes and destinations.")

