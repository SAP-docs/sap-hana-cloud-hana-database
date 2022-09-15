<!-- loio6ba89596e3a64a5480c3977d4ea7fdba -->

# Configure the Multitarget Application Router

The application routes to the available microservices are described in the `xs-app.json` file.



## Prerequisites

-   File name
    -   `xs-app.json`

        Configures the application router and describes the routes.

        > ### Note:  
        > Without the application router configuration, no access to the dependent application is possible.

    -   `package.json`

        Contains the start command for the application router and a list of package dependencies.


-   Location

    Application's Web resources folder, for example, `/path/appname/web`

-   Format

    JavaScript Object Notation \(JSON\)




## Context

The application router is used to serve static content, authenticate users, rewrite URLs, and forward or proxy requests to other micro services while propagating user information. The application-router configuration file `xs-app.json` configures the application router and describes the routes. To configure the application router, perform the following steps:



<a name="loio6ba89596e3a64a5480c3977d4ea7fdba__steps_xly_smq_xs"/>

## Procedure

1.  Create the application resource-file structure.

    For example, `/path/appname/`

2.  Create a sub-folder for the static Web-resources module.

    The sub-folder for the Web-resources module must be located in the application root folder, for example, <code>/path/<i class="varname">&lt;myAppName&gt;</i>/web</code>

    > ### Tip:  
    > The Web-resource module uses `@sap/approuter` as a dependency; the Web-resources module also contains the configuration and static resources for the application. All the standard SAP NPM packages can be found in the public NPM registry at `registry.npmjs.org`. For more information, see *Related Information below.* 

3.  Create sub-folder for the application's static resources.

    Static resources can include the following file and components: `index.html`, style sheets \(`.css` files\), images and icons, etc.\). Typically, static resouces for a Web application are placed in a subfolder of the Web module, for example, <code>/path/<i class="varname">&lt;myAppName&gt;</i>/web/resources</code>.

4.  Create the application-router configuration file.

    The application router configuration file `xs-app.json` must be located in the application's Web-resources folder, for example, <code>/path/<i class="varname">&lt;appname&gt;</i>/web</code>.

    > ### Sample Code:  
    > ```
    > <myAppName>
    > |- web/                         # Application descriptors
    > |  |- xs-app.json               # Application routes configuration
    > |  |- package.json              # Application router details/dependencies
    > |  \- resources/ 
    > 
    > ```

5.  Define details of the application's routes, destinations, and security scopes.

    The contents of the `xs-app.json` file must use the required JSON syntax. For more information, see *Application Router Configuration Syntax* in *Related Information* below.

    1.  Create the required “destinations configuration”.

        > ### Sample Code:  
        > <code><i class="varname">&lt;myAppName&gt;</i>/web/xs-app.json</code>
        > 
        > ```
        > { 
        >   "welcomeFile": "index.html", 
        >   "routes": [ 
        >     { 
        >       "source": "/sap/ui5/1(.*)", 
        >       "target": "$1", 
        >       "localDir": "sapui5" 
        >     }, 
        >     { 
        >       "source": "/rest/addressbook/testdataDestructor", 
        >       "destination": "backend", 
        >       "scope": "node-hello-world.Delete" 
        >     }, 
        >     { 
        >       "source": "/rest/.*", 
        >       "destination": "backend" 
        >     }, 
        >     { 
        >       "source": "^/(.*)", 
        >       "localDir": "resources" 
        >     } 
        >   ] 
        > } 
        > ```

    2.  Add the routes \(destinations\) for the specific application \(for example, `node-hello-world`\) to the `env` section of the application’s deployment manifest \(`manifest.yml`\).

        Every route configuration that forwards requests to a micro service has property destination. The destination is a name that refers to the same name in the destinations configuration. The destinations configuration is specified in an environment variable passed to the approuter application.

        > ### Sample Code:  
        > <code><i class="varname">&lt;myAppName&gt;</i>/manifest.yml</code>
        > 
        > ```
        > - name: node-hello-world
        >   host: myHost-node-hello-world 
        >   domain: xsapps.acme.ondemand.com 
        >   memory: 100M 
        >   path: web 
        >   env: 
        >     destinations: > 
        >      [ 
        >        { 
        >          "name":"backend", 
        >          "url":"https://myHost-node-hello-world-backend.ondemand.acme.com", 
        >          "forwardAuthToken": true 
        >        } 
        >      ] 
        > ```


6.  Add a package descriptor for the multitarget application router.

    The package descriptor \(`package.json`\) describes the prerequisites and dependencies for the application and starts the application router, too. Add a `package.json` file to the root folder of your application's Web resources module \(`web/`\).

    > ### Sample Code:  
    > ```
    > <myAppName>
    > |- web/                         # Application descriptors
    > |  |- xs-app.json               # Application routes configuration
    > |  |- package.json              # Application router details/dependencies
    > |  \- resources/ 
    > 
    > ```

    The basic `package.json` file for your Web-resources module \(`web/`\) should look similar to the following example:

    > ### Sample Code:  
    > ```
    > {
    >   "name": "node-hello-world-approuter",  
    >   "dependencies": {
    >      "@sap/approuter": "^2.7.1"
    >   },
    >   "scripts": {
    >      "start": "node node_modules/@sap/approuter/approuter.js"
    >   } 
    > } 
    > ```

    > ### Tip:  
    > The start script \(for example, `approuter.js`\) is mandatory; the start script is executed after application deployment.


**Related Information**  


[Application Routes and Destinations](application-routes-and-destinations-875809c.md "The application router is the single point of entry for an application.")

[Application-Router Resource Files](application-router-resource-files-8dccaad.md "The routing configuration for an application is defined in one or more so-called &quot;destinations&quot; that are defined in a destinations configuration.")

[The Application Descriptor](the-application-descriptor-96c7545.md "Understand the contents of the file used to configure the multitarget application router.")

[Application Router Configuration Syntax](application-router-configuration-syntax-5f77e58.md "The application description defined in the xs-app.json file contains the configuration information used by the application router.")

[The NPM Registry](../060-HANA-Cloud-DB-Dev-App-Code/the-npm-registry-726e5d4.md "The public NPM registry includes SAP Node.js modules for use by application developers.")

